---
title: "Nikon L330 not being recognized!"
date: 2016-02-21
forum: Multimedia Software
---

### Post by Ricardo_Dias on 2016-02-21
Hello mates, I'm new in the forum and this is my first thread. So, I'm going to skip the intros and go straight to my problem. 
I'm running Linux Mint on my desktop and I own a Nikon L330 Digital Cam, it's been working properly when mounting since I bought it, except one or two times, those times I used digiKam since it was not mounting, but via lsusb it was recognizable. But now, suddenly, I have the same problem, I turn on the cam and I plug it into one of the USB ports and it's being even detected. Below, the output:

> ricardo@ricardo ~ $ lsusb
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 003: ID 0461:4d0f Primax Electronics, Ltd HP Optical Mouse
Bus 004 Device 002: ID 045e:0750 Microsoft Corp. Wired Keyboard 600
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 0ac8:332d Z-Star Microelectronics Corp. Vega USB 2.0 Camera
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub




I also tried to use gphoto to see if it's being detected, but not. I ran udevadm monitor and plugged and unplugged the device, nothing changed. Tried to unplug another device, using the same ports, they work properly. I'd be very glad if you guys help me. Thanks a lot!

---

