# singularity-docker-centos7-draw.io
draw.io singularity container on CentOS-7

```
Running without installation:
```
singularity run shub://truatpasteurdotfr/singularity-docker-centos7-draw.io
```
Building:
```
sudo singularity build draw.io.simg Singularity
```
Download and rename:
```
singularity pull --name "draw.io.simg" shub://truatpasteurdotfr/singularity-docker-centos7-draw.io
```
Running with a separate $HOME and access to /run
```
mkdir -p  ~/singularity.d/home/draw.io
singularity run -B /run -H  ~/singularity.d/home/draw.io ./draw.io.simg
```

Caveat:
- you need to rebuild the container for each update of chrome/base os if you are using the squashfs image format.
- possible workaround: convert the squash file system to a directory with the `--sandbox`
```
mkdir -p ~/singularity.d/sandbox/draw.io
sudo singularity build --sandbox ~/singularity.d/sandbox/draw.io ./draw.io.simg
sudo singularity exec --writable ~/singularity.d/sandbox/draw.io 'yum -y update'
```

