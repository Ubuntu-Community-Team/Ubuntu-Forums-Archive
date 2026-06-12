---
title: "TV Card does what?"
date: 2010-01-02
forum: Multimedia Software
---

### Post by Stray Wolf on 2010-01-02
The short of it is I have a PCI Express x1 TV tuner card in my HP Pavilion Media Center PC.  Specs: [http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01312600&lc=en&dlc=en&cc=us&#9001;=en&product=3644705]("http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01312600&lc=en&dlc=en&cc=us&lang=en&product=3644705")

Is there any way to utilize it?

---

### Post by HappyFeet on 2010-01-02
Post the output of
```
lspci
```

---

### Post by Stray Wolf on 2010-01-02
> **HappyFeet said:**
> Post the output of
```
lspci
```

Oh crap!  Post what to where?  In the terminal?  sudo apt-get lspci...or something.  I'm almost hopelessly ignorant at this though I've managed to get my Hulu Desktop working and XBMC.  The Guide walked me through the terminal commands to install restricted codecs so I can at least follow instructions.  I hope you can spare the patience to give them in baby talk.

---

### Post by HappyFeet on 2010-01-02
When someone asks for the output of whatever, just copy and paste what they are asking into a terminal, and hit enter. In this case, just **lspci** will do. Then after it spits out some info, highlight it copy it, then paste here so we can see it.

---

### Post by Stray Wolf on 2010-01-03
Thanks.  Info as follows:
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
00:18.0 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Link Control
01:05.0 FireWire (IEEE 1394): Agere Systems FW322/323 (rev 70)
01:0a.0 Communication controller: Conexant Systems, Inc. HSF 56k Data/Fax Modem
02:00.0 VGA compatible controller: nVidia Corporation G86 [GeForce 8500 GT] (rev a1)
04:00.0 Multimedia controller: ViXS Systems, Inc. XCode 2100 Series

I'll remember that.  "lspci"

---

### Post by Stray Wolf on 2010-04-07
[B]I have Karmic on a HP Pavilion and would like to not only use the TV card but also the IR remote and receiver that also came with the PC.  Have yet to do so.  I may be in over my head.

Re: TV Card does what?[/B] 			
 			 			 		   		 		 		Thanks.  Info as follows:
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
00:18.0 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Link Control
01:05.0 FireWire (IEEE 1394): Agere Systems FW322/323 (rev 70)
01:0a.0 Communication controller: Conexant Systems, Inc. HSF 56k Data/Fax Modem
02:00.0 VGA compatible controller: nVidia Corporation G86 [GeForce 8500 GT] (rev a1)
04:00.0 Multimedia controller: ViXS Systems, Inc. XCode 2100 Series

---

