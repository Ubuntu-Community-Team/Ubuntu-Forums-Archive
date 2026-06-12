---
title: "Wireless drivers for National Semiconductor Corporation DP83815"
date: 2009-07-19
forum: Networking &amp; Wireless
---

### Post by sv2146 on 2009-07-19
Hello,

I just installed Ubuntu and don't get wireless reception. I do get it in windows. It might be that I don't have the drivers for Ubuntu. My card appears to be "National Semiconductor Corporation DP83815"

Could you please let me know where can I obtain the Ubuntu drivers so that I may have wireless?

sergio@ubuntu:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc AGP Bridge [IGP 320M] (rev 13)
00:01.0 PCI bridge: ATI Technologies Inc PCI Bridge [IGP 320M] (rev 01)
00:02.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:06.0 Multimedia audio controller: ALi Corporation M5451 PCI AC-Link Controller Audio Device (rev 02)
00:07.0 ISA bridge: ALi Corporation M1533/M1535/M1543 PCI to ISA Bridge [Aladdin IV/V/V+]
00:08.0 Modem: ALi Corporation M5457 AC'97 Modem Controller
00:09.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 02)
00:0a.0 CardBus bridge: O2 Micro, Inc. OZ601/6912/711E0 CardBus/SmartCardBus Controller
00:0c.0 FireWire (IEEE 1394): Texas Instruments TSB43AB21 IEEE-1394a-2000 Controller (PHY/Link)
00:10.0 IDE interface: ALi Corporation M5229 IDE (rev c4)
00:11.0 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
00:12.0 Ethernet controller: National Semiconductor Corporation DP83815 (MacPhyter) Ethernet Controller
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility U1
sergio@ubuntu:~$

---

### Post by cariboo on 2009-07-19
What is the output of:

```
sudo lshw -C network
```

There is a driver for that nic, as I have the same chipset in my laptop, and it worked out of the box.

---

