---
title: "Dell wireless 1350 true mobile card"
date: 2012-02-27
forum: Networking &amp; Wireless
---

### Post by mosstrumpet on 2012-02-27
Hello,
I have a dell inspiron 5100. I just recently installed Ubuntu on my laptop, so far everything works great with the exception that I can not get my wireless card to work. I've tried the ndiswrapper but have not had any luck with the driver installation. I do have the CD that came with the card it is a Dell wireless 1350 true mobile card, and I have it hard wired to the INTERNET as well if that can help. If you have any helpful hints or can walk me through this I would greatly appreciate it. Thanks

---

### Post by praseodym on 2012-02-27
Hi,

normally you dont need ndiswrapper for this. Uninstall it completely:

```
sudo modprobe -rf ndiswrapper
sudo apt-get remove --purge ndiswrapper-common ndiswrapper-utils-1.9 ndisgtk
sudo rm /etc/modprobe.d/ndiswrapper.conf
sudo rm -r /etc/ndiswrapper/* 
```
and check the device, and other infos via terminal (CTRL+ALT+T):

```
lcpci -nnk | grep -iA2 net
lsmod
iwconfig
rfkill list
```

---

