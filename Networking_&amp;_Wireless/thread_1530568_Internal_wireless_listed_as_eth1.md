---
title: "Internal wireless listed as eth1"
date: 2010-07-13
forum: Networking &amp; Wireless
---

### Post by baguahsing on 2010-07-13
I have an older laptop, a Toshiba Satellite Pro 6100 that has a switchable internal wireless connection.  It will not connect to my router.  I am using the 10,04 netbook remix.  When I use lshw in terminal this is what I get:
 
*-network
description: Wireless interface
physical id:  1
logical name:  eth1
serial:  00:02:2d:80:5a:15
capabilities: ethernet physical wireless
configuration:  broadcast=yes driver=orinoco driverversion=0.15 firmware=Lucent/Agere 9.48 multicast=yes wireless=IEEE 802.11b
 
ifconfig:
eth1   Link encap:Ethernet  HWaddr 00:02:2d:80:5a:15
         UP BROADCAST MULTICAST MTU:1500  Metric:1
         RX packets:0 errors:0 dropped:0 overruns:0 frame:0
         TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
         collisions:0 txqueuelen:1000
         RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
         Interrupt:11 Base address:0xd100
 
Any suggestions on how to make this work?  Should it not be identified as wlan0?  I'm a 2 week old newbie so I need specific guidance.  Please don't assume I know a whole lot about Ubuntu linux because I don't.  I did a clean install over XP and am using this laptop as a learning tool for linux in hopes to divorce windows completely.

---

### Post by kerry_s on 2010-07-13
is your router setup to work with wireless b ? since it seems you have a b only card. (for example: my router is only set to "g" so "b" connections will fail)

does the network manager show any connections? so you know it's working.

it's not uncommon for it to have a name other then wlan0, it depends on the machine & card setup, yours just happens to be like a normal ethernet device.

---

### Post by baguahsing on 2010-07-13
My router is setup for b/g and some networks do show up but mine is not broadcast, it is hidden.

---

### Post by baguahsing on 2010-07-13
iwconfig eth1 results:
 
IEEE 802.11b  ESSID: ""
Mode:Managed  Frequency:2.457 GHz  Access Point: None
Bit Rate:11 Mb/s  Sensitivity:1/0
Retry limit:8  RTS thr:off  Fragment thr:off
Link Quality=0/70  Signal level=-122 dBm  Noise level=-122 dBm
Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
Tx excessive retries:0  Invalid misc:0  Missed beacon:0
 
Note - I am not at home next to my router.

---

### Post by kerry_s on 2010-07-13
so when you click on "connect to hidden wireless" & put in your network name it does nothing?

---

### Post by baguahsing on 2010-07-13
It will attempt to connect for about 30 seconds then the login screen will pop up again asking for the network name and password.

---

### Post by kerry_s on 2010-07-13
> **baguahsing said:**
> It will attempt to connect for about 30 seconds then the login screen will pop up again asking for the network name and password.

are you sure your putting the password right? :lolflag:

try disabling the password in your router, but leave it hidden, see if you can connect to just hidden.

---

### Post by baguahsing on 2010-07-13
The password is correct.

---

