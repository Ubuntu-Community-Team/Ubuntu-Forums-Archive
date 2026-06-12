---
title: "TV Video Input Card - how to use in Linux?"
date: 2011-03-05
forum: Multimedia Software
---

### Post by green_earth on 2011-03-05
Hi, I can't seem to find a post that answers my question, so I hope this isn't obvious to many...

I just installed 10.10 on my desktop, which contains a TV card with audio/video inputs. So here are my questions:

1. How do I verify that it is recognized in Ubuntu? I'm a perpetual newbie, so without something like the Windows Device Manager, I'm a little lost...

2. Assuming Ubuntu is "seeing" the card, what programs do I need to use to grab and convert video to a digital format such as Xvid or even DVD? I want to convert around 20 old family movies on VHS to both DVD and a digital format such as Xvid or MP4. Is there a way to do this on the fly or real time? 

Any help would be most appreciated!

---

### Post by johntaylor1887 on 2011-03-05
Please post the output of:
```
lspci
```

---

### Post by green_earth on 2011-03-05
Here is the output of lspci:

> 00:00.0 RAM memory: nVidia Corporation MCP55 Memory Controller (rev a2)
00:01.0 ISA bridge: nVidia Corporation MCP55 LPC Bridge (rev a3)
00:01.1 SMBus: nVidia Corporation MCP55 SMBus (rev a3)
00:02.0 USB Controller: nVidia Corporation MCP55 USB Controller (rev a1)
00:02.1 USB Controller: nVidia Corporation MCP55 USB Controller (rev a2)
00:04.0 IDE interface: nVidia Corporation MCP55 IDE (rev a1)
00:05.0 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a3)
00:05.1 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a3)
00:05.2 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a3)
00:06.0 PCI bridge: nVidia Corporation MCP55 PCI bridge (rev a2)
00:06.1 Audio device: nVidia Corporation MCP55 High Definition Audio (rev a2)
00:08.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a3)
00:0f.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:07.0 Multimedia controller: Philips Semiconductors SAA7134/SAA7135HL Video Broadcast Decoder (rev 01)
01:0a.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)
02:00.0 VGA compatible controller: nVidia Corporation G71 [GeForce 7950 GT] (rev a1)

---

### Post by johntaylor1887 on 2011-03-05
It seems Ubuntu recognizes your card as 01:07.0 Multimedia controller: Philips Semiconductors SAA7134/SAA7135HL Video Broadcast Decoder (rev 01). Try installing TVTime from synaptic and give it a go.

---

### Post by green_earth on 2011-03-05
johntaylor1887, thanks. 

Any suggestions on the best program to use to convert the video stream to xvid or some other codec?

---

### Post by johntaylor1887 on 2011-03-06
> **green_earth said:**
> johntaylor1887, thanks. 

Any suggestions on the best program to use to convert the video stream to xvid or some other codec?

TV works then?

Winff is a good all around video converter. Handbrake is also good if you need a converter for iphone, ipod, psp, etc. (mp4)

---

### Post by green_earth on 2011-03-06
Yes, TV is working. I'm just not sure how to take that video feed through TVTime and get it "ripped" or copied onto the hard drive... I'll get both WinFF and Handbrake installed and see if I can follow some breadcrumbs. Thanks again!

---

