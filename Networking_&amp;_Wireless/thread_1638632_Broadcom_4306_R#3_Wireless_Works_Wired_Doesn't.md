---
title: "Broadcom 4306 R#3_Wireless Works_Wired Doesn't"
date: 2010-12-05
forum: Networking &amp; Wireless
---

### Post by homeuser1 on 2010-12-05
After much work over the last 36 hours, my wireless network is now working but not the ethernet connection on my Dell latitude D600 which uses a Broadcom 4306 card.  Any ideas on why this would be?  

~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation 82855PM Processor to I/O Controller [8086:3340] (rev 03)
00:01.0 PCI bridge [0604]: Intel Corporation 82855PM Processor to AGP Controller [8086:3341] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 [8086:24c2] (rev 01)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 [8086:24c4] (rev 01)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 [8086:24c7] (rev 01)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller [8086:24cd] (rev 01)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 81)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge [8086:24cc] (rev 01)
00:1f.1 IDE interface [0101]: Intel Corporation 82801DBM (ICH4-M) IDE Controller [8086:24ca] (rev 01)
00:1f.5 Multimedia audio controller [0401]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller [8086:24c5] (rev 01)
00:1f.6 Modem [0703]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller [8086:24c6] (rev 01)
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Radeon RV250 [Mobility FireGL 9000] [1002:4c66] (rev 02)
02:01.0 CardBus bridge [0607]: O2 Micro, Inc. OZ711EC1 SmartCardBus Controller [1217:7113] (rev 20)
02:01.1 CardBus bridge [0607]: O2 Micro, Inc. OZ711EC1 SmartCardBus Controller [1217:7113] (rev 20)
02:03.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 03)

---

### Post by bkratz on 2010-12-06
> **homeuser1 said:**
> After much work over the last 36 hours, my wireless network is now working but not the ethernet connection on my Dell latitude D600 which uses a Broadcom 4306 card.  Any ideas on why this would be?  

~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation 82855PM Processor to I/O Controller [8086:3340] (rev 03)
00:01.0 PCI bridge [0604]: Intel Corporation 82855PM Processor to AGP Controller [8086:3341] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 [8086:24c2] (rev 01)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 [8086:24c4] (rev 01)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 [8086:24c7] (rev 01)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller [8086:24cd] (rev 01)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 81)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge [8086:24cc] (rev 01)
00:1f.1 IDE interface [0101]: Intel Corporation 82801DBM (ICH4-M) IDE Controller [8086:24ca] (rev 01)
00:1f.5 Multimedia audio controller [0401]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller [8086:24c5] (rev 01)
00:1f.6 Modem [0703]: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller [8086:24c6] (rev 01)
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Radeon RV250 [Mobility FireGL 9000] [1002:4c66] (rev 02)
02:01.0 CardBus bridge [0607]: O2 Micro, Inc. OZ711EC1 SmartCardBus Controller [1217:7113] (rev 20)
02:01.1 CardBus bridge [0607]: O2 Micro, Inc. OZ711EC1 SmartCardBus Controller [1217:7113] (rev 20)
02:03.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 03)

I see from your other postings that you are probably waiting for Dr Chili to arrive, but for now your ethernet card is not even showing up in the listing above.  It really should show something like this thread

[http://ubuntuforums.org/showthread.php?t=1583550](http://ubuntuforums.org/showthread.php?t=1583550)

Could the card have come loose by vibration (dropping) or actually failing. If anybody can solve the problem Chili555 can!

---

### Post by chili555 on 2010-12-06
Hey, you're doing perfectly well.> your ethernet card is not even showing up in the listing above. It really should show something like this thread
My thoughts exactly. I'd also like homeuser1 to verify that it's enabled in the BIOS.

---

### Post by homeuser1 on 2010-12-07
Sorry for the slow reply back.  Anyway, I checked the bios and can't see where anything is turned off. I still don't have the ethernet connection.  For a few hours early in this troubleshooting process, all I had was the ethernet connection until everything was gone.  Eventually, Chili was able to bring the wireless network back from the dead.  
One thing to add since then, yesterday when I turned my laptop on after being off all night my internet connection was gone.  Also, the broadcom driver wasn't showing up in the additional drivers list.  I restarted the laptop and the wireless connection came back to life.  Today, I didn't have any problems.  Upon startup, the wireless connection connected right way and I was off doing my business.  
So, I'm back to trying to get the ethernet connection to work.  It's not a big deal though.  As long as the wireless connection is working, which I prefer, I'm in good shape. Any ideas on what's going on?

---

### Post by bkratz on 2010-12-07
> **homeuser1 said:**
> Sorry for the slow reply back.  Anyway, I checked the bios and can't see where anything is turned off. I still don't have the ethernet connection.  For a few hours early in this troubleshooting process, all I had was the ethernet connection until everything was gone.  Eventually, Chili was able to bring the wireless network back from the dead.  
One thing to add since then, yesterday when I turned my laptop on after being off all night my internet connection was gone.  Also, the broadcom driver wasn't showing up in the additional drivers list.  I restarted the laptop and the wireless connection came back to life.  Today, I didn't have any problems.  Upon startup, the wireless connection connected right way and I was off doing my business.  
So, I'm back to trying to get the ethernet connection to work.  It's not a big deal though.  As long as the wireless connection is working, which I prefer, I'm in good shape. Any ideas on what's going on?

When the ethernet is working, does it show up in the command you tried earlier

lspci -nn

If so, it really could be just an intermittent connection (made after heating up a bit) or a card that is failing, but wait for Mr. Terminals response.

---

### Post by chili555 on 2010-12-07
I think bkratz is right on track. If it doesn't even appear in lspci -nn, I'm not sure we have any way to fix what we can't see. Does it appear in:```
sudo lshw -C network
```I think there is a real possibility it's defective.

---

### Post by homeuser1 on 2010-12-07
I think in post 37 of the thread below, Chili brought the ethernet connection back to life.  However, after closing the laptop for a few hours the ethernet was lost and has been gone ever since.  

[http://ubuntuforums.org/showthread.php?t=1637238&page=4](http://ubuntuforums.org/showthread.php?t=1637238&page=4)

Anyway, here's the output requested.

dell@dell-Latitude-D600:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:02:03.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=32
       resources: irq:5 memory:faffe000-faffffff
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:0b:7d:0f:0d:5f
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=2.6.35-23-generic firmware=N/A ip=xxx.xxx.x.xxx multicast=yes wireless=IEEE 802.11bg

---

### Post by bkratz on 2010-12-07
> **homeuser1 said:**
> I think in post 37 of the thread below, Chili brought the ethernet connection back to life.  However, after closing the laptop for a few hours the ethernet was lost and has been gone ever since.  

[http://ubuntuforums.org/showthread.php?t=1637238&page=4](http://ubuntuforums.org/showthread.php?t=1637238&page=4)

Anyway, here's the output requested.

dell@dell-Latitude-D600:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:02:03.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=32
       resources: irq:5 memory:faffe000-faffffff
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:0b:7d:0f:0d:5f
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=2.6.35-23-generic firmware=N/A ip=xxx.xxx.x.xxx multicast=yes wireless=IEEE 802.11bg

Looking back at the two pages prior to that particular posting Dr Chili was trying to get the b43 driver to work on your system.  That would not have affected the wired connection (different drivers). It really looks like that was just a chance happening.

---

