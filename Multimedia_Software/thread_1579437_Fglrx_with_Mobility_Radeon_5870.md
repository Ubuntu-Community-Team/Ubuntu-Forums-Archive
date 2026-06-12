---
title: "Fglrx with Mobility Radeon 5870"
date: 2010-09-21
forum: Multimedia Software
---

### Post by Cyclops_ on 2010-09-21
Hey, all,

I'm trying to follow this guide: 

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

I'm doing the option where I downloaded the .run file from the ATI site.  I ran it, it created 6 .deb files for me.  When I go to install the .deb files I get the following:

```

$ sudo dpkg -i *.deb

.....  a bunch of stuff .....

Saving as /etc/ati/logo.xbm.example.dpkg-bak ...
dpkg: error processing xorg-driver-fglrx_8.771-0ubuntu1_amd64.deb (--install):
 trying to overwrite '/usr/share/fglrx/atigetsysteminfo.sh', which is also in package fglrx 2:8.723.1-0ubuntu4
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Selecting previously deselected package xorg-driver-fglrx-dev.
Unpacking xorg-driver-fglrx-dev (from xorg-driver-fglrx-dev_8.771-0ubuntu1_amd64.deb) ...
dpkg: dependency problems prevent configuration of fglrx-amdcccle:
 fglrx-amdcccle depends on xorg-driver-fglrx; however:
  Package xorg-driver-fglrx is not installed.
 fglrx-amdcccle depends on fglrx; however:
  Package fglrx is not configured yet.
dpkg: error processing fglrx-amdcccle (--install):
 dependency problems - leaving unconfigured
Setting up fglrx-kernel-source (2:8.771-0ubuntu1) ...
Removing old fglrx- DKMS files...

Error! Invalid number of parameters passed.
Usage: remove -m <module> -v <module-version> --all
   or: remove -m <module> -v <module-version> -k <kernel-version>
Loading new fglrx-8.771 DKMS files...
First Installation: checking all kernels...
Building initial module for 2.6.32-24-generic, architecture -a x86_64

Error! Bad return status for module build on kernel: 2.6.32-24-generic (x86_64)
Consult the make.log in the build directory
/var/lib/dkms/fglrx/8.771/build/ for more information.
Done.

Error! Could not locate fglrx.ko for module fglrx in the DKMS tree.
You must run a dkms build for kernel 2.6.32-24-generic (x86_64) first.
update-initramfs: deferring update (trigger activated)

Setting up fglrx-modaliases (2:8.771-0ubuntu1) ...
Setting up libamdxvba1 (2:8.771-0ubuntu1) ...

dpkg: dependency problems prevent configuration of xorg-driver-fglrx-dev:
 xorg-driver-fglrx-dev depends on xorg-driver-fglrx; however:
  Package xorg-driver-fglrx is not installed.
dpkg: error processing xorg-driver-fglrx-dev (--install):
 dependency problems - leaving unconfigured
Processing triggers for desktop-file-utils ...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.32-24-generic
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 xorg-driver-fglrx_8.771-0ubuntu1_amd64.deb
 fglrx-amdcccle
 xorg-driver-fglrx-dev

```Any help would be GREAT!

Thanks!

---

### Post by Cyclops_ on 2010-09-21
Apparently I also get an error when removing the packages:

```


(Reading database ... 186522 files and directories currently installed.)
Removing fglrx ...
dpkg-divert: mismatch on package
  when removing `diversion of /usr/lib/libGL.so.1.2 to /usr/lib/fglrx/libGL.so.1.2.xlibmesa by fglrx'
  found `diversion of /usr/lib/libGL.so.1.2 to /usr/lib/fglrx/libGL.so.1.2.xlibmesa by xorg-driver-fglrx'
dpkg: error processing fglrx (--purge):
 subprocess installed post-removal script returned error exit status 2
Processing triggers for ureadahead ...
Errors were encountered while processing:
 fglrx
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:


```

---

### Post by joxl on 2010-10-24
In reply to your first post; I have no experience trying to install drivers from the ATI website, I won't be much help there.  I have a XFX Radeon HD 4650 graphics card and have been able to get everything I need out of it using drivers from the Ubuntu repo's.

> **Cyclops_ said:**
> ```
dpkg-divert: mismatch on package
  when removing `diversion of /usr/lib/libGL.so.1.2 to  /usr/lib/fglrx/libGL.so.1.2.xlibmesa by fglrx'
  found `diversion of /usr/lib/libGL.so.1.2 to  /usr/lib/fglrx/libGL.so.1.2.xlibmesa by xorg-driver-fglrx'

```


I just had this exact problem while attempting to uninstall the **fglrx** package.  Here's what I was trying to do, and what happened:

```
$ sudo apt-get remove -y --purge fglrx-modaliases fglrx  xorg-driver-fglrx

<snip>
dpkg-divert: mismatch on package
  when removing `diversion of /usr/lib/libGL.so.1.2 to /usr/lib/fglrx/libGL.so.1.2.xlibmesa by fglrx'
  found `diversion of /usr/lib/libGL.so.1.2 to /usr/lib/fglrx/libGL.so.1.2.xlibmesa by xorg-driver-fglrx'
dpkg: error processing fglrx (--purge):
 subprocess installed post-removal script returned error exit status 2
<snip>
Errors were encountered while processing:
 fglrx
```SIDENOTE: I'm not positive what caused this problem, but I have a guess.  In my case, my system crashed mid-upgrade to Maverick 10.10.  I've had to do some hacking around to get everything up and running since then.  I suspect that fglrx is a little out of whack due to the upgrade problems.

It seems that the uninstall process is attempting to remove a package diversion, but isn't finding the diversion it's expecting to remove.  To fix it, I changed the diversion to what it was "expecting" to remove.  I'm sure there's a way to do this using dpkg-divert, but I decided to manually tweak the diversion myself.  In order to do this you need to edit the file "/var/lib/dpkg/diversions".  Back up the file, and then open it in a text editor.

```
# first, make a backup
sudo cp /var/lib/dpkg/diversions /var/lib/dpkg/diversions.bak
# open and edit
sudo gedit /var/lib/dpkg/diversions
```Somewhere in the file you should find three consecutive lines that look like this:

```
/usr/lib/libGL.so.1.2
/usr/lib/fglrx/libGL.so.1.2.xlibmesa
xorg-driver-fglrx
```Change the last line from "xorg-driver-fglrx" to "fglrx".  The three lines should now look like this:

```
/usr/lib/libGL.so.1.2
/usr/lib/fglrx/libGL.so.1.2.xlibmesa
fglrx
```Save the file, now apt-get should be able to remove fglrx.  It worked for me.

Good luck.

---

