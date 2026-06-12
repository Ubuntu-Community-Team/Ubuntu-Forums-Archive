---
title: "NVIDIA GeForce FX 5500 Driver Install Failed on Maverick"
date: 2010-10-13
forum: Multimedia Software
---

### Post by FullMetalManiac on 2010-10-13
Okay, tried to install drivers for FX 5500 today, the one that Ubuntu recommended (173) and the current version (260). Both installs failed when it tried to set up python-support.  Returned an exit status of "10".  I don't know what that means.  I could really use some help, because I just installed UT2K4, and without the driver, I can't play it. :(  I'm running the latest release, as noted in the thread title.  Dunno if it helps, but it was a clean install, because an alternate iso upgrade failed and mucked up 10.04.

---

### Post by FullMetalManiac on 2010-10-13
Okay, I can give a little more information, now.

Here's what we get when I install something:

```
------------------------------
Deleting module version: 260.19.06
completely from the DKMS tree.
------------------------------
Done.
Loading new nvidia-current-260.19.06 DKMS files...
First Installation: checking all kernels...
Building only for 2.6.35-22-generic
Building for architecture i686
Building initial module for 2.6.35-22-generic

Error! Bad return status for module build on kernel: 2.6.35-22-generic (i686)
Consult the make.log in the build directory
/var/lib/dkms/nvidia-current/260.19.06/build/ for more information.
Traceback (most recent call last):
  File "/usr/share/apport/package-hooks/dkms.py", line 57, in <module>
    report.write(open(apport.fileutils.make_report_path(report), 'w'))
IOError: [Errno 2] No such file or directory: '/var/crash/nvidia-current.0.crash'
dpkg: error processing nvidia-current (--configure):
 subprocess installed post-installation script returned error exit status 10
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.UTF8.cache...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.35-22-generic
Processing triggers for python-support ...
Errors were encountered while processing:
 nvidia-current
```


And here's what we get when we check the 'make.log' file:

```
DKMS make.log for nvidia-current-260.19.06 for kernel 2.6.35-22-generic (i686)
Wed Oct 13 14:19:07 EDT 2010

The C compiler 'cc' does not appear to be able to
create executables.  Please make sure you have 
your Linux distribution's gcc and libc development
packages installed.

*** Failed CC sanity check. Bailing out! ***

make: *** [select_makefile] Error 1
```

---

### Post by FullMetalManiac on 2010-10-15
Anybody?

---

### Post by Dr_Willis on 2010-11-15
Having a similar problem. I recall in the past that for my 5500 based system I had to use an older nvidia driver version then what it suggested from the 'hardware-drivers' 'additional drivers' tool.

I just cant seem to figure out what version i had before that worked.


I recall having to fight with this every time i reinstall my 'backup' machine  with the 5500 card.

---

