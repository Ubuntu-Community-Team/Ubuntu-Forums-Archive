---
title: "PVR-150 Retail not tuning correctly after upgrade to 8.04"
date: 2008-05-11
forum: Mythbuntu
---

### Post by bblboy54 on 2008-05-11
This one is totally blowing my mind.  After upgrading my mythbuntu-backend to 8.04 LTS this week my one tuner card is not tuning correctly.  Basically the card just records static.  I have 2 cards in this system and both are PVR150's but one is the retail version (comes with remote and IR blaster) and the other is the MCE version (has stereo A/V in).  The retail card is the one that is doing this odd behavior.  On an initial boot up it will work perfectly.

*NOTE: I previously did an upgrade to 8.04 but was informed that 8.04 LTS was available so I upgrade to that.  The first upgrade was fine.*

So why am I asking this?  It's just a hardware issue!

Actually, no.  I figured this was the problem too but I had a PVR-150 retail in one of my front ends just for the purpose of using the remote so I replaced the one in the backend with that..... and it did the same thing.  The card also tunes just fine otherwise but its when the backend starts to record it apparently doesnt set the channel.  I am absolutely clueless on this.  Also, a side note.... the card that was in it first was one that I actually had Hauppauge upgrade the chip on.  The revision number after the upgrade is C399.  The card that I replaced it with is Rev C199.  Both are model 26032.

To add to this issue, tonight when I arrived home I found that my backend had seg faulted.....  this is something that I had never had happen before the upgrade.  I'm not sure if this is related to the card or not.

Here is some information.

Backend Configuration:
> 
Tyan S2882-D Mainboard
Dual AMD Opteron 244 CPUs
8GB (4x1GB per CPU) Corsair DDR333 RAM
3Ware 9500 Controller
8x 250GB SATA Hard drives (RAID 5)
1x Hauppauge PVR150 MCE
1x Hauppauge PVR150 Retail


End of dmesg:
> 
[  133.384214] ivtv0: Loaded v4l-cx2341x-enc.fw firmware (376836 bytes)
[  133.495424] ivtv0: Encoder revision: 0x02060039
[  138.160038] cx25840 2-0044: loaded v4l-cx25840.fw firmware (16382 bytes)
[  137.069708] ivtv1: Loaded v4l-cx2341x-enc.fw firmware (376836 bytes)
[  137.178819] ivtv1: Encoder revision: 0x02060039
[  142.483906] cx25840 3-0044: loaded v4l-cx25840.fw firmware (16382 bytes)
[  143.396963] ADDRCONF(NETDEV_UP): eth2: link is not ready
[  143.479945] ADDRCONF(NETDEV_UP): eth3: link is not ready
[  140.402435] NET: Registered protocol family 17
[  140.944447] mtrr: type mismatch for fd000000,800000 old: write-back new: write-combining
[  140.971200] mtrr: type mismatch for fd000000,800000 old: write-back new: write-combining
[  284.928267] Machine check events logged
[  451.350731] Machine check events logged
[42465.320754] mythbackend[5968]: segfault at 330036 rip 7fd1292eb4e0 rsp 4412b7b0 error 4


lspci
> 
bblboy54@mythbuntu-master:~$ lspci
00:06.0 PCI bridge: Advanced Micro Devices [AMD] AMD-8111 PCI (rev 07)
00:07.0 ISA bridge: Advanced Micro Devices [AMD] AMD-8111 LPC (rev 05)
00:07.1 IDE interface: Advanced Micro Devices [AMD] AMD-8111 IDE (rev 03)
00:07.2 SMBus: Advanced Micro Devices [AMD] AMD-8111 SMBus 2.0 (rev 02)
00:07.3 Bridge: Advanced Micro Devices [AMD] AMD-8111 ACPI (rev 05)
00:0a.0 PCI bridge: Advanced Micro Devices [AMD] AMD-8131 PCI-X Bridge (rev 12)
00:0a.1 PIC: Advanced Micro Devices [AMD] AMD-8131 PCI-X IOAPIC (rev 01)
00:0b.0 PCI bridge: Advanced Micro Devices [AMD] AMD-8131 PCI-X Bridge (rev 12)
00:0b.1 PIC: Advanced Micro Devices [AMD] AMD-8131 PCI-X IOAPIC (rev 01)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
00:19.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:19.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:19.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:19.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:03.0 RAID bus controller: 3ware Inc 9xxx-series SATA-RAID
02:03.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)
02:06.0 SCSI storage controller: Adaptec AIC-7902B U320 (rev 10)
02:06.1 SCSI storage controller: Adaptec AIC-7902B U320 (rev 10)
02:09.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5704 Gigabit Ethernet (rev 03)
02:09.1 Ethernet controller: Broadcom Corporation NetXtreme BCM5704 Gigabit Ethernet (rev 03)
03:00.0 USB Controller: Advanced Micro Devices [AMD] AMD-8111 USB (rev 0b)
03:00.1 USB Controller: Advanced Micro Devices [AMD] AMD-8111 USB (rev 0b)
03:04.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)
03:06.0 VGA compatible controller: ATI Technologies Inc Rage XL (rev 27)
03:08.0 Ethernet controller: Intel Corporation 82557/8/9/0/1 Ethernet Pro 100 (rev 10)


tail of mythbackend.log
> 
2008-05-10 20:11:28.355 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-05-10 20:12:11.220 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2008-05-10 20:12:11.224 UPnpMedia: BuildMediaMap Done. Found 0 objects
2008-05-10 20:26:28.745 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
QDom: saving invalid character &#x0;, the document will not be well-formed
QDom: saving invalid character &#x0;, the document will not be well-formed
QDom: saving invalid character &#x0;, the document will not be well-formed
2008-05-10 20:41:29.098 AutoExpire: CalcParams(): Max required Free Space: 1.0 GB w/freq: 15 min
2008-05-10 20:42:12.227 UPnpMedia: BuildMediaMap VIDEO scan starting in :/var/lib/mythtv/videos:
2008-05-10 20:42:12.228 UPnpMedia: BuildMediaMap Done. Found 0 objects



If anyone has ANY idea what might be causing this I would really appreciate the input.  :confused:

Thanks

---

### Post by bblboy54 on 2008-05-15
It seems that I may be having a lot more issues than just the tuning problems.  My mythtv-backend is segfaulting at least every other day.  Since the upgrade things have been extremely unreliable.  Has anyone else had the segfault problem or the tuner problem?  Does anyone have even an idea of what I might start looking for?

---

### Post by bblboy54 on 2008-05-16
Well, I found the problem with the tuning and its not hardware or software related.  Apparently Comcast killed most of the analog signals in my neighborhood ironically on the same day I did the upgrade.  Compounding the confusion the signals were killed mostly on the channels that had my highest priority shows.  Basically, it wasn't the tuner that was having the error but the channel and the confusion was because the higher priority shows recorded on one tuner and the lower priority on the other thus making it look like it was isolated to one tuner.

The instability of the system, however, still hasn't been answered.

---

### Post by agamotto on 2008-05-16
> **bblboy54 said:**
> Well, I found the problem with the tuning and its not hardware or software related.  Apparently Comcast killed most of the analog signals in my neighborhood ironically on the same day I did the upgrade.  Compounding the confusion the signals were killed mostly on the channels that had my highest priority shows.  Basically, it wasn't the tuner that was having the error but the channel and the confusion was because the higher priority shows recorded on one tuner and the lower priority on the other thus making it look like it was isolated to one tuner.

The instability of the system, however, still hasn't been answered.

If memory serves, the RC version of 8.04 wasn't supposed to be upgradable... they were suggesting a clean install with the final version.  I am wondering if there is some stray code from the rc that is screwing things up for you.

---

