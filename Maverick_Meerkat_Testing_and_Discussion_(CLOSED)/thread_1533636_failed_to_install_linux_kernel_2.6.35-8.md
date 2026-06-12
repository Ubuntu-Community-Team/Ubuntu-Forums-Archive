---
title: "failed to install linux kernel 2.6.35-8"
date: 2010-07-18
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by cjcj on 2010-07-18
Tried to upgrade to Maverick. Most downloaded and installed but the installation of the kernel bailed out. :mad:

Has anyone else had this problem? Anything to suggest? There appears to be some dependencies missing. more info ..


At end of update process I get

E: linux-image-2.6.35-8-generic: subprocess installed post-installation script returned error exit status 2
E: linux-image-generic: dependency problems - leaving unconfigured
E: linux-generic: dependency problems - leaving unconfigured
E: linux-image: dependency problems - leaving unconfigured
E: linux: dependency problems - leaving unconfigured
E: initramfs-tools: subprocess installed post-installation script returned error exit status 1


In order to get more information I tried upgrading at the command line. 

root@Chris-Deskop:~# apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
6 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? Y
Setting up initramfs-tools (0.97.2ubuntu1) ...
update-initramfs: deferring update (trigger activated)
Setting up linux-image-2.6.35-8-generic (2.6.35-8.13) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.35-8-generic
E: /usr/share/initramfs-tools/hooks/iscan failed with return 1.
update-initramfs: failed for /boot/initrd.img-2.6.35-8-generic
Failed to create initrd image.
dpkg: error processing linux-image-2.6.35-8-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.35-8-generic; however:
  Package linux-image-2.6.35-8-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image:
 linux-image depends on linux-image-generic (= 2.6.35.8.9); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-image (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux:
 linux depends on linux-image (= 2.6.35.8.9); however:
  Package linux-image is not configured yet.
dpkg: error processing linux (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.35.8.9); however:
  Package linux-image-generic is not No apport report written because the error message indicates it's a follow-up error from a previous failure.
                                                                 No apport report written because the error message indicates it's a follow-up error from a previous failure.
             No apport report written because MaxReports has already been reached
 No apport report written because MaxReports has already been reached
                                                                     configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.32-23-generic
E: /usr/share/initramfs-tools/hooks/iscan failed with return 1.
update-initramfs: failed for /boot/initrd.img-2.6.32-23-generic
dpkg: error processing initramfs-tools (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports has already been reached
                                                                    Errors were encountered while processing:
 linux-image-2.6.35-8-generic
 linux-image-generic
 linux-image
 linux
 linux-generic
 initramfs-tools
E: Sub-process /usr/bin/dpkg returned an error code (1)


get same when I try 
    dpkg --configure -a
    apt-get dist-upgrade

---

### Post by ranch hand on 2010-07-18
Have you run;
```

sudo dpkg --configure -a

```
?

This would be a good place to start.  If it doesn't get it all the first time try it again.

If that doesn't get it try booting to recovery and use the "dpkg fix broken files" option.

---

### Post by jfernyhough on 2010-07-18
Try aptitude in place of apt-get. In my experience it's far better at resolving dependencies (and another reason I don't understand why it's being removed as installed by default). Either that, or use synaptic or update-manager.

You'll also want to remove the 2.6.32 kernel. Looks like this is what is making initramfs fail.

---

