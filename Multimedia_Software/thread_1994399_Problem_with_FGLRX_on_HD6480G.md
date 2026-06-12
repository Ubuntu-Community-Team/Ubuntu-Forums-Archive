---
title: "Problem with FGLRX on HD6480G"
date: 2012-06-02
forum: Multimedia Software
---

### Post by Randy M on 2012-06-02
I get this error when I install the Radeon drivers on my HP G7 with an HD6480G video card. How do I find out what the dependency problems are?

E: fglrx: subprocess installed post-installation script returned error exit status 10
E: fglrx-amdcccle: dependency problems - leaving unconfigured

---

### Post by inashdeen on 2012-06-02
May I know how did you install the fgrlx? did you use the additional dirver options in system settings (jockey-gtk)?

---

### Post by Randy M on 2012-06-02
I did a search for RADEON in the package manager and installed from there. Thanks for the response and any help you can provide.

---

### Post by inashdeen on 2012-06-02
have you tried this?

sudo apt-get update
sudo apt-get install fglrx fglrx-amdcccle fglrx-dev

---

### Post by Randy M on 2012-06-02
I still get an error.

root@randy-laptop:/home/randy# apt-get install fglrx fglrx-amdcccle fglrx-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
fglrx is already the newest version.
fglrx-amdcccle is already the newest version.
fglrx-dev is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up fglrx (2:8.723.1-0ubuntu6) ...
update-initramfs: deferring update (trigger activated)
Removing old fglrx-8.723.1 DKMS files...

------------------------------
Deleting module version: 8.723.1
completely from the DKMS tree.
------------------------------
Done.
Loading new fglrx-8.723.1 DKMS files...
First Installation: checking all kernels...
Building only for 2.6.32-41-generic
Building for architecture x86_64
Building initial module for 2.6.32-41-generic

Error! Bad return status for module build on kernel: 2.6.32-41-generic (x86_64)
Consult the make.log in the build directory
/var/lib/dkms/fglrx/8.723.1/build/ for more information.
dpkg: error processing fglrx (--configure):
 subprocess installed post-installation script returned error exit status 10
dpkg: dependency problems prevent configuration of fglrx-amdcccle:
 fglrx-amdcccle depends on fglrx; however:
  Package fglrx is not configured yet.
dpkg: error processing fglrx-amdcccle (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of fglrx-dev:
 fglrx-dev depends on fglrx; however:
  Package fglrx is not configured yet.
dpkg: error processing fglrx-dev (--configure):
 dependency problems - leaving unconfigured
Processing triggers for python-gmenu ...
No apport report written because the error message indicates its a followup error from a previous failure.
                          No apport report written because the error message indicates its a followup error from a previous failure.
                                                    Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.32-41-generic
Processing triggers for python-support ...
Errors were encountered while processing:
 fglrx
 fglrx-amdcccle
 fglrx-dev
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by Randy M on 2012-06-03
I gave up on 10.04 and went to 12.04. It'll take a while to get used to the new GUI, but I'll manage. Yes, I'm old. No, I don't like change. You don't have to get out of my yard, my wife likes it when people stop and smell the flowers.  :popcorn:Thanks for all the help!

---

### Post by inashdeen on 2012-06-03
Doesnt really understand the last part, but congratulation for the fix. well, you can't really help it, the world moves on. seriously. I work very hard last time to get my audio run on ubuntu 10.04 last time, they say it could work, but it just doesnt. at the end, is the upgrade that fix my prob. all the best!

---

