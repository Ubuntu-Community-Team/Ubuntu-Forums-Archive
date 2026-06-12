---
title: "ALSA vs PulseAudio weirdness"
date: 2008-08-29
forum: Multimedia Software
---

### Post by wizardStan on 2008-08-29
Hello,
I run Ubuntu AMD64.  The output of aplay -l is
```
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC882 Analog [ALC882 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC882 Digital [ALC882 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```
Occasionally, for some reason, I'll not be able to playback any audio in MPlayer unless I switch to ALSA, or PulseAudio.  Back and forth I go.  One works for a while, then it dies and I switch, until that stops working and I must switch back.  When this happens, weirdness also occurs in other players: Movie Player, Rhythm Box, Flash, and even Pidgin stops playing sounds.
If I try to start up MPlayer when it's doing this, I get "Could not open/initialize audio device".  So I switch to the other driver (from Pulse to ALSA or vice versa) and try again, and it works.  For a while.  Then eventually (usually following a restart, but not always) I must switch it back.
I have no idea what causes the other programs I mentioned to start playing their sounds again, but sooner or later they do.
Most recently, two days ago, I was trying to listen to some streaming music, and neither Movie Player nor Rhythm Box was playing it: gave some kind of connection error which I hadn't thought to write down and cannot currently replicate.  MPlayer was in Pulse at the time, giving the "Could not open..." error, so I switched to ALSA and it worked.
It was still in ALSA this morning, when I was playing back some recorded music.  I since had to restart, and now it needed to be back in Pulse again, ALSA refusing to playback.  But now both Movie Player and Rhythm Box both playback again as well.  No problems except from MPlayer using ALSA drivers.
Hopefully I've explained this seemingly bizarre situation well enough.  Does anyone have a clue, either as to what may be going on, or even how I might go about diagnosing the problem?
Thanks a lot!  I don't want to have to reset every few days.  This isn't Windows, you know :D

---

### Post by Crafty Kisses on 2008-08-30
Post the results of > lspci

---

### Post by wizardStan on 2008-08-30
eep, sorry.  Here you go: lspci
```
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
00:09.0 RAM memory: nVidia Corporation MCP55 Memory Controller (rev a1)
00:0a.0 ISA bridge: nVidia Corporation MCP55 LPC Bridge (rev a2)
00:0a.1 SMBus: nVidia Corporation MCP55 SMBus (rev a2)
00:0b.0 USB Controller: nVidia Corporation MCP55 USB Controller (rev a1)
00:0b.1 USB Controller: nVidia Corporation MCP55 USB Controller (rev a2)
00:0d.0 IDE interface: nVidia Corporation MCP55 IDE (rev a1)
00:0e.0 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2)
00:0e.1 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2)
00:0e.2 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2)
00:0f.0 PCI bridge: nVidia Corporation MCP55 PCI bridge (rev a2)
00:0f.1 Audio device: nVidia Corporation MCP55 High Definition Audio (rev a2)
00:12.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a2)
00:18.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8600 GT (rev a1)
02:07.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
03:00.0 VGA compatible controller: nVidia Corporation GeForce 8600 GT (rev a1)

```

---

### Post by wizardStan on 2008-09-07
This seems to have advanced to a worse problem.
My sound seems to have died completely.
Trying to play something in Totem, it locks up.
MPlayer, no matter what audio system I choose, it says no audio/cannot open device.
Thinking maybe firefox or something had somehow locked my sound card, I killed everything, after which a lot of things refused to open.  I couldn't reopen firefox (process would hang, and nothing would display).  Same opening up any Nautilus windows.  Didn't try much else.
Hitting ctrl-alt-backspace did not solve the problem: I log back in, and it basically halts.  The pointer still works, but nothing else happens no matter how long I wait.
The only way to fix it is to reboot.
Any thoughts on where to begin looking?  Anyone?

---

### Post by wizardStan on 2008-09-08
Problem solved?  Maybe?
Don't know exactly what has been going on.  I stumbled on bug report [https://bugs.launchpad.net/ubuntu/+source/totem/+bug/191027](https://bugs.launchpad.net/ubuntu/+source/totem/+bug/191027) and following the advice of setting ALSA to the system default (as opposed to "auto") seems to have fixed the problem for the time being.

---

