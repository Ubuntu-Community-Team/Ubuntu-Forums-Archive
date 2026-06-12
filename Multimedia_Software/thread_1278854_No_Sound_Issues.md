---
title: "No Sound Issues"
date: 2009-09-30
forum: Multimedia Software
---

### Post by jlg6184 on 2009-09-30
Alright, I have racked my brain, and checked/read over several articles/how-to's and still haven't the slightest idea as to how to fix my issue with no sound. I decided today to try out the new version of Ubuntu (last version used was 7.04) and I am having problems with my sound. It simply isn't working. I tried updating the ALSA drivers through one tutorial (don't have the link...) and when that didn't work, I tried another tutorial on switching it to run through OSS (also don't have the link) which also didn't work. At that point I figured I would just reformat and start over because the OSS thing didn't even remotely come close to working and made it to where the I was having issues even accessing the mixer and what not, so I figured a reformat would allow me to start back at scratch and try this again, but I am still coming up with nothing. It could be stress or that it is late, or that I am being an idiot, or simply that it just won't work, so I am presenting the issue to you. The sound is not muted and I have tried every sound setting that is offered to no avail. Here is the information I have on the sound card that the basic tutorials tell me to find out:

```
card 0: NVidia [HDA NVidia], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
    Subsystem: Hewlett-Packard Company Device 2a34
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 22
    Memory at fe024000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

```I would appreciate any help that might possibly be provided. Thank you.

---

### Post by Nattydread69 on 2009-09-30
I have the same hardware and same problem. I have tried everything. :(

---

### Post by Nattydread69 on 2009-09-30
ah the solution is to use OSS4, see this thread for link

[http://ubuntuforums.org/showthread.php?t=1137254&highlight=ALC883]("http://ubuntuforums.org/showthread.php?t=1137254&highlight=ALC883")

yay sound again ALSA sucks :o)

---

### Post by jlg6184 on 2009-09-30
Well, I figured out part of my problem, there was a BIOS setting that was wrong (Audio was set to Auto, so I enabled it) Now I have sound, but it is crap quality...off to try to figure out why that is...

---

