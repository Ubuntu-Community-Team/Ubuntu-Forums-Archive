---
title: "Need Assistance:  Audio Playback (Fiesty 7.04)"
date: 2007-09-14
forum: Multimedia &amp; Video
---

### Post by Llision on 2007-09-14
Hello,

I have recently installed Fiesty Fawn v7.04 all is well apart from the fact that I am unable
to play back audio of any form.

I have looked around the net a little, and I can't seem  to find much to help me out, I would appreciate it if you guys could give me a little advice:

On windows of which my sound works fine, I am using SigmaTel drivers.
I ran lspci and my output was as follows:

00:00.0 Host bridge: nVidia Corporation Unknown device 0071 (rev c1)
00:00.1 RAM memory: nVidia Corporation Unknown device 007f (rev a1)
00:00.2 RAM memory: nVidia Corporation Unknown device 0075 (rev a1)
00:00.3 RAM memory: nVidia Corporation Unknown device 006f (rev a1)
00:00.4 RAM memory: nVidia Corporation Unknown device 00b4 (rev a1)
00:01.0 RAM memory: nVidia Corporation Unknown device 0076 (rev a1)
00:01.1 RAM memory: nVidia Corporation Unknown device 0078 (rev a1)
00:01.2 RAM memory: nVidia Corporation Unknown device 0079 (rev a1)
00:01.3 RAM memory: nVidia Corporation Unknown device 007a (rev a1)
00:01.4 RAM memory: nVidia Corporation Unknown device 007b (rev a1)
00:01.5 RAM memory: nVidia Corporation Unknown device 007c (rev a1)
00:01.6 RAM memory: nVidia Corporation Unknown device 007d (rev a1)
00:02.0 PCI bridge: nVidia Corporation Unknown device 007e (rev a2)
00:04.0 PCI bridge: nVidia Corporation Unknown device 007e (rev a2)
00:05.0 PCI bridge: nVidia Corporation Unknown device 007e (rev a2)
00:09.0 RAM memory: nVidia Corporation MCP55 Memory Controller (rev a1)
00:0a.0 ISA bridge: nVidia Corporation MCP55 LPC Bridge (rev a2)
00:0a.1 SMBus: nVidia Corporation MCP55 SMBus (rev a2)
00:0a.2 RAM memory: nVidia Corporation MCP55 Memory Controller (rev a2)
00:0b.0 USB Controller: nVidia Corporation MCP55 USB Controller (rev a1)
00:0b.1 USB Controller: nVidia Corporation MCP55 USB Controller (rev a2)
00:0d.0 IDE interface: nVidia Corporation MCP55 IDE (rev a1)
00:0e.0 RAID bus controller: nVidia Corporation MCP55 SATA Controller (rev a2)
00:0e.1 RAID bus controller: nVidia Corporation MCP55 SATA Controller (rev a3)
00:0e.2 RAID bus controller: nVidia Corporation MCP55 SATA Controller (rev a4)
00:0f.0 PCI bridge: nVidia Corporation MCP55 PCI bridge (rev a2)
00:0f.1 Audio device: nVidia Corporation MCP55 High Definition Audio (rev a2)
00:13.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
00:18.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 7900 GS (rev a1)
03:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5751 Gigabit Ethernet PCI Express (rev 21)
04:0a.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)

Within the sound preferences I can select Sigmatel STAC9227 but this does not affect my audio output at all.

Regards Llision

---

### Post by ufayzull on 2007-09-14
Basically this is what you need to do to get the sound working.
1. soundcard, which you have, lspci output
2. appropriate alsa module loaded in your kernel, alsa module needs to recognize your card. you can check this by looking into /proc/asound directory. there will be bunch of files for each recognized sound card and you can 'cat' the content of various files there to see what devices exist on each card, useful for doing digital out.
3. once the card is recognized by alsa you need to unmute certain channels, using amixer.

hope this helps.

---

