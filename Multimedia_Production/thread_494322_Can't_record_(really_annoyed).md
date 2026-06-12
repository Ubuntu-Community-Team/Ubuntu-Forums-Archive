---
title: "Can't record (really annoyed)"
date: 2007-07-06
forum: Multimedia Production
---

### Post by DAaaMan64 on 2007-07-06
I cannot record from my guitar, I have it plugged into the front mic here is an lspci:
```

daaaman64@govinda:~$ lspci
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
00:02.1 RAM memory: nVidia Corporation Unknown device 03bc (rev a1)
00:02.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:03.0 PCI bridge: nVidia Corporation C55 PCI Express bridge (rev a1)
00:06.0 PCI bridge: nVidia Corporation C55 PCI Express bridge (rev a1)
00:07.0 PCI bridge: nVidia Corporation C55 PCI Express bridge (rev a1)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.2 RAM memory: nVidia Corporation MCP51 Memory Controller 0 (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev a1)
00:0e.0 RAID bus controller: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:0f.0 RAID bus controller: nVidia Corporation MCP51 Serial ATA Controller (rev a1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
01:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7600 GT] (rev a1)
04:09.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev c0)


```

I have jack running it makes no difference whether it is on alsa or oss.  I use kmix and the latest ubuntu kernel.  I have tried every recording program I can think of.  **Please help.**

---

### Post by oxalá on 2007-07-06
oh, dude, I feel your pain.
kind of given up on Ubuntu Studio for the time being -- hopefully i'll return sometime in the future.
good luck!

---

### Post by nalmeth on 2007-07-06
I know it may seem like a redundant question, but have you checked your mixer settings?

Open up the preferences in the mixer, and make sure the mic is turned up and UNMUTED.

Go into the advanced preferences, so you can add a control for 20dB boost, and some other controls you may find useful.

---

### Post by DAaaMan64 on 2007-07-07
absolutely everything is turned up and turned on.  Save me!

---

### Post by nalmeth on 2007-07-08
Do you have your guitar plugged right into the mic jack? Or are you using a microphone and an amp?

---

### Post by Teer on 2007-07-08
I am having trouble with my mic, too.  I looked in alsamixer and the controls for the mic have an unusual notation... it says
L        R 
CAPTUR
  Mic

The L, R, CAPTUR are in dark red color and there is no volume bar.  I am using a Turtle Beach Santa Cruz, and a CX46xx chipset driver.  Any idea what this might indicate?

---

### Post by Teer on 2007-07-08
Hey, I got my fix.  Here it is in-case anyone else is doing a search for help:

In ALSAMIXER, I had to choose the device, switch to Capture view, look at ADC settings (was set to 100%), then press SPACE BAR on ADC - which enables capture.  Exit and let the recording begin!

[http://alsa.opensrc.org/index.php/Cs46xx](http://alsa.opensrc.org/index.php/Cs46xx)

---

