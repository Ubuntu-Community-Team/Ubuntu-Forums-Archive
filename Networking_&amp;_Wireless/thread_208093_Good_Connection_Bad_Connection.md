---
title: "Good Connection Bad Connection"
date: 2006-07-03
forum: Networking &amp; Wireless
---

### Post by mattoman on 2006-07-03
Using ndiswrapper for WUSB54G V4 acts as if working great. connects to wireless router sucessfully. Internet services work..mostly. I can only access so many urls through firefox, synpatic, everything that needs an internet address. I've adjusted Fire Fox internet connection settings every way possible to no avail... Ideas?

Thanks!

Matt McMurry

Further, Network Manager will not enable as it cannot find a network device. Also running wpa_gui out of curiousity does not see the device either, however, it is clearly connected to the network and i do have an ip address. 

This may be tied into the fact that everytime it starts up i have to type

sudo depmod
sudo modprobe ndiswrapper

inorder to make the hardware present, also the hardware is seen by the default network settings as to the reason i know i have a good strong connection to the router.

---

