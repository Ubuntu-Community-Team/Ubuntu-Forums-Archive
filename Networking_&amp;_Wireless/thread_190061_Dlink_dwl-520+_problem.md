---
title: "Dlink dwl-520+ problem"
date: 2006-06-05
forum: Networking &amp; Wireless
---

### Post by gerst on 2006-06-05
Hi,

I hope someone can help me out... I can read these strange stuff in my log files for my d-link dwl 520+ card. What could be the problem?  Here is a log:
"Jun  6 02:06:08 localhost kernel: [4296417.184000] wlan0: less than 5 minutes since last radio recalibration, not recalibrating (maybe card is too hot?)
Jun  6 02:06:08 localhost kernel: [4296417.999000] wlan0: tx error 0x20, buf 04!
Jun  6 02:06:19 localhost kernel: [4296429.043000] wlan0: rx: 12 DUPs in 30 packets received in 10 secs
Jun  6 02:06:23 localhost kernel: [4296432.826000] wlan0: tx error 0x20, buf 12!
Jun  6 02:06:24 localhost kernel: [4296433.639000] wlan0: tx error 0x20, buf 03!
Jun  6 02:06:24 localhost kernel: [4296433.639000] wlan0: less than 5 minutes since last radio recalibration, not recalibrating (maybe card is too hot?)
Jun  6 02:06:25 localhost kernel: [4296434.380000] wlan0: tx error 0x20, buf 07!
Jun  6 02:06:25 localhost kernel: [4296434.380000] wlan0: tx error 0x20, buf 09!
Jun  6 02:06:27 localhost kernel: [4296436.612000] wlan0: tx error 0x20, buf 05!
Jun  6 02:06:30 localhost kernel: [4296439.175000] wlan0: rx: 42 DUPs in 92 packets received in 10 secs
Jun  6 02:06:33 localhost kernel: [4296442.919000] wlan0: tx error 0x20, buf 04!
Jun  6 02:06:33 localhost kernel: [4296442.919000] wlan0: less than 5 minutes since last radio recalibration, not recalibrating (maybe card is too hot?)
Jun  6 02:06:33 localhost kernel: [4296442.919000] disabling above message
Jun  6 02:06:33 localhost kernel: [4296442.995000] wlan0: tx error 0x20, buf 06!
Jun  6 02:06:34 localhost kernel: [4296443.521000] wlan0: tx error 0x20, buf 12!
Jun  6 02:06:34 localhost kernel: [4296443.852000] wlan0: tx error 0x20, buf 15!
Jun  6 02:06:37 localhost kernel: [4296446.775000] wlan0: tx error 0x20, buf 05!
Jun  6 02:06:37 localhost kernel: [4296446.775000] wlan0: tx error 0x20, buf 06!
Jun  6 02:06:39 localhost kernel: [4296449.126000] wlan0: tx error 0x20, buf 02!
Jun  6 02:06:40 localhost kernel: [4296449.419000] wlan0: rx: 56 DUPs in 160 packets received in 10 secs
"
Please help... Thanks

---

### Post by DrRobotnik on 2007-06-18
I too am having the same problems except its a Dlink GWL G650+ wireless card and the card doesnt feel hot at all

---

### Post by ramadhian on 2007-07-21
My DWL-520+ PCI Card finally work fine with ndiswrapper (AIRPLUS.INF Windows Driver)

What I did is just to copy the windows driver (Driver shipped with CD) to my linux drive.
and do the following :

*) cd ~path-to-driver-location/
*) sudo ndiswrapper -i **AIRPLUS.INF**
*) add **ndiswrapper** kernel module at the end of** /etc/module**s file

** dmesg | grep ndis**

[   58.866325] ndiswrapper version 1.38 loaded (preempt=no,smp=yes)
[   59.086813] ndiswrapper: driver airplus (D-Link,09/08/2003,4.15.5.1) loaded
[   59.087864] ndiswrapper: using IRQ 20
[   60.316645] ndiswrapper (set_encr_mode:694): setting encryption mode to 6 failed (C00000BB)
[   63.038027] usbcore: registered new interface driver ndiswrapper

and then all work perfect except the Signal Strength (signal max.60%)
Internet Work fine but I still confuse why I can not ping my Access Point IP Address 
and I can not browse my Access Point trough Web based setup

---

