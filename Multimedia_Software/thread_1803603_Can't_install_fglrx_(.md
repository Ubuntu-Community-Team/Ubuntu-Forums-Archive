---
title: "Can't install fglrx :("
date: 2011-07-13
forum: Multimedia Software
---

### Post by ethicalankit09 on 2011-07-13
hello to all 
i am trying to install ati drivers "fglrx" but i am getting lot of erros :-

```
root@HP-Pavalion:~# apt-get install fglrx
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  fglrx-amdcccle
The following NEW packages will be installed:
  fglrx fglrx-amdcccle
0 upgraded, 2 newly installed, 0 to remove and 31 not upgraded.
Need to get 0B/25.1MB of archives.
After this operation, 75.1MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Selecting previously deselected package fglrx.
(Reading database ... 228248 files and directories currently installed.)
Unpacking fglrx (from .../fglrx_2%3a8.780-0ubuntu2_i386.deb) ...
Selecting previously deselected package fglrx-amdcccle.
Unpacking fglrx-amdcccle (from .../fglrx-amdcccle_2%3a8.780-0ubuntu2_i386.deb) ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
Setting up fglrx (2:8.780-0ubuntu2) ...
update-alternatives: using /usr/lib/fglrx/ld.so.conf to provide /etc/ld.so.conf.d/GL.conf (gl_conf) in auto mode.
update-alternatives: warning: skip creation of /usr/lib32/libaticalcl.so because associated file /usr/lib32/fglrx/libaticalcl.so (of link group gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/lib32/libaticalrt.so because associated file /usr/lib32/fglrx/libaticalrt.so (of link group gl_conf) doesn't exist.
update-initramfs: deferring update (trigger activated)
Loading new fglrx-8.780 DKMS files...
First Installation: checking all kernels...
Building only for 2.6.38-8-generic
Building for architecture i686
Building initial module for 2.6.38-8-generic

Error! Bad return status for module build on kernel: 2.6.38-8-generic (i686)
Consult the make.log in the build directory
/var/lib/dkms/fglrx/8.780/build/ for more information.
Traceback (most recent call last):
  File "/usr/share/apport/package-hooks/dkms.py", line 57, in <module>
    report.write(open(apport.fileutils.make_report_path(report), 'w'))
IOError: [Errno 2] No such file or directory: '/var/crash/fglrx.0.crash'
dpkg: error processing fglrx (--configure):
 subprocess installed post-installation script returned error exit status 10
dpkg: dependency problems prevent configuration of fglrx-amdcccle:
 fglrx-amdcccle depends on fglrx; however:
  Package fglrx is not configured yet.
dpkg: error processing fglrx-amdcccle (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.38-8-generic
W: Possible missing firmware /lib/firmware/radeon/SUMO_rlc.bin for module radeon
W: Possible missing firmware /lib/firmware/radeon/PALM_me.bin for module radeon
W: Possible missing firmware /lib/firmware/radeon/PALM_pfp.bin for module radeon
W: Possible missing firmware /lib/firmware/radeon/CAYMAN_rlc.bin for module radeon
W: Possible missing firmware /lib/firmware/radeon/CAYMAN_mc.bin for module radeon
W: Possible missing firmware /lib/firmware/radeon/CAYMAN_me.bin for module radeon
W: Possible missing firmware /lib/firmware/radeon/CAYMAN_pfp.bin for module radeon
W: Possible missing firmware /lib/firmware/radeon/CAICOS_mc.bin for module radeon
W: Possible missing firmware /lib/firmware/radeon/CAICOS_me.bin for module radeon
W: Possible missing firmware /lib/firmware/radeon/CAICOS_pfp.bin for module radeon
W: Possible missing firmware /lib/firmware/radeon/TURKS_mc.bin for module radeon
W: Possible missing firmware /lib/firmware/radeon/TURKS_me.bin for module radeon
W: Possible missing firmware /lib/firmware/radeon/TURKS_pfp.bin for module radeon
W: Possible missing firmware /lib/firmware/radeon/BTC_rlc.bin for module radeon
W: Possible missing firmware /lib/firmware/radeon/BARTS_mc.bin for module radeon
W: Possible missing firmware /lib/firmware/radeon/BARTS_me.bin for module radeon
W: Possible missing firmware /lib/firmware/radeon/BARTS_pfp.bin for module radeon
Processing triggers for python-support ...
Errors were encountered while processing:
 fglrx
 fglrx-amdcccle
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@HP-Pavalion:~# 
 
```
lspci | grep VGA

 ```


01:00 0 VGA compatible controller: ATI Technologies Inc Redwood [Radeon 5650 Series]


```

---

