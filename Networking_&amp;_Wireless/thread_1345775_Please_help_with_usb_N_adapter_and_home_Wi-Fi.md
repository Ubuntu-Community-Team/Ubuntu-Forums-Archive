---
title: "Please help with usb N adapter and home Wi-Fi"
date: 2009-12-04
forum: Networking &amp; Wireless
---

### Post by darkod on 2009-12-04
Hi all. I hope someone can help or at least point me at the right direction because I have been googling for almost a week with no solution.
My desktop is connected to the internet by a network cable, on eth0. I bought usb N adapter, Tenda W311U, and hope to share the internet with my netbook (built in G reported as ath5k driver).

Two problems:
1. The usb N seems not to be working correctly.
2. How to create basic soft AP to transmit, not ad-hoc if possible.

For 1. I can't be sure the usb N adapter is working fine because I want it to transmit and not receive (no other networks around anyway to check). After plugging it in the driver reported as used was rt2800usb. But I got suspicious that it's working fine and started googling around, it seems my chip is RT2870. I blacklisted rt2800usb and that was small progress. Now it allows me to create new wireless network but with that option it works only as ad-hoc and the signal seems almost dead. After the blacklisting it seems to be working with rt2870sta.
But... Doing sudo lsusb is giving something like 148e:3070 Ralink blabla. Does the 3070 means it's RT3070 chip because that exists too? Should I blacklist rt2870sta too so I can see if Ubuntu will use another driver? Also from Ralink website I downloaded the RT3070 driver for linux, ver 2.1 I think. Should I compile? I found some tutorials for RT2870 but it would be the same.
And after compiling how can I be sure with which driver it's working?

For 2. Once the adapter is working with correct driver (hopefully soon), is there any basic was to make soft AP running? The chip has the option but it seems there is no package in Ubuntu to make this happen. I don't mind entering commands in /etc/network/interfaces if that can create it, but I know too little to create it myself. I'm not trying to connect to an AP, I'm trying to create one.

Any help is appreciated, I'm already getting lost. :(

---

### Post by XxDARKXx on 2010-01-07
i am like i want help

---

### Post by Timbot2000 on 2010-01-07
I have pretty much the same problem. Hope somebody helps both of us.

---

