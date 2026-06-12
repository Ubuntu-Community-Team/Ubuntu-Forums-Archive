---
title: "Averatec Laptop, wireless driver problems"
date: 2010-01-10
forum: Networking &amp; Wireless
---

### Post by Don1500 on 2010-01-10
I have an Averatec Laptop (3280 series). I just updated to 9.10 and can't find my wireless driver. I had it up and running in 9.04 so I know it will work.
Here is the output from lspci
```
00:00.0 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. K8M800 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI bridge [K8T800/K8T890 South]
00:09.0 Network controller: RaLink RT2500 802.11g Cardbus/mini-PCI (rev 01)
00:0a.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: VIA Technologies, Inc. K8M800/K8N800/K8N800A [S3 UniChrome Pro] (rev 01)
```

I know it's something stupid I'm missing but any help would be appreciated. (It works in Windows XP)

---

### Post by bkratz on 2010-01-10
There is probably something useful in this thread. If not just do a search above for the RT2500.

[http://ubuntuforums.org/showthread.php?t=1211513&highlight=RT2500](http://ubuntuforums.org/showthread.php?t=1211513&highlight=RT2500)

---

### Post by Don1500 on 2010-01-10
> **bkratz said:**
> There is probably something useful in this thread. If not just do a search above for the RT2500.

[http://ubuntuforums.org/showthread.php?t=1211513&highlight=RT2500](http://ubuntuforums.org/showthread.php?t=1211513&highlight=RT2500)

Thanks, That got me started in the right direction, connection established, this thread is solved.

---

