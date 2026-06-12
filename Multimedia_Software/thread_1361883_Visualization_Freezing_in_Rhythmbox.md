---
title: "Visualization Freezing in Rhythmbox"
date: 2009-12-22
forum: Multimedia Software
---

### Post by jhd121 on 2009-12-22
Hi Everyone,

I am having a rather strange problem.  When I turn on the visualization in Rhythmbox, it will work fine for a few minutes and then suddenly freeze.  Rhythmbox continues to work fine, only the visualization is frozen.  The only way to fix it is to restart Rhythmbox, but then it will freeze again after a few minutes.  The type of visualization doesn't seem to matter, they all freeze.  I tried running Rhythmbox in debug mode but the output didn't contain an error.

Any ideas?  I don't even know where to start.

Thanks!

---

### Post by tripolitan on 2009-12-23
Yep, video problem but without any info on your system, I don't think anyone can do much for ya.

---

### Post by jhd121 on 2009-12-23
What information would be useful?  I am running Ubuntu 9.10 64bit.  Here is the output of lspci:

```
00:00.0 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a2)
00:01.0 ISA bridge: nVidia Corporation nForce 750a LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP78S [GeForce 8200] SMBus (rev a1)
00:01.2 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a1)
00:01.3 Co-processor: nVidia Corporation MCP78S [GeForce 8200] Co-Processor (rev a2)
00:01.4 RAM memory: nVidia Corporation MCP78S [GeForce 8200] Memory Controller (rev a1)
00:02.0 USB Controller: nVidia Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller (rev a1)
00:02.1 USB Controller: nVidia Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller (rev a1)
00:04.0 USB Controller: nVidia Corporation MCP78S [GeForce 8200] OHCI USB 1.1 Controller (rev a1)
00:04.1 USB Controller: nVidia Corporation MCP78S [GeForce 8200] EHCI USB 2.0 Controller (rev a1)
00:06.0 IDE interface: nVidia Corporation MCP78S [GeForce 8200] IDE (rev a1)
00:07.0 Audio device: nVidia Corporation MCP72XE/MCP72P/MCP78U/MCP78S High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge (rev a1)
00:09.0 IDE interface: nVidia Corporation MCP78S [GeForce 8200] SATA Controller (non-AHCI mode) (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation MCP77 Ethernet (rev a2)
00:0b.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Express Bridge (rev a1)
00:10.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Express Bridge (rev a1)
00:12.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Express Bridge (rev a1)
00:13.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge (rev a1)
00:14.0 PCI bridge: nVidia Corporation MCP78S [GeForce 8200] PCI Bridge (rev a1)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] HyperTransport Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Miscellaneous Control
00:18.4 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Link Control
01:08.0 Mass storage controller: Silicon Image, Inc. PCI0680 Ultra ATA-133 Host Controller (rev 02)
01:0a.0 FireWire (IEEE 1394): Agere Systems FW322/323 (rev 70)
02:00.0 VGA compatible controller: nVidia Corporation C77 [nForce 750a SLI] (rev a2)
```

---

### Post by billzeeabob on 2009-12-28
I am having very similar trouble.

I have never used visualization before so I do not know if the problem is new. It seems to freeze at the end of a song.

Dell 600m laptop with ATI Radeon R250 (Mobility FireGL 9000) video card running 9.10 32-bit.

What information would be helpful?

---

### Post by mbuller10 on 2010-01-23
same problem here too, with and nvidia gforce g 105m on a thinkpad sl500, runny 9.10 32 bit 185 drivers

---

### Post by JSeymour on 2010-01-23
Same thing happens here. Dell PowerEdge 1600SC. Ubuntu 9.10 Desktop, 32-bit.  ATI Radeon HD 2400 Pro 256MB PCI.  fglrx driver.  I *think* I've seen it happen after pause or when starting a new song.  I've seen it restart w/o restarting Rhythmbox, but I don't recall the conditions.

Jim

---

### Post by nmyrick on 2010-01-26
Same problem here.  I have an Acer Aspire 4720z.  I've seen it restart sometimes, usually when I change to the Monoscope mode.  But it freezes after every song.

---

### Post by happylinuxguy on 2010-01-26
I have the same issue on an Nvidia 8600 GT.

When I first install the system, the freezing issue doesn't happen.  It's only after I install the NVIDIA driver that is starts to occur.  I think if it was tested more extensively by other users they may find the same thing.  It could be an issue with the way openGL interacts with gstreamer.

---

### Post by Uppsala9496 on 2010-02-10
Same issue with a radeon 4670.

---

### Post by nmyrick on 2010-02-10
With all of the posts here, it sounds like this has nothing to do with what computer or video card that anyone has, since there are so many different ones listed.  It sounds like it is a problem in RhythmBox itself.

---

### Post by Mr_Leo on 2010-02-18
similar problem on 9.10 64-bit w/ nvidia proprietery driver.
I've noticed that it works fine for the first song and then freezes.

---

### Post by nmyrick on 2010-02-18
I've since found that the best music media player for Ubuntu with GNome desktop is Banshee.  I like the GUI better, it has a great equalizer and works well with most I-Pods, but it doesn't have visualization.

[http://banshee-project.org](http://banshee-project.org)

---

### Post by mbuller10 on 2010-04-29
After all these months I think i finally figured it out, under preferences>playback check the the use crossfading backend option... worked for me

---

### Post by zeealpal on 2010-05-14
> **mbuller10 said:**
> After all these months I think i finally figured it out, under preferences>playback check the the use crossfading backend option... worked for me

Yep i tried that and it works.

When the cross fade option is enabled the visualization worked with no issues, and u cans et it to 0.2 seconds or so if u dont want to use the actual cross fade.

---

### Post by /bee/ on 2010-05-17
Thank you very much.  Enabling cross-fading appears to have done the trick for me as well.

---

### Post by mbuller10 on 2010-05-18
Welcome everybody, after using other people's posts so many times to fix my own issues I finally have found a fix I can share with others

---

### Post by rodrigor on 2010-06-11
> **mbuller10 said:**
> After all these months I think i finally figured it out, under preferences>playback check the the use crossfading backend option... worked for me

worked for me too, thanks!!!:D

---

### Post by fireprog on 2010-06-30
> **mbuller10 said:**
> After all these months I think i finally figured it out, under preferences>playback check the the use crossfading backend option... worked for me

Thanks worked for me too :)

---

### Post by John Baptist on 2010-07-31
Hi. Is there a launchpad bug for this? I think the developers should be aware.

---

### Post by Davidian1024 on 2010-08-20
This sounds like [Bug #534553]("https://bugs.launchpad.net/bugs/534553")

---

### Post by gbestrada on 2010-10-26
problem solved

---

