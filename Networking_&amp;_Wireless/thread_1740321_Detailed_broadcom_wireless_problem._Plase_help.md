---
title: "Detailed broadcom wireless problem. Plase help"
date: 2011-04-26
forum: Networking &amp; Wireless
---

### Post by slixz85 on 2011-04-26
hi, i am using a hp pavillion entertainment dv2 1030us and am having an issue getting the wifi to work on it. i have installed the sta driver for bcm4322 and it will installed and activated succesfully and say it is working, however no interface will detect. i can enable and disable the wifi icon but no networks ever show up. i have blacklisted a few things as the ubuntu and broadcom websites have showed but no luck. i have used ndiswrapper and installed the .inf and .sys files and it said it was working as well, but no interface was ever detected.

i have blacklisted b43,ssb,wl

the ethernet connection works fine i have been using it. also i don't know if it matters since the ethernet connection works fine but this ubuntu is installed to usb (laptop hard drive failed and i took it out), just mentioning this because i don't know if it matter or not as in device locations and all that.

lsmod | grep "b43\|ssb\|wl"
wl 1959565 0 
lib80211 5058 2 lib80211_crypt_tkip,wl

lsusb
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 0bda:0158 Realtek Semiconductor Corp. Mass Storage Device
Bus 001 Device 003: ID 0c45:62c0 Microdia Sonix USB 2.0 Camera
Bus 001 Device 002: ID 0781:5530 SanDisk Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub



lo no wireless extensions.

eth0 no wireless extensions.

eth1 IEEE 802.11 Access Point: Not-Associated 
Link Quality:5 Signal level:0 Noise level:0
Rx invalid nwid:0 invalid crypt:0 invalid misc:0



eth0 Link encap:Ethernet HWaddr 00:21:cc:3a:30:55 
inet addr:192.168.1.121 Bcast:192.168.1.255 Mask:255.255.255.0
inet6 addr: fe80::221:ccff:fe3a:3055/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:1703 errors:0 dropped:0 overruns:0 frame:0
TX packets:1570 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000 
RX bytes:1531676 (1.5 MB) TX bytes:303632 (303.6 KB)
Interrupt:43 Base address:0x4000 

eth1 Link encap:Ethernet HWaddr 00:25:56:39:81:27 
inet6 addr: fe80::225:56ff:fe39:8127/64 Scope:Link
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000 
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
Interrupt:18 

lo Link encap:Local Loopback 
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:272 errors:0 dropped:0 overruns:0 frame:0
TX packets:272 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0 
RX bytes:20136 (20.1 KB) TX bytes:20136 (20.1 KB)

thanks to any help, im a little new to linux so bear with me

---

### Post by BertN45 on 2011-04-26
The STA driver as supplied by Ubuntu often (always?) does not work. It did not work on the bcm4312 I am using, but I could use the b43 driver. There are more people having problems with the bcm4322. I only saw two possible solutions:

- load the source of the driver from the Broadcom site and follow their instructions to generate the driver.
- use the ndsiswrapper and the windows XP driver.

---

### Post by slixz85 on 2011-04-26
ok unfortunately i just noticed i installed the 32bit os onto this amd ahtlon 64bit, does this matter with the wifi working? the ethernet and everything else recognizes.

---

