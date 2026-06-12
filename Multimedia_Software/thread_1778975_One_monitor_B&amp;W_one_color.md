---
title: "One monitor B&amp;W one color"
date: 2011-06-09
forum: Multimedia Software
---

### Post by rjcataniajr on 2011-06-09
Kind of new to this Linux OS thing so please bear with me. I have installed 11.04 on same PC that has Vista. (different hard drives)
When I turn on my other monitor (Samsung TV) it only shows black and white. Works fine on Vista. I have tried all sorts of combo's setting up the second monitor but not successful.
Any help appreciated
roscoe

(let me know what additional info you will need)

---

### Post by rjcataniajr on 2011-06-15
[FONT="Comic Sans MS"][SIZE="4"]**"Hello"?**[/SIZE][/FONT]

---

### Post by underdog512 on 2011-06-15
Open a terminal and type...

```
lspci
```

Post the output.

---

### Post by rjcataniajr on 2011-06-20
russell@russell-D5468AT-ABA-ALONPAV:~$ lspci
00:00.0 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a1)
00:01.0 ISA bridge: nVidia Corporation MCP61 LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP61 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP61 Memory Controller (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:02.1 USB Controller: nVidia Corporation MCP61 USB Controller (rev a3)
00:04.0 PCI bridge: nVidia Corporation MCP61 PCI bridge (rev a1)
00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP61 IDE (rev a2)
00:07.0 Bridge: nVidia Corporation MCP61 Ethernet (rev a2)
00:08.0 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:08.1 IDE interface: nVidia Corporation MCP61 SATA Controller (rev a2)
00:09.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP61 PCI Express bridge (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 10h Processor Link Control
01:06.0 Communication controller: Conexant Systems, Inc. HSF 56k Data/Fax Modem
01:09.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev 80)
02:00.0 VGA compatible controller: ATI Technologies Inc RV610 video device [Radeon HD 2400 PRO]
02:00.1 Audio device: ATI Technologies Inc RV610 audio device [Radeon HD 2400 PRO]

---

### Post by rjcataniajr on 2011-07-07
**.....anybody?**

---

