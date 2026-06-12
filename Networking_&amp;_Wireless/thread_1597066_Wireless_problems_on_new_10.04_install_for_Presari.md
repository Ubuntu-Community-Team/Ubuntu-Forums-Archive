---
title: "Wireless problems on new 10.04 install for Presario 2100"
date: 2010-10-14
forum: Networking &amp; Wireless
---

### Post by dwcbrq on 2010-10-14
I talked my friend into solving his Windows problems, so I installed 10.04, and now his wireless doesn't work.

Here is output from lspci:

00:00.0 Host bridge: ATI Technologies Inc RS200/RS200M AGP Bridge [IGP 340M] (rev 02)
00:01.0 PCI bridge: ATI Technologies Inc PCI Bridge [IGP 340M]
00:02.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:06.0 Multimedia audio controller: ALi Corporation M5451 PCI AC-Link Controller Audio Device (rev 02)
00:07.0 ISA bridge: ALi Corporation M1533/M1535/M1543 PCI to ISA Bridge [Aladdin IV/V/V+]
00:08.0 Modem: ALi Corporation M5457 AC'97 Modem Controller
00:0a.0 CardBus bridge: O2 Micro, Inc. OZ601/6912/711E0 CardBus/SmartCardBus Controller
00:10.0 IDE interface: ALi Corporation M5229 IDE (rev c4)
00:11.0 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
00:12.0 Ethernet controller: National Semiconductor Corporation DP83815 (MacPhyter) Ethernet Controller
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon IGP 330M/340M/350M


He has a Belkin Basic Wireless USB Adapter, but I am not sure if he was using that.  If so, can Ubuntu work with that device?

---

### Post by dwcbrq on 2010-10-14
I found this and followed the steps for my Belkin USB device, but I may be missing a step, because I don't see my wireless device:

[http://ubuntuforums.org/showthread.php?t=1522815&highlight=Belkin+F7D1101](http://ubuntuforums.org/showthread.php?t=1522815&highlight=Belkin+F7D1101)

---

### Post by dwcbrq on 2010-10-14
Also, I have wicd installed.

---

### Post by dwcbrq on 2010-10-15
Got it to work.

Installed the net8192su.inf driver, then in wicd, set the wireless device to wlan0, then set preferences->general settings->WPA Supplicant Driver = ndiswrapper.

Then ran:

sudo ifconfig wlan0 up

---

### Post by dwcbrq on 2010-10-15
Not sure where to set this to "solved", so admin or mod, please do.

---

