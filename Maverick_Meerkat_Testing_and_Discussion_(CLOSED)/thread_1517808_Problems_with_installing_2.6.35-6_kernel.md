---
title: "Problems with installing 2.6.35-6 kernel"
date: 2010-06-25
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by aviramof on 2010-06-25
I tried sudo dpkg --configure -a and got this:

Setting up linux-image-2.6.35-6-generic (2.6.35-6.7) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.35-6-generic
cpio: ./etc/modprobe.d/motorola_ve.options: Cannot stat: No such file or directory
cpio: blank line ignored
/usr/sbin/update-initramfs: 527: initramfs_bak: parameter not set
Failed to create initrd image.
dpkg: error processing linux-image-2.6.35-6-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.35-6-generic; however:
  Package linux-image-2.6.35-6-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.35.6.7); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:

---

### Post by jppr on 2010-06-25
Why you don´t install it in synaptic? install new and remove old, or wait that this 
[https://launchpad.net/ubuntu/maverick/+source/linux-meta/2.6.35.6.7](https://launchpad.net/ubuntu/maverick/+source/linux-meta/2.6.35.6.7) is comes in repos and update then all kernel packages

---

### Post by aviramof on 2010-06-26
I installed it from update manager and it didn't worked properly.

Maybe it had something to do with the fglrx driver i'm using but it's not working so well.

---

### Post by ranch hand on 2010-06-26
> **aviramof said:**
> I installed it from update manager and it didn't worked properly.
That is not a big surprise.

On these testing OS' you should really use a real package manager.

---

### Post by aviramof on 2010-06-26
Problem solved:
[http://ubuntuforums.org/showthread.php?t=1518070](http://ubuntuforums.org/showthread.php?t=1518070)

---

