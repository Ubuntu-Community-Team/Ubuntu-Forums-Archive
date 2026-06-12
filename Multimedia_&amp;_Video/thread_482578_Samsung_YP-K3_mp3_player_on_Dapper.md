---
title: "Samsung YP-K3 mp3 player on Dapper"
date: 2007-06-23
forum: Multimedia &amp; Video
---

### Post by gpaciga on 2007-06-23
I just got a Samsung YP-K3 mp3 player and am trying to get it to work on Dapper. Plugging it into the USB port starts it charging, and lsusb lists the device:

Bus 004 Device 004: ID 04e8:5081 Samsung Electronics Co., Ltd

but nothing shows up under /dev/.

There are a few threats about similar problems with the K3's big brother K5, which required upgrading the firmware for it to be detected. There's no chatter about the K3 version, though, and whether this woudl work. I don't even know if my firmware has any updates; It claims to be running 3.05 (under Settings/About), where as on the Samsung websites it has three listings: firmware (ver 1.09), firmware with upgrade manual (ver 3.05), and firmware with automatic upgrade program (ver 3.05). I have no idea why one is version 1.09 and another 3.05.

Does anybody know how I can get my K3 to work?

---

### Post by tgalati4 on 2007-06-23
It could show up in one of three places:

/media/PLAYA

/mnt/PLAYA

/home/username/Desktop/PLAYA

for a device with a volume named 'PLAYA'

How was the device formatted?  Perhaps you can reformat using the built-in menu and see if it shows up.

---

