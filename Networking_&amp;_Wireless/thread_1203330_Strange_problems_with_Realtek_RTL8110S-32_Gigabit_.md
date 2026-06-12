---
title: "Strange problems with Realtek RTL8110S-32 Gigabit Ethernet"
date: 2009-07-03
forum: Networking &amp; Wireless
---

### Post by j_a_n on 2009-07-03
I have very very  strange problems with my onboard network interface Realtek RTL8110S-32.

I read a lot of the problems with realtek chipsets but nothing seems to help me. 

My current state:
- I installed a new driver for the card from (Version 6.010.00 from the realtek homepage)
(i used the howto [http://ubuntuforums.org/showthread.php?t=1022411](http://ubuntuforums.org/showthread.php?t=1022411))
- module r8169 is loaded and "ethtool -i eth0" shows the driver r8169 and it's version "6.010.00-NAPI"
- ethtool eth0 and mii-tool said that the network link is up
- No ping (except to 127.0.0.1) works, I always get 100% paket lost
- ethtool -S eth0 shows a lot of "align_errors" (about one more each second)

The strangest things of all are the network led: Just after power-on the orange led is blinking very fast and the green light glows permanent and this status does not change after ubuntu has bootet. Even rmmod 8169 and modprobe r8169 does not influences the leds.

Until some days ago (before the last reboot) the network was working with the following "trick": If the leds were in the status described above, I unplugged the power cable for some hours and then everything works fine again until I needed a restart (then I had to unplug the cable again). But now unplugging the power cable does not help any more ... the led status remains the same.

---

### Post by j_a_n on 2009-07-03
After installing ubuntu server 9.04 on a new hdd I've a new strange situation: 

First, the problem seems to be the same. But after plugging the network and power cable in and out the leds seems to be normal (no fast blinking), but now lspci shows an "undefined" network interface:
[PHP]Ethernet Controller: device f000:8169 (rev 10)[/PHP]
and (of course) no eth0 is available.

---

### Post by j_a_n on 2009-07-04
By accident I found out, that the network device is working when setting the speed to 10Mbit. 100Mbit is still not working. Same result with a WinXP test installation.

Unfortunately I cannot test 1000Mbit in my network.

I think it's a hardware failure ...

---

