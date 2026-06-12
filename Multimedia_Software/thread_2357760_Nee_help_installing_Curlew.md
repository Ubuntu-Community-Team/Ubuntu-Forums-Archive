---
title: "Nee help installing Curlew"
date: 2017-04-05
forum: Multimedia Software
---

### Post by jacatone on 2017-04-05
I would like to install Curlew video converter. Wasn't in repositories so downloaded the .deb file. Keeps telling me I need python 3.5. Can't seem to find that either. Anyone know the answer?

---

### Post by howefield on 2017-04-05
What operating system are you using and how are you trying to install ?

Seems to run fine here albeit in 17.04

```
sudo apt install -s ~/Downloads/curlew_0.2.2-1_all.deb 
[sudo] password for hugh: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'curlew' instead of '/home/hugh/Downloads/curlew_0.2.2-1_all.deb'
The following additional packages will be installed:
  ffmpeg gnome-icon-theme gnome-icon-theme-symbolic libavdevice57 libavfilter6 libavresample3 libbs2b0 libebur128-1 libflite1
  libmediainfo0v5 libmms0 libopenal-data libopenal1 libopencv-core2.4v5 libopencv-imgproc2.4v5 libpostproc54 librubberband2v5
  libsdl2-2.0-0 libtbb2 libtinyxml2-4 libzen0v5 mediainfo
Suggested packages:
  ffmpeg-doc mediainfo-gui
The following NEW packages will be installed
  curlew ffmpeg gnome-icon-theme gnome-icon-theme-symbolic libavdevice57 libavfilter6 libavresample3 libbs2b0 libebur128-1 libflite1
  libmediainfo0v5 libmms0 libopenal-data libopenal1 libopencv-core2.4v5 libopencv-imgproc2.4v5 libpostproc54 librubberband2v5
  libsdl2-2.0-0 libtbb2 libtinyxml2-4 libzen0v5 mediainfo
0 to upgrade, 23 to newly install, 0 to remove and 0 not to upgrade.
Inst gnome-icon-theme (3.12.0-2 Ubuntu:17.04/zesty [all])
Inst gnome-icon-theme-symbolic (3.12.0-2 Ubuntu:17.04/zesty [all])
Inst libavresample3 (7:3.2.4-1build2 Ubuntu:17.04/zesty [amd64])
Inst libbs2b0 (3.1.0+dfsg-2.2 Ubuntu:17.04/zesty [amd64])
Inst libebur128-1 (1.2.0-2 Ubuntu:17.04/zesty [amd64])
Inst libflite1 (2.0.0-release-3 Ubuntu:17.04/zesty [amd64])
Inst libtbb2 (4.4~20160526-0ubuntu1 Ubuntu:17.04/zesty [amd64])
Inst libopencv-core2.4v5 (2.4.9.1+dfsg-2.2 Ubuntu:17.04/zesty [amd64])
Inst libopencv-imgproc2.4v5 (2.4.9.1+dfsg-2.2 Ubuntu:17.04/zesty [amd64])
Inst libpostproc54 (7:3.2.4-1build2 Ubuntu:17.04/zesty [amd64])
Inst librubberband2v5 (1.8.1-6ubuntu2 Ubuntu:17.04/zesty [amd64])
Inst libavfilter6 (7:3.2.4-1build2 Ubuntu:17.04/zesty [amd64])
Inst libopenal-data (1:1.17.2-4 Ubuntu:17.04/zesty [all])
Inst libopenal1 (1:1.17.2-4 Ubuntu:17.04/zesty [amd64])
Inst libsdl2-2.0-0 (2.0.5+dfsg1-2ubuntu3 Ubuntu:17.04/zesty [amd64])
Inst libavdevice57 (7:3.2.4-1build2 Ubuntu:17.04/zesty [amd64])
Inst ffmpeg (7:3.2.4-1build2 Ubuntu:17.04/zesty [amd64])
Inst libmms0 (0.6.4-2 Ubuntu:17.04/zesty [amd64])
Inst libtinyxml2-4 (4.0.1-1 Ubuntu:17.04/zesty [amd64])
Inst libzen0v5 (0.4.34-1 Ubuntu:17.04/zesty [amd64])
Inst libmediainfo0v5 (0.7.91-1 Ubuntu:17.04/zesty [amd64])
Inst mediainfo (0.7.91-1 Ubuntu:17.04/zesty [amd64])
Inst curlew (0.2.2-1 local-deb [all])
Conf gnome-icon-theme (3.12.0-2 Ubuntu:17.04/zesty [all])
Conf gnome-icon-theme-symbolic (3.12.0-2 Ubuntu:17.04/zesty [all])
Conf libavresample3 (7:3.2.4-1build2 Ubuntu:17.04/zesty [amd64])
Conf libbs2b0 (3.1.0+dfsg-2.2 Ubuntu:17.04/zesty [amd64])
Conf libebur128-1 (1.2.0-2 Ubuntu:17.04/zesty [amd64])
Conf libflite1 (2.0.0-release-3 Ubuntu:17.04/zesty [amd64])
Conf libtbb2 (4.4~20160526-0ubuntu1 Ubuntu:17.04/zesty [amd64])
Conf libopencv-core2.4v5 (2.4.9.1+dfsg-2.2 Ubuntu:17.04/zesty [amd64])
Conf libopencv-imgproc2.4v5 (2.4.9.1+dfsg-2.2 Ubuntu:17.04/zesty [amd64])
Conf libpostproc54 (7:3.2.4-1build2 Ubuntu:17.04/zesty [amd64])
Conf librubberband2v5 (1.8.1-6ubuntu2 Ubuntu:17.04/zesty [amd64])
Conf libavfilter6 (7:3.2.4-1build2 Ubuntu:17.04/zesty [amd64])
Conf libopenal-data (1:1.17.2-4 Ubuntu:17.04/zesty [all])
Conf libopenal1 (1:1.17.2-4 Ubuntu:17.04/zesty [amd64])
Conf libsdl2-2.0-0 (2.0.5+dfsg1-2ubuntu3 Ubuntu:17.04/zesty [amd64])
Conf libavdevice57 (7:3.2.4-1build2 Ubuntu:17.04/zesty [amd64])
Conf ffmpeg (7:3.2.4-1build2 Ubuntu:17.04/zesty [amd64])
Conf libmms0 (0.6.4-2 Ubuntu:17.04/zesty [amd64])
Conf libtinyxml2-4 (4.0.1-1 Ubuntu:17.04/zesty [amd64])
Conf libzen0v5 (0.4.34-1 Ubuntu:17.04/zesty [amd64])
Conf libmediainfo0v5 (0.7.91-1 Ubuntu:17.04/zesty [amd64])
Conf mediainfo (0.7.91-1 Ubuntu:17.04/zesty [amd64])
Conf curlew (0.2.2-1 local-deb [all])
```

---

### Post by RobGoss on 2017-04-05
This is version **Curlew 2.1.2** a more updated version

You can install it running the following commands:

```
sudo add-apt-repository ppa:noobslab/apps
```

```
 sudo apt-get update
```

```
sudo apt-get install curlew
```


If you want more information on it you can visit this article [http://linuxg.net/install-curlew-on-ubuntu/](http://linuxg.net/install-curlew-on-ubuntu/)

---

### Post by howefield on 2017-04-05
> **RobGoss said:**
> Try running the following commands:

Are you sure that would be a good idea ?

The current version (0.2.2) is about a year old, the version you want the OP to install 0.1.12 is going on 5 years old.

---

### Post by RobGoss on 2017-04-05
Good catch Howefield, removed that PPA did not realize that. I was under the impression it was a early version

---

