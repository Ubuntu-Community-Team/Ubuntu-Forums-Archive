---
title: "help with Realtek 10ec:8176 wireless card"
date: 2012-05-28
forum: Networking &amp; Wireless
---

### Post by kingaxon on 2012-05-28
I just got a new computer, and started using ubuntu for the first time. I've been searching and reading up, but I cannot get my wireless working. I've looked and found the info for my wireless card is

02:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8176 (rev 01)

02:00.0 0280: 10ec:8176 (rev 01)

I used ndiswrapper to install the driver, but it says there is no hardware. After a little more looking i'm pretty sure that I got the wrong driver. I got what I am sure is the proper driver from the realtek site, but I can't find the .inf file to use with ndiswrapper. I've been reading other topics and forums, but I haven't found any that were able to help. I'll admit it might just be because I'm not entirely sure of what to do, I've only been following the instructions other people have posted to fix the problem. Any insight into this would be a big help.

---

### Post by nothingspecial on 2012-05-29
*Thread moved to **Networking & Wireless**.*

---

### Post by praseodym on 2012-05-29
Hi,

this device normally works with the native driver, ndiswrapper is not needed, so you may uninstall it via terminal (CTRL+ALT+T):
```

sudo modprobe -rf ndiswrapper
sudo apt-get remove --purge ndiswrapper-common ndiswrapper-utils-1.9 ndisgtk
sudo rm /etc/modprobe.d/ndiswrapper.conf
sudo rm -r /etc/ndiswrapper/* 
```
Reboot after that, and show the terminal outputs of the following commands:
```
iwconfig
rfkill list
lsmod
```

---

