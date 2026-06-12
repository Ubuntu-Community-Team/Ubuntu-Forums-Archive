---
title: "need help for network issue where i get this error while downloading any file"
date: 2011-04-28
forum: Networking &amp; Wireless
---

### Post by bruce2wayne on 2011-04-28
hi, guys i'm shan and kinda new to ubuntu and recently i installed the wireless drivers for my system after that i seem to get a lot of this error messages if i install any thing and you can see the error message i got after i installed filezilla in my system.

```
shan@shan:~$ sudo apt-get install filezilla
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  x11proto-xext-dev x11proto-fonts-dev xserver-xorg-dev patchutils
  x11proto-render-dev x11proto-video-dev libpciaccess-dev sdparm
  x11proto-dri2-dev x11proto-randr-dev libpixman-1-dev dh-make dpatch
  libxkbfile-dev
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  filezilla-common
The following NEW packages will be installed:
  filezilla filezilla-common
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 4,023kB of archives.
After this operation, 12.5MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://in.archive.ubuntu.com/ubuntu/ lucid-updates/universe filezilla-common 3.3.1-1ubuntu2 [2,739kB]
Get:2 http://in.archive.ubuntu.com/ubuntu/ lucid-updates/universe filezilla 3.3.1-1ubuntu2 [1,285kB]
Fetched 4,023kB in 1min 2s (64.6kB/s)                                          
Selecting previously deselected package filezilla-common.
(Reading database ... 165064 files and directories currently installed.)
Unpacking filezilla-common (from .../filezilla-common_3.3.1-1ubuntu2_all.deb) ...
Selecting previously deselected package filezilla.
Unpacking filezilla (from .../filezilla_3.3.1-1ubuntu2_i386.deb) ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for man-db ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_IN.cache...
Processing triggers for desktop-file-utils ...
Processing triggers for python-support ...
Setting up oss4-dkms (4.2-build2002-2) ...

Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area....
cp /lib/modules/2.6.32-32-generic/source/include/linux/limits.h /var/lib/dkms/oss4/4.2-build2002/build/core && make -C /lib/modules/2.6.32-32-generic/build SUBDIRS=/var/lib/dkms/oss4/4.2-build2002/build/core modules && make -C /var/lib/dkms/oss4/4.2-build2002/build/drivers osscore_symbols.inc && make -C /lib/modules/2.6.32-32-generic/build SUBDIRS=/var/lib/dkms/oss4/4.2-build2002/build/drivers modules....(bad exit status: 1)

Error! Bad return status for module build on kernel: 2.6.32-32-generic (i686)
Consult the make.log in the build directory
/var/lib/dkms/oss4/4.2-build2002/build/ for more information.
0
0
dpkg: error processing oss4-dkms (--configure):
 subprocess installed post-installation script returned error exit status 10
Setting up filezilla-common (3.3.1-1ubuntu2) ...
Setting up filezilla (3.3.1-1ubuntu2) ...

Errors were encountered while processing:
 oss4-dkms
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by bruce2wayne on 2011-04-28
and while i open the make.log it has the following info i'm totally clueless on how to resolve this issue as i plan to create a live cd out of the existing congiuration of my os using remastersys if this problem is solved i will do it. And the log info is as follows :

```
DKMS make.log for oss4-4.2-build2002 for kernel 2.6.32-32-generic (i686)
Thu Apr 28 18:25:21 IST 2011
```

---

