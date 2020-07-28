# docker-snapcraft-builder
Simple docker image to build snaps.

Based on: https://snapcraft.io/docs/build-on-docker

# Usage.

## Get the image and create a container.

Get the image from docker hub:

```bash
docker pull williamjmorenor/snapcraft-builder
```

From the project directory run the image:

```bash
docker run --name snap-packaging -v $PWD:/home/packager:rw -ti williamjmorenor/snapcraft-builder
```

The snapcraft command is available:

```bash
 packager@ed8fa654731b:~$ snapcraft --help
[...]
packager@ed8fa654731b:~$ whoami
packager
packager@ed8fa654731b:~$ pwd
/home/packager
```
Note the image not run as root.

To finish the sesion in the container just type:

```bash
  exit
```

## Reuse the docker container.

To resue the same docker container run:

```bash
  docker start snap-packaging -i
```

## Update to the last image.

Remove old image and container:

```bash
  docker rm snap-packaging
  docker image rm williamjmorenor/snapcraft-builder
```

Pull last image and recreate container:

```bash
  docker pull williamjmorenor/snapcraft-builder
  docker run --name snap-packaging -v $PWD:/home/packager:rw -ti williamjmorenor/snapcraft-builder
```
