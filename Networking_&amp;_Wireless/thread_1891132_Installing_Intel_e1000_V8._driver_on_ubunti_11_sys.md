---
title: "Installing Intel e1000 V8. driver on ubunti 11 system"
date: 2011-12-04
forum: Networking &amp; Wireless
---

### Post by RoyB (Aus) on 2011-12-04
I've tried following the README instructions for installing the latest E1000 driver on my 64 bit Ubuntu 11 server but to no avail -the system continues to load the old V7. driver.

I have built the driver and have a cope of e1000.ko in a subdirectory of home.  What is the proper sequence of commands to put the new driver where it belongs and tell the os to use the new version?  The commands shown in the driver README don't seem to work on an Ubuntu system.  I've copied the README section below in case it will be useful.

The Intel make install doesn't appear to place the new driver in /lib/modules/2.6.38-13-server/kernel/net/e1000.  The new driver is placed in /lib/modules/2.6.38-13-server/kernel/drivers/net/e1000

insmod /lib/modules/2.6.38-13-server/kernel/drivers/net/e1000 runs but when the system is restarted the old driver is still present.

Could someone inform me of the proper procedure for installing the intel e1000 V8.n driver?



README Extract:
--------------------------------------------------------
1. Move the base driver tar file to the directory of your choice.  For
   example, use /home/username/e1000 or /usr/local/src/e1000.

2. Untar/unzip archive:

     tar zxf e1000-x.x.x.tar.gz

3. Change to the driver src directory:

     cd e1000-x.x.x/src/

4. Compile the driver module:

     make install

   The binary will be installed as:

     /lib/modules/<KERNEL VERSION>/kernel/drivers/net/e1000/e1000.[k]o

   The install locations listed above are the default locations.  They
   might not be correct for certain Linux distributions.

5. Load the module using either the insmod or modprobe command:

     modprobe e1000

     insmod e1000

   Note that for 2.6 kernels the insmod command can be used if the full
   path to the driver module is specified.  For example:

     insmod /lib/modules/<KERNEL VERSION>/kernel/drivers/net/e1000/e1000.ko

   With 2.6 based kernels also make sure that older e1000 drivers are
   removed from the kernel, before loading the new module:

     rmmod e1000; modprobe e1000

---

