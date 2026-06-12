---
title: "webcam studio"
date: 2012-09-10
forum: Multimedia Software
---

### Post by neuman1812 on 2012-09-10
Has anyone been able to install Webcam Studio   on Ubuntu 12.04 64bit?

```
~$ sudo apt-get install webcamstudio
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  webcamstudio
0 upgraded, 1 newly installed, 0 to remove and 106 not upgraded.
Need to get 0 B/11.3 MB of archives.
After this operation, 12.4 MB of additional disk space will be used.
Selecting previously unselected package webcamstudio.
(Reading database ... 207146 files and directories currently installed.)
Unpacking webcamstudio (from .../webcamstudio_0.56-1~getdeb2_all.deb) ...
Processing triggers for desktop-file-utils ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Processing triggers for ureadahead ...
Setting up webcamstudio (0.56-1~getdeb2) ...
update-rc.d: warning: webcamstudio stop runlevel arguments (0 1 6) do not match LSB Default-Stop values (none)
Removing the webcamstudio module from memory
ERROR: Module webcamstudio does not exist in /proc/modules
Removing webcamstudio.ko from the modules
Restating the webcamstudio service to update the module
 * Stopping WebcamStudio kernel module webcamstudio                                                         [ OK ] 
 * Starting WebcamStudio kernel module webcamstudio                                                                make -C /lib/modules/3.2.0-23-generic/build SUBDIRS=/tmp/webcamstudio-src modules
make[1]: Entering directory `/usr/src/linux-headers-3.2.0-23-generic'
  CC [M]  /tmp/webcamstudio-src/webcamstudio.o
/tmp/webcamstudio-src/webcamstudio.c:191:2: error: #error "need CONFIG_VIDEO_V4L1_COMPAT"
/tmp/webcamstudio-src/webcamstudio.c:215:28: fatal error: linux/videodev.h: No such file or directory
compilation terminated.
make[2]: *** [/tmp/webcamstudio-src/webcamstudio.o] Error 1
make[1]: *** [_module_/tmp/webcamstudio-src] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.2.0-23-generic'
make: *** [all] Error 2
install -d /lib/modules/3.2.0-23-generic/kernel/drivers/misc
install -m 644 -c webcamstudio.ko /lib/modules/3.2.0-23-generic/kernel/drivers/misc
install: cannot stat `webcamstudio.ko': No such file or directory
make: *** [install] Error 1

 * Modprobe webcamstudio failed. Please use 'dmesg' to find out why.

```

Dmesg output can be found here [http://pastebin.com/0gWKKx2u](http://pastebin.com/0gWKKx2u)

---

### Post by samalex on 2012-11-05
Hi...

Did you ever get Webcam Studio working on Ubuntu 12.04? I'm running Xubuntu 12.04 but I'm getting the same error as you.  I followed some of the instructions on [http://code.google.com/p/webcamstudio/issues/detail?id=75](http://code.google.com/p/webcamstudio/issues/detail?id=75) which I noticed you posted to as well, but installing the patch did no good to me.  Also your post there mentioned a webcamstudio.rej file, but where is this at?  

Thanks for any insight...

---

### Post by dannyboy79 on 2012-12-01
have you tried compiling from svn as it shows here?
[http://www.ws4gl.org/download/compiling](http://www.ws4gl.org/download/compiling)

---

