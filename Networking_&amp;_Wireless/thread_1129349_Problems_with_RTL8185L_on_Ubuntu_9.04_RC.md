---
title: "Problems with RTL8185L on Ubuntu 9.04 RC"
date: 2009-04-18
forum: Networking &amp; Wireless
---

### Post by DL21 on 2009-04-18
Hi,
I've got a problem with RTL8185L (using a PCI card) on Ubuntu 9.04 RC.
When it's connected, After booting ubuntu, when you connect (i have enabled auto-connection), it just simply freezes.
I searched in different threads to install the driver, but it doesn't work.
Can you help me, please ?
Thanks, DL21.

EDIT :

Here's how I solved my problem (Used "Amarina Wireless PCI CARD 54M 802.11G 54 Mbps" installation cd) :

- Boot with "Ubuntu 9.04 (recovery mode)" at GRUB screen.
- Choose "root" when asked for mode

- Open your CD tray and put the "Amarina Wireless PCI CARD 54M 802.11G 54 Mbps" installation cd

- Install windows xp drivers with ndiswrapper (remove the $) :
```
$ mkdir ~/.driver/
$ mount /dev/cdrom /media/cdrom0/
$ cd /media/cdrom0/wl8185\ PCI/Driver_1097_2KXP_0201/WINXP/
$ cp net8185.inf ~/.driver/
$ cp rtl8185.sys ~/.driver/
$ cd ~/.driver/
$ ndiswrapper -i net8185.inf
$ ndiswrapper -m
$ modprobe -r rtl8180
$ modprobe ndiswrapper
```

- Blacklist the default driver (remove the $) :
```
$ nano /etc/modprobe.d/blacklist.conf
```
- At the end of the file, add :
```
blacklist rtl8180
```
- Close the file with Ctrl + X.

- Reboot your computer, it'll be working ! :)

---

### Post by Crafty Kisses on 2009-04-18
When you say "freezes" does the whole computer freeze?

---

### Post by DL21 on 2009-04-18
I think, yeah, i can't move the mouse cursor nor use the keyboard...

---

### Post by DL21 on 2009-04-18
Hrm, never mind, it was just a conflict between drivers...
I told how I resolved the problem in first post.

---

