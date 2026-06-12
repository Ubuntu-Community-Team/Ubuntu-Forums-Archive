---
title: "USB WIFI Key: RTL8187"
date: 2013-05-20
forum: Networking &amp; Wireless
---

### Post by MR2 on 2013-05-20
I have a RTL8187 usb wifi key, for driver problems (at many times wifi not go or go too slow - the problem is tested and related to drivers, because with x86 ndiswrapper and XP drivers work well) i need a help.

I use XP drivers through ndiswrapper,but this work only on x86 version of ubuntu, because i have a x64 hardware and ubuntu go faster on x64 version, so i want use it.

I repeat for make clear:

Linux Drivers: Not Work Well or too old for compiling

Ndiswrapper+XP drivers: [x86]WORK - [x64]NOT WORK

Please help me if you know how make working ndiswrapper on x64, or (if pssible) i can install ndiswrapper and network related stuff [x86 version] on x64 Ubuntu and use it? (i think yes but i donìt know exactly what install in x86 version and make off well x64 related stuff)


Thanks

---

### Post by mörgæs on 2013-05-21
Moved to Networking and Wireless, as this is not specific for Dell.

---

### Post by MR2 on 2013-06-16
sudo modprobe rtl8187
sudo iwconfig wlan1 rate 5.5M fixed 
sudo iwconfig wlan1 frag 2346
sudo iwconfig wlan1 rts 2347
sudo iwconfig wlan1 txpower 30

solved by myself

---

