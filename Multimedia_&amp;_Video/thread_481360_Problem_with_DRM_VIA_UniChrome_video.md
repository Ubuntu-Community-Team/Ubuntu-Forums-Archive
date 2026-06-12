---
title: "Problem with DRM: VIA UniChrome video"
date: 2007-06-22
forum: Multimedia &amp; Video
---

### Post by pac-man on 2007-06-22
Hi, before anything I will start off saying the hardware I got: AMD Sempron 2200, 256 mb ram, 8mb shared integrated VIA Unichrome km400 video and xubuntu 7.04

Well, I was installing the openchrome drivers for my via unichrome km400, I followed the guidelines described in the following site: [https://help.ubuntu.com/community/OpenChrome](https://help.ubuntu.com/community/OpenChrome)

At first I decided to only install the 2D stuff, everything was fine without any problem, but when I tried to install the 3D using this command
[I]
make LINUXDIR=/lib/modules/`uname -r`/build DRM_MODULES=via[/I]

... I had the following error messages:
[I]
make -C /lib/modules/2.6.20-16-386/build  SUBDIRS=`pwd` DRMSRCDIR=`pwd` modules

make: *** /lib/modules/2.6.20-16-386/build: No such file or directory.  Stop.

make: *** [modules] Error 2[/I]

If I go to /lib/modules/2.6.20-16-386/ and type "ls -a" I can't find anything named "build", so I guess that's why I get this problem.

I have to say that before this attempt to install those drivers, I could see the gears moving with the command "glxgears" and the glxinfo returned me a message saying that the 3d acceleration was ok. In other words, everything was ok, but I tried to fix something that was not unfixed by doing all this :(

So anyone knows how can I resolve this? 

Thanks in advance

---

