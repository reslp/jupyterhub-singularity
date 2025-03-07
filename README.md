# jupyterhub-singularity

## Set up a Jupyterhub instance with singularity

This allows to create a Jupyter hub server which also has custom authetication and is running in singularity.

It generally makes sense to run this in screen or tmux.

1. Reserve a node:

```
srun -c 32 --mem 128G --tmp 100G --pty bash 
```

Once this is running:

2. Clone this repository:

```
git clone https://github.com/reslp/jupyterhub-singularity.git
```

3. Get IP address of node:

```
ip addr
```

4. Run Jupyter Hub:

```
singularity exec -B $(pwd) -B $(pwd)/homes:/data/homes docker://reslp/jupyter-hub:5.2.1 jupyterhub
```

This commands need to be run inside the folder with the homes directory and the `jupyterhub_config.py` file.

It is now possible to access the server through the IP address and port 8000 from above in a browser.

The dockerfile for this jupyterhub server can be found here: https://github.com/reslp/dockerfiles

