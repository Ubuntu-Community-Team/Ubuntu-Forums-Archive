---
title: "Belkin USB Wireless F5D8053"
date: 2009-07-27
forum: Networking &amp; Wireless
---

### Post by Buzzbait on 2009-07-27
Hi all. I could really use some help. I'm no Ubuntu genius or anything, and this one has me stumped. I picked up a Belkin USB F5D8053 wireless today. It runs off of the RT2870 chipset, which from what I've read, should work well on Jaunty. I plug it in, and I get nothing. I tried ndiswrapper, with the supplied windows driver, and it won't connect. It finds the usb wireless, but just can't manage to connect to the WPA2 network. 

So I ditched the ndiswrapper association, and did some forum reading, and found a thread on the Linux wireless RT2870 driver, supplied by RALINK. I got it all setup, did the 'make' and 'make install', and everything went fine. I then tried to 'modprobe rt2870sta' and...... nothing. It's as if Linux doesn't know what to do with the hardware. Running ifconfig, iwconfig and lshw shows no trace of the hardware whatsoever. The only way I even know that the hardware is there is by running lsusb, from which I get:

> Bus 001 Device 003: ID 050d:805e Belkin Components 
Bus 001 Device 002: ID 0d49:7350 Maxtor 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 002: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

The Belkin at 001:003 is obviously the wireless.

But how to I go about associating 001:003 with the Linux rt2870sta driver.

---

### Post by khelben1979 on 2009-07-27
[Check this out]("http://tonybierman.com/blog/2009/05/09/belkin-n-wireless-usb-f5d8053-ralink-rt2870-chipset-on-ubuntu-jaunty-linux/") from tonybierman.com

Don't know if it works myself.

---

