---
title: "fglrx_experimental_9 fails to install"
date: 2012-11-17
forum: Multimedia Software
---

### Post by Yuioup on 2012-11-17
Hi,

I'm trying to install fglrx_experimental_9 on my machine but for some reason it fails. This is what I'm trying to do:

moni@moni-HPS:~$ jockey-text --list
xorg:fglrx - ATI/AMD proprietary FGLRX graphics driver (Proprietary, Enabled, In use)
xorg:fglrx_experimental_9 - ATI/AMD proprietary FGLRX graphics driver (Proprietary, Disabled, Not in use)
xorg:fglrx_updates - ATI/AMD proprietary FGLRX graphics driver (post-release updates) (Proprietary, Disabled, Not in use)
moni@moni-HPS:~$ sudo jockey-text --enable=xorg:fglrx_experimental_9
[sudo] password for moni: 

Sorry, installation of this driver failed.

Please have a look at the log file for details: /var/log/jockey.log

So I take a look at jockey.log but it does not give me any indication as to why it failed:

2012-11-17 10:05:22,623 DEBUG: install progress libc-bin 37.500000
2012-11-17 10:05:22,853 DEBUG: install progress dpkg-exec 37.500000
2012-11-17 10:05:23,122 DEBUG: install progress fglrx-experimental-9 37.500000
2012-11-17 10:05:23,122 DEBUG: install progress fglrx-experimental-9 43.750000
2012-11-17 10:05:36,369 DEBUG: install progress fglrx-experimental-9 50.000000
2012-11-17 10:05:36,373 DEBUG: install progress fglrx-experimental-9 56.250000
2012-11-17 10:05:36,411 DEBUG: install progress fglrx-amdcccle-experimental-9 56.250000
2012-11-17 10:05:36,511 DEBUG: install progress fglrx-amdcccle-experimental-9 62.500000
2012-11-17 10:05:37,210 DEBUG: install progress fglrx-amdcccle-experimental-9 68.750000
2012-11-17 10:05:37,214 DEBUG: install progress fglrx-amdcccle-experimental-9 75.000000
2012-11-17 10:05:37,221 DEBUG: install progress ureadahead 75.000000
2012-11-17 10:05:37,562 DEBUG: install progress dpkg-exec 75.000000
2012-11-17 10:05:37,603 DEBUG: install progress fglrx-experimental-9 75.000000
2012-11-17 10:05:37,704 DEBUG: install progress fglrx-experimental-9 81.250000
2012-11-17 10:06:03,598 DEBUG: install progress fglrx-experimental-9 87.500000
2012-11-17 10:06:03,636 DEBUG: install progress bamfdaemon 87.500000
2012-11-17 10:06:03,656 DEBUG: install progress fglrx-amdcccle-experimental-9 87.500000
2012-11-17 10:06:03,665 DEBUG: install progress fglrx-amdcccle-experimental-9 93.750000
2012-11-17 10:06:03,669 DEBUG: install progress fglrx-amdcccle-experimental-9 100.000000
2012-11-17 10:06:03,674 DEBUG: install progress initramfs-tools 100.000000
2012-11-17 10:06:09,864 DEBUG: install progress libc-bin 100.000000
2012-11-17 10:06:11,568 DEBUG: (Reading database ... 155568 files and directories currently installed.)
Removing fglrx-amdcccle ...
Removing fglrx ...
Removing all DKMS Modules
Done.
update-alternatives: removing manually selected alternative - switching x86_64-linux-gnu_gl_conf to auto mode
update-alternatives: using /usr/lib/pxpress/ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in auto mode.
update-alternatives: warning: skip creation of /usr/bin/amdcccle because associated file /usr/lib/fglrx/bin/amdcccle (of link group x86_64-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/share/applications/ubuntu-amdcccle.desktop because associated file /usr/share/fglrx/amdcccle.desktop (of link group x86_64-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/share/applications/ubuntu-amdccclesu.desktop because associated file /usr/share/fglrx/amdccclesu.desktop (of link group x86_64-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /etc/OpenCL/vendors/amdocl32.icd because associated file /usr/lib/fglrx/etc/OpenCL/vendors/amdocl32.icd (of link group x86_64-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/bin/amdupdaterandrconfig because associated file /usr/lib/fglrx/bin/amdupdaterandrconfig (of link group x86_64-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: skip creation of /usr/bin/amdxdg-su because associated file /usr/lib/fglrx/bin/amdxdg-su (of link group x86_64-linux-gnu_gl_conf) doesn't exist.
update-alternatives: warning: not replacing /usr/lib/x86_64-linux-gnu/xorg/extra-modules with a link.
update-alternatives: removing manually selected alternative - switching i386-linux-gnu_gl_conf to auto mode
update-alternatives: using /usr/lib/pxpress/alt_ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode.
update-alternatives: using /usr/lib/x86_64-linux-gnu/mesa/ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in auto mode.
update-alternatives: warning: not replacing /usr/lib/x86_64-linux-gnu/xorg/extra-modules with a link.
update-alternatives: using /usr/lib/i386-linux-gnu/mesa/ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode.
update-initramfs: deferring update (trigger activated)
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.2.0-33-generic
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Selecting previously unselected package fglrx-experimental-9.
(Reading database ... 155296 files and directories currently installed.)
Unpacking fglrx-experimental-9 (from .../fglrx-experimental-9_2%3a9.010-0ubuntu0.1_amd64.deb) ...
Selecting previously unselected package fglrx-amdcccle-experimental-9.
Unpacking fglrx-amdcccle-experimental-9 (from .../fglrx-amdcccle-experimental-9_2%3a9.010-0ubuntu0.1_amd64.deb) ...
Processing triggers for ureadahead ...
Setting up fglrx-experimental-9 (2:9.010-0ubuntu0.1) ...
update-alternatives: using /usr/lib/fglrx/ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in auto mode.
update-alternatives: warning: forcing reinstallation of alternative /usr/lib/fglrx/ld.so.conf because link group x86_64-linux-gnu_gl_conf is broken.
update-alternatives: using /usr/lib/fglrx/alt_ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode.
update-initramfs: deferring update (trigger activated)
Loading new fglrx-experimental-9-9.010 DKMS files...
First Installation: checking all kernels...
Building only for 3.2.0-33-generic
Building for architecture x86_64
Building initial module for 3.2.0-33-generic
Done.

fglrx_experimental_9:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.2.0-33-generic/updates/dkms/

depmod....

DKMS: install completed.
update-initramfs: deferring update (trigger activated)
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Setting up fglrx-amdcccle-experimental-9 (2:9.010-0ubuntu0.1) ...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.2.0-33-generic
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

2012-11-17 10:06:11,820 WARNING: /sys/module/fglrx_experimental_9/drivers does not exist, cannot rebind fglrx_experimental_9 driver
2012-11-17 10:06:11,897 ERROR: xorg:fglrx_experimental_9: get_alternative_by_name(fglrx-experimental-9) returned nothing
2012-11-17 10:06:11,996 DEBUG: fglrx.enabled(fglrx_experimental_9): target_alt None current_alt /usr/lib/fglrx/ld.so.conf other target alt None other current alt /usr/lib/fglrx/alt_ld.so.conf
2012-11-17 10:06:11,996 DEBUG: fglrx_experimental_9 is not the alternative in use

Is there something else I can do? I'm using 12.04 LTS on 64 bit using an ATI Radeon HD 6700 card.

---

### Post by Yuioup on 2012-11-17
... but wait a minute!

I rebooted my machine and now have a "AMD Testing use only" box at the bottom right of my screen. It looks like it works because I can launch Team Fortress 2 with no problem.

Running this does this:

moni@moni-HPS:~$ jockey-text --list
xorg:fglrx - ATI/AMD proprietary FGLRX graphics driver (Proprietary, Disabled, Not in use)
xorg:fglrx_experimental_9 - ATI/AMD proprietary FGLRX graphics driver (Proprietary, Disabled, Not in use)
xorg:fglrx_updates - ATI/AMD proprietary FGLRX graphics driver (post-release updates) (Proprietary, Disabled, Not in use)

So I guess it works but it just doesn't show up in jockey.

That's ok because they're experimental drivers.

This thread may be closed as far as I'm concerned.

---

