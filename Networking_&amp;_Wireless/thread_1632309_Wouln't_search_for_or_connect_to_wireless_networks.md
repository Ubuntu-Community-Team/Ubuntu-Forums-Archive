---
title: "Wouln't search for or connect to wireless networks!"
date: 2010-11-27
forum: Networking &amp; Wireless
---

### Post by supergeek67 on 2010-11-27
I'm new to Ubuntu but have used other Linux types for short times and have been trying to connect to a wireless network and cant get farther than the network settings window.   I can do just about anything with WIN XP  but decided Ubuntu was 100x better and more stable.   I can't get Ubuntu to search for Wireless networks or connect to one i typed in manually.   I hate saying this but, I need help. :x
For any one who wants to know:  I am using a...
HP Probook 6555b (laptop)
2Gb RAM
160Gb HDD
a/g/n wireless + BT
XP PRO running side by side with UBUNTU desktop 10.04 LTS
2.09Gh AMD II P320
32-Bit system
and FYI: I know "geek-speak"  so no need to dumb-down or explain basic stuff.

---

### Post by Jlayman on 2010-11-27
show results of```
ifconfig

```

---

### Post by supergeek67 on 2010-11-28
> **Jlayman said:**
> show results of```
ifconfig

```

$ ifconfig
eth0      Link encap:Ethernet  HWaddr 1c:c1:de:93:65:24  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:24 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1696 (1.6 KB)  TX bytes:1696 (1.6 KB)

$

---

### Post by uncaspi on 2010-11-29
let's see sudo lspci -nn

---

### Post by supergeek67 on 2010-12-01
> **uncaspi said:**
> let's see sudo lspci -nn

i got:

$
00:00.0 Host bridge [0600]: Advanced Micro Devices [AMD] RS780 Host Bridge Alternate [1022:9601]
00:01.0 PCI bridge [0604]: Hewlett-Packard Company Device [103c:9602]
00:04.0 PCI bridge [0604]: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 0) [1022:9604]
00:05.0 PCI bridge [0604]: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1) [1022:9605]
00:07.0 PCI bridge [0604]: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 3) [1022:9607]
00:09.0 PCI bridge [0604]: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 4) [1022:9608]
00:11.0 SATA controller [0106]: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode] [1002:4391]
00:12.0 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller [1002:4397]
00:12.2 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB EHCI Controller [1002:4396]
00:13.0 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller [1002:4397]
00:13.2 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB EHCI Controller [1002:4396]
00:14.0 SMBus [0c05]: ATI Technologies Inc SBx00 SMBus Controller [1002:4385] (rev 41)
00:14.2 Audio device [0403]: ATI Technologies Inc SBx00 Azalia (Intel HDA) [1002:4383] (rev 40)
00:14.3 ISA bridge [0601]: ATI Technologies Inc SB700/SB800 LPC host controller [1002:439d] (rev 40)
00:14.4 PCI bridge [0604]: ATI Technologies Inc SBx00 PCI to PCI Bridge [1002:4384] (rev 40)
00:14.5 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller [1002:4399]
00:16.0 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller [1002:4397]
00:16.2 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB EHCI Controller [1002:4396]
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] HyperTransport Configuration [1022:1200]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Address Map [1022:1201]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] DRAM Controller [1022:1202]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Miscellaneous Control [1022:1203]
00:18.4 Host bridge [0600]: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Link Control [1022:1204]
01:05.0 VGA compatible controller [0300]: ATI Technologies Inc M880G [Mobility Radeon HD 4200] [1002:9712]
01:05.1 Audio device [0403]: ATI Technologies Inc RS880 Audio Device [Radeon HD 4200] [1002:970f]
02:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. Device [11ab:4381] (rev 11)
03:00.0 SD Host controller [0805]: Ricoh Co Ltd Device [1180:e822] (rev 01)
03:00.1 System peripheral [0880]: Ricoh Co Ltd Device [1180:e230] (rev 01)
03:00.2 System peripheral [0880]: Ricoh Co Ltd Device [1180:e852] (rev 01)
03:00.3 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd Device [1180:e832] (rev 01)
07:00.0 Network controller [0280]: Broadcom Corporation Device [14e4:4727] (rev 01)
~$ 

hope i can get this working

---

### Post by Davste on 2010-12-01
> 07:00.0 Network controller [0280]: Broadcom Corporation Device [14e4:4727] (rev 01)

Broadcom wireless card? Troublesome... 

Check this thread out:
[http://ubuntuforums.org/showthread.php?t=760568](http://ubuntuforums.org/showthread.php?t=760568)

Cheers

---

### Post by TBABill on 2010-12-01
Since it's Broadcom, can you plug into an ethernet port? If you can, then just click settings>>administration>>hardware (or additional drivers if 10.10) and follow the prompts. You need to know which Broadcom device you have and normally you can get that by looking at the output of ```
lspci
``` but it looks like when you did it you got no return of the exact chipset. For example, mine is a Broadcom BCM4312, but there are quite a few others. Some require the B43 driver and others require the STA driver. It's important to know which you need.
 
So if you are able maybe that's a way to get it going. You can activate the one you need and then restart the computer to begin using.
 
You could have additional quirks to deal with if you are on 10.10 because it is just aggravating to get going initially with Broadcom devices for some reason, while in 10.04 it's a breeze. Post back if you get part way through and need further help.

---

### Post by supergeek67 on 2010-12-01
> **TBABill said:**
> Since it's Broadcom, can you plug into an ethernet port? If you can, then just click settings>>administration>>hardware (or additional drivers if 10.10) and follow the prompts. You need to know which Broadcom device you have and normally you can get that by looking at the output of ```
lspci
``` but it looks like when you did it you got no return of the exact chipset. For example, mine is a Broadcom BCM4312, but there are quite a few others. Some require the B43 driver and others require the STA driver. It's important to know which you need.
 
So if you are able maybe that's a way to get it going. You can activate the one you need and then restart the computer to begin using.
 
You could have additional quirks to deal with if you are on 10.10 because it is just aggravating to get going initially with Broadcom devices for some reason, while in 10.04 it's a breeze. Post back if you get part way through and need further help.

it's internal. Plus it's a laptop and a hate pulling them apart.  if it were a tower i'd open it up, not with laptops.

---

