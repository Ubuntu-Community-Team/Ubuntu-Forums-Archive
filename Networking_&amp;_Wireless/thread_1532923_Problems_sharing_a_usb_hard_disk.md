---
title: "Problems sharing a usb hard disk"
date: 2010-07-17
forum: Networking &amp; Wireless
---

### Post by WesleyNeary on 2010-07-17
Hi,

Have a home network consisting of a Desktop and a Laptop Both Running 10.4,
The desktop has a usb hard drive attached that contains all files music vids photos etc.

Have gone in and set up the share of the drive in the desktop and changed all the permissions etc.

When i open network on the laptop the hard disk is visible but when i double click to access i get the following error message

"Unable to mount location"
"failed to mount windows share"

Please Help

---

### Post by Morbius1 on 2010-07-17
>  Have gone in and set up the share of the drive in the desktop and  changed all the permissions etc.I'm going to guess this is using Samba so the question becomes what method of Samba are you using: Nautilus-share or Classic-share. Posting the output of the following commands will tell us that and will tell us how they are configured:
```
net usershare info
testparm -s
```>  The desktop has a usb hard drive attached that contains all files music  vids photos etc. How is the external drive formatted ( FAT32, ntfs, ext3 ? ) and how is it mounted? Did you set up a mount in fstab?

---

