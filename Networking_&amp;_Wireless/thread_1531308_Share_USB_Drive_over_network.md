---
title: "Share USB Drive over network"
date: 2010-07-14
forum: Networking &amp; Wireless
---

### Post by Tech2077 on 2010-07-14
I have a usb 1tb drive that I want to share over my netowork, but when i share it through nautilus, it doesn't mount right  on other computers, ect. Is there a way to mount it. The location of the drive is /media/FreeAgent Drive___

---

### Post by ubunterooster on 2010-07-14
In the Host's nautilus, go to "network"

see also: [http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/](http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/)

---

### Post by Tech2077 on 2010-07-14
I'm sorry, but that didn't help me at all, i know how to make a share, i know how to view network shares, i just have problems sharing usb drives and need a way to share them.

---

### Post by sundays211 on 2010-07-14
try adding a line to the /etc/fstab file to automatically mount the external drive.

---

