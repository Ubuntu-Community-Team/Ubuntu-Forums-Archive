---
title: "I have a problem with initramfs-tools i have an error with it"
date: 2010-06-26
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by aviramof on 2010-06-26
cpio: ./etc/modprobe.d/motorola_ve.options: Cannot stat: No such file or directory
cpio: blank line ignored
update-initramfs: failed for /boot/initrd.img-2.6.35-5-generic
dpkg: error processing initramfs-tools (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 initramfs-tools
E: Sub-process /usr/bin/dpkg returned an error code (1

---

### Post by aviramof on 2010-06-26
Problem solved i deleted motorola_ve.options which i created and everything is fine now.

---

