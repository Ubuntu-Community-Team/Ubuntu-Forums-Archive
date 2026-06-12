---
title: "No Sound"
date: 2010-08-12
forum: Multimedia Software
---

### Post by iKiddo on 2010-08-12
ikiddo@Shiela:~$ lspci
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
00:0a.2 RAM memory: nVidia Corporation MCP51 Memory Controller 0 (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:0f.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
03:00.0 VGA compatible controller: nVidia Corporation G86 [GeForce 8500 GT] (rev a1)
04:07.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)


Under the hardware drivers I am not getting anything for sound drivers at all.

Any help is appreciated but I will state that I cam complete and total Ubuntu / Linux noob. :D

[B]EDIT

[/B]Sound IS coming out of headphones .. but not speakers.
SigmaTel STAC9227
Is sound card to be exact.

---

### Post by iKiddo on 2010-08-12
Anyone that can help please? :(

---

### Post by Unknown-Demon on 2010-08-12
[iKiddo]("http://ubuntuforums.org/member.php?u=1129045"),
  What version of Ubuntu are you using?

---

### Post by Yellow Pasque on 2010-08-12
If you have sound in the headphone jack, then you probably just need to unmute or turn up some volume control.
```
alsamixer
```

---

### Post by iKiddo on 2010-08-13
> **Temüjin said:**
> If you have sound in the headphone jack, then you probably just need to unmute or turn up some volume control.
```
alsamixer
```


[IMG]http://i37.tinypic.com/ms0fhd.png[/IMG]

---

### Post by iKiddo on 2010-08-13
**SOLVED**

Cable wasn't in properly. :$

---

