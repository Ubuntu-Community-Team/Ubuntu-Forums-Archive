---
title: "/etc/init.d/iscsitarget does not exist?"
date: 2012-07-11
forum: Networking &amp; Wireless
---

### Post by acidrop on 2012-07-11
Hello!

I have  
> Ubuntu 3.2.0-24-generic #39-Ubuntu SMP Mon May 21 16:52:17 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

And I am trying to setup an simple iscsi target.I give the following command to install:

> sudo apt-get install iscsitarget iscsitarget-source iscsitarget-dkms

> 
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following extra packages will be installed:
  dkms module-assistant
Recommended packages:
  iscsitarget-module linux-headers-2.6
The following NEW packages will be installed:
  dkms iscsitarget iscsitarget-dkms iscsitarget-source module-assistant
0 upgraded, 5 newly installed, 0 to remove and 3 not upgraded.
Need to get 0 B/366 kB of archives.
After this operation, 1,560 kB of additional disk space will be used.
Do you want to continue [Y/n]?
Selecting previously unselected package dkms.
(Reading database ... 166573 files and directories currently installed.)
Unpacking dkms (from .../dkms_2.2.0.3-1ubuntu3_all.deb) ...
Selecting previously unselected package iscsitarget.
Unpacking iscsitarget (from .../iscsitarget_1.4.20.2-5ubuntu3_amd64.deb) ...
Selecting previously unselected package iscsitarget-dkms.
Unpacking iscsitarget-dkms (from .../iscsitarget-dkms_1.4.20.2-5ubuntu3_all.deb) ...
Selecting previously unselected package module-assistant.
Unpacking module-assistant (from .../module-assistant_0.11.4_all.deb) ...
Selecting previously unselected package iscsitarget-source.
Unpacking iscsitarget-source (from .../iscsitarget-source_1.4.20.2-5ubuntu3_all.deb) ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
Setting up dkms (2.2.0.3-1ubuntu3) ...
Setting up iscsitarget (1.4.20.2-5ubuntu3) ...
Setting up iscsitarget-dkms (1.4.20.2-5ubuntu3) ...

Creating symlink /var/lib/dkms/iscsitarget/1.4.20.2/source ->
                 /usr/src/iscsitarget-1.4.20.2

DKMS: add completed.

Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area....
make KERNELRELEASE=3.2.0-24-generic -C /lib/modules/3.2.0-24-generic/build M=/var/lib/dkms/iscsitarget/1.4.20.2/build.....
cleaning build area....

DKMS: build completed.

iscsi_trgt:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.2.0-24-generic/updates/dkms/

depmod....

DKMS: install completed.
Setting up module-assistant (0.11.4) ...
Setting up iscsitarget-source (1.4.20.2-5ubuntu3) ...


It seems to install correctly...but when I go to /etc/init.d there is no iscsitarget file to start the service.

Any suggestions?

---

