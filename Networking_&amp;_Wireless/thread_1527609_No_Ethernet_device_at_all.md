---
title: "No Ethernet device at all?"
date: 2010-07-09
forum: Networking &amp; Wireless
---

### Post by Breath! on 2010-07-09
I just installed 10.04 on a Dell C800 and I've been trying to connect to the internet via Ethernet with no avail. I did some searching and ran lspci -nn and got this:

user@user-desktop:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation 82815 815 Chipset Host Bridge and Memory Controller Hub [8086:1130] (rev 02)
00:01.0 PCI bridge [0604]: Intel Corporation 82815 815 Chipset AGP Bridge [8086:1131] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 02)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801BAM ISA Bridge (LPC) [8086:244c] (rev 02)
00:1f.1 IDE interface [0101]: Intel Corporation 82801BAM IDE U100 Controller [8086:244a] (rev 02)
00:1f.2 USB Controller [0c03]: Intel Corporation 82801BA/BAM USB Controller #1 [8086:2442] (rev 02)
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Rage Mobility M4 AGP [1002:4d46]
02:03.0 Multimedia audio controller [0401]: ESS Technology ES1983S Maestro-3i PCI Audio Accelerator [125d:1998] (rev 10)
02:06.0 Communication controller [0780]: 3Com Corporation Mini PCI 56k Winmodem [10b7:1007]
02:0f.0 CardBus bridge [0607]: Texas Instruments PCI4451 PC card Cardbus Controller [104c:ac42]
02:0f.1 CardBus bridge [0607]: Texas Instruments PCI4451 PC card Cardbus Controller [104c:ac42]
02:0f.2 FireWire (IEEE 1394) [0c00]: Texas Instruments PCI4451 IEEE-1394 Controller [104c:8027]

There's no mention on Ethernet...
__________________________________________________________________________

I also ran ifconfig -a and got this:

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:172 errors:0 dropped:0 overruns:0 frame:0
          TX packets:172 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:13392 (13.3 KB)  TX bytes:13392 (13.3 KB)

 No mention here either...

__________________________________________________________________________

Any suggestions?

---

### Post by Iowan on 2010-07-09
Although it's much the same information, I like the results of **sudo lshw -C network** - as it limits output to information about networking interfaces. **ifconfig -a** isn't showing the interface at all, so it (they?) might not be recognized.

---

