---
title: "Intel 3945abg can't get working"
date: 2009-08-22
forum: Networking &amp; Wireless
---

### Post by uniqa on 2009-08-22
Hi there! 
Please help me, i'm already near to give up. 
My laptop is amilo Xa 1526 with Intel 3945abg wireless. Kutnubu 9.04 2.6.28-15-generic
I can't get it working =/ I read a lot of threads here, but no solution workin for me.
Here is my lspci output:
```

00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:04.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.3 Co-processor: nVidia Corporation MCP51 PMU (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev f1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev f1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
05:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce Go 7600] (rev a1)
07:06.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306 Fire II IEEE 1394 OHCI Link Layer Controller (rev c0)


```as you can see it's not even listed here =(

iwl3945 module is enabled. here is dmesg:
```

root@spider:/home/uniq# dmesg | grep iwl
[   17.108015] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.26ks
[   17.108015] iwl3945: Copyright(c) 2003-2009 Intel Corporation

```I tried to use ndiswrapper, but it, ofcourse, says "hardware present: no" and doesn't work.

iwconfig doesn't show me wlan0 interface, only lo,eth0,pan0 - no wireless extensions.



On the same card there is Bluetoth adapter and it works fine. Under winXP & Vista wifi works fine. 

Please help me, i'm far away from home and i really, really, REALLY  need to get wifi working. any info you need i'll post, thank you!!

---

### Post by uniqa on 2009-08-22
I really need help, please...

---

### Post by uniqa on 2009-08-23
up, i really need help, please!

---

