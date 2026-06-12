---
title: "trying to have a dvb-t usb cards working"
date: 2010-12-23
forum: Mythbuntu
---

### Post by danlin on 2010-12-23
I have an eb1a:2870 pinnacle pctv usb2 , and lately an elgato eyetv dtt usb2, both are called as "compatible and working with linux" on linuxtv.org ... but none of them is recognized by kernels...



lsusb

Bus 002 Device 002: ID eb1a:2870 eMPIA Technology, Inc. Pinnacle PCTV Stick
em28xx compiled module doesn't resolve...at the end i can recognize only some channels(italy) , i verified that on different computers and antennas...simply no reason why i can watch onlyand every the same "retecapri" channel. any channel reaserch find only a channel, so i suppose it's a driver problem anyway.

0fd9:003f ....nothing more

That's sad!!
any help??;)

---

### Post by BicyclerBoy on 2011-01-06
But what kernel version has the support ?
Your kernel is probably much older..

If your kernel is older you can upgrade by kernel ppa.
Or you can build the video 4 linux subsystem and add to your kernel.

You will also need linux-firmware & linux-firmware-nonfree packages

---

