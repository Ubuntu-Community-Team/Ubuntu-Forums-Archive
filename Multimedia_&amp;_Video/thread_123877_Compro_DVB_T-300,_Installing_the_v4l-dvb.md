---
title: "Compro DVB T-300, Installing the v4l-dvb"
date: 2006-01-31
forum: Multimedia &amp; Video
---

### Post by stevenyu on 2006-01-31
Hi guys, I am trying to install the v4l-dvb package for my compro DVB T-300 Digital TV Tuner, I have download the latest source file, however I can't get it to compile correctly.

> root@stevenyu:/home/stevenyu/v4l-dvb# make
make -C /home/stevenyu/v4l-dvb/v4l
make[1]: Entering directory `/home/stevenyu/v4l-dvb/v4l'
creating symbolic links...
make -C /lib/modules/2.6.12-9-386/build SUBDIRS=/home/stevenyu/v4l-dvb/v4l  modules
/usr/src/linux-headers-2.6.12-9-386/scripts/gcc-version.sh: line 11: gcc-3.4: command not found
/usr/src/linux-headers-2.6.12-9-386/scripts/gcc-version.sh: line 12: gcc-3.4: command not found
make[2]: gcc-3.4: Command not found
make[2]: Entering directory `/usr/src/linux-headers-2.6.12-9-386'
  CC [M]  /home/stevenyu/v4l-dvb/v4l/video-buf.o
/bin/sh: gcc-3.4: command not found
make[3]: *** [/home/stevenyu/v4l-dvb/v4l/video-buf.o] Error 127
make[2]: *** [_module_/home/stevenyu/v4l-dvb/v4l] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.12-9-386'
make[1]: *** [default] Error 2
make[1]: Leaving directory `/home/stevenyu/v4l-dvb/v4l'
make: *** [all] Error 2

I have the kernel header installed, but I not sure whether the problem is cause by having GCC Version 4 instead of 3.4????

Can anyone help?  Thanks!!!

---

