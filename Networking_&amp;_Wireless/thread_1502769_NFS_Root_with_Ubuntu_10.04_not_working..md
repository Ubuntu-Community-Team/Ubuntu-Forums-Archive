---
title: "NFS Root with Ubuntu 10.04 not working."
date: 2010-06-06
forum: Networking &amp; Wireless
---

### Post by AxelF on 2010-06-06
Hi,

I am trying to get a nfs root working with PXE using Ubuntu 10.04.  I have done this successfully with many versions previously, but for some reason with 10.04 I cannot make it work.  

When I boot I see:

> 
Loading vmlinuz-2.6.32-22-generic.....................................................................................
Loading initrd.img-2.6.32-22-generic-pxe............................................................................................................................................................ready.


At this point it just hangs.  Here is my configuration details.

pxelinux.cfg:
> 
LABEL linux
KERNEL vmlinuz-2.6.32-22-generic
APPEND root=/dev/nfs initrd=initrd.img-2.6.32-22-generic-pxe nfsroot=192.168.100.25:/nfsroot/rootlucid vga=785 ip=dhcp rw


I created a new initramfs using mkinitramfs, turing on MODULES=most and BOOT=nfs.  I have also tried various combinations of these two settings, and got the same results.   I am using a the stock 2.6.32.22 kernel.

To create the root file system I installed a base install of 10.4 and the used cp -ravx to copy it onto my server using nfs.

If anyone can help I would appreciate it, I have been mucking around with it for days getting no results.  

Axel

---

### Post by AxelF on 2010-06-07
I figured it out so I am posting the fix here.  Apparently my steps were correct, but the vga=765 option was causing the issue.  Once I removed that, everything booted normally.  Hopefully this might help someone else.

---

