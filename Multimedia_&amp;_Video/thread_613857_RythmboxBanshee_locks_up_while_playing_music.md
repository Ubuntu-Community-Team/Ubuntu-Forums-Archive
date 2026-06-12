---
title: "Rythmbox/Banshee locks up while playing music"
date: 2007-11-15
forum: Multimedia &amp; Video
---

### Post by Stryker on 2007-11-15
Hello all.

I've been fighting with my sound card to try and determine why Rythmbox and Banshee lock up during playback of my mp3's located on my hard drive.

I tried following the Comprehensive Guide to Sound Issues ([http://ubuntuforums.org/showthread.php?t=205449&highlight=alsamixer+settings+is](http://ubuntuforums.org/showthread.php?t=205449&highlight=alsamixer+settings+is))

Here is the output from aplay -l
```
**** List of PLAYBACK Hardware Devices ****
card 0: SI7012 [SiS SI7012], device 0: Intel ICH [SiS SI7012]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```
Here is the relevant output from lspci -v
```
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
        Subsystem: Elitegroup Computer Systems Unknown device 1b13
        Flags: bus master, medium devsel, latency 64, IRQ 18
        I/O ports at e800 [size=256]
        I/O ports at e400 [size=128]
        Capabilities: [48] Power Management version 2

```

I found the correct module which should be snd-intel8x0 and got the driver installed (I think). After rebooting though, now I have NO sound.

I went into Volume Control, made sure everything was un-muted and turned up. Still no effect.

I found another hopefully helpful thread and followed these instructions.

* sudo apt-get install module-assistant
* sudo m-a update
* sudo m-a prepare
* sudo m-a a-i alsa
* Reboot and setup your sound settings

But I still have no sound.

My original issue was that mp3 files and music extracted from CD's would just lockup after a few songs. I'm relatively new to Ubuntu but have a high technical background. So any help or suggestions would be most appreciated as I'm not sure where to go and I'm not sure exactly what questions I need to ask to move forward.

Thanks!

---

### Post by Stryker on 2007-11-16
bumpity

---

### Post by Stryker on 2008-01-03
Just updating this for those that find it.

Found out that in following directions above, I had told my system to try to load an ISA sound card. That has been corrected and I can play music for a while. However Rhythmbox still will suddenly stop playing MP3's until I reboot the system.

I ran Rhythmbox in debug mode from a terminal and when it locks up, it continues to process the file as normal. The debug output doesn't change or show any errors. I suspect it's an issue with the driver then and not Rhythmbox as any player does the same thing.

I'm using the snd-intel8x0 driver on an amd64 kernel. If anyone has any further suggestions I would appreciate it.

Thanks,
Stryker

---

