---
title: "[SOLVED] No Sound"
date: 2008-09-25
forum: Multimedia Software
---

### Post by tonyh6243 on 2008-09-25
I have put together a HTPC with a EVGA 780i motherboard. I was attempting to use the digital SPDIF output integrated on the motherboard. I can not seem to get the sound working. I appreciate any suggestions. Below is an output of my lspci

00:00.0 Host bridge: nVidia Corporation C55 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.3 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.4 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.5 RAM memory: nVidia Corporation C55 Memory Controller (rev a2)
00:00.6 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.7 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.0 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.3 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.4 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.5 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.6 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:02.0 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:02.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:02.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:03.0 PCI bridge: nVidia Corporation C55 PCI Express bridge (rev a1)
00:09.0 RAM memory: nVidia Corporation MCP55 Memory Controller (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP55 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP55 SMBus (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP55 USB Controller (rev a1)
00:0b.1 USB Controller: nVidia Corporation MCP55 USB Controller (rev a2)
00:0d.0 IDE interface: nVidia Corporation MCP55 IDE (rev a1)
00:0e.0 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a3)
00:0e.1 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a3)
00:0e.2 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a3)
00:0f.0 PCI bridge: nVidia Corporation MCP55 PCI bridge (rev a2)
00:0f.1 Audio device: nVidia Corporation MCP55 High Definition Audio (rev a2)
00:11.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a3)
00:12.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a3)
00:13.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a3)
01:00.0 PCI bridge: nVidia Corporation Unknown device 05b1 (rev a2)
02:00.0 PCI bridge: nVidia Corporation Unknown device 05b1 (rev a2)
02:02.0 PCI bridge: nVidia Corporation Unknown device 05b1 (rev a2)
03:00.0 VGA compatible controller: nVidia Corporation GeForce 8800 GT (rev a2)
05:07.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)


Below is an output of my aplay -l

**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


Thank you

---

### Post by Yellow Pasque on 2008-09-25
Have you configured the alsa-base file?
[http://ubuntuforums.org/showpost.php?p=5131958&postcount=2](http://ubuntuforums.org/showpost.php?p=5131958&postcount=2)

Also, what is your output from this command:
```
asoundconf list
```

---

### Post by tonyh6243 on 2008-09-25
Thanks for the tip. I tried to configure the alsa-base file using both the 6stack-dig & 3stack-6ch-dig models, neither of which worked. Has anyone had any luck getting this to work? I should also mention that I am running 8.04 Server edition with the latest kernel.

The output of asoundconf list is: NVidia

---

### Post by tonyh6243 on 2008-09-25
As it turns out I did not have the SPDIF setting activated in the sound menu. I guess I still have quite a bit to learn about linux.

Thank you for the help.

---

