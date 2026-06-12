---
title: "Fuzzy Speakers"
date: 2007-10-08
forum: Multimedia &amp; Video
---

### Post by zoqaeski on 2007-10-08
For some odd reason my left speaker has been making static and fuzzy sounds that I can hear no matter what music or sounds I play. I've checked the cables, I've reinstalled the ALSA drivers, I've played around with the volume and yet this irritating noise is still there. It doesn't seem to be a hardware problem, as the speaker works fine when I plug my mp3 player in and play off that, and my other OS on this dual-boot system has a whole lot of other bugs but the sound works fine. I've had some issues with this before; rebooting usually fixed it but now the problematic fuzziness occurs with the drum roll when you login. I can't figure out what's causing the problem, but I'd really really really like to get it fixed. Can anyone help me? Please?

By the way, I've got an internal sound card on the motherboard that came with this computer, and stereo speakers with a subwoofer.

EDIT
I boot up this morning, and the speakers appear to be working fine, which is even more odd as they were completely screwing up yesterday, although I suspect that the good sound quality won't last the day...

I dunno if this is useful, but:
(sudo) lspci -v yields:
```
Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
        Subsystem: Dell Unknown device 01d2
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at efebc000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: [50] Power Management version 2
        Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
        Capabilities: [70] Express Unknown type IRQ 0

```
and aplay -l yields:
```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

```

---

### Post by zoqaeski on 2007-10-23
Doesn't anyone know how to fix this issue? It comes and goes, but it is really annoying me!

---

### Post by flange on 2007-11-26
I know this post is getting a little old, but I wanted to confirm that I'm having the same issue with the same audio controller, and I'm also getting static out of the left speaker.

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
        Subsystem: Intel Corporation Unknown device 0417
        Flags: bus master, fast devsel, latency 0, IRQ 22
        Memory at 52200000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: [50] Power Management version 2
        Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
        Capabilities: [70] Express Unknown type IRQ 0

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by flange on 2007-11-27
I was able to completely eliminate the left speaker static problem and wanted to follow up on how I did it.

First, I followed the steps on [this wiki page]("https://help.ubuntu.com/community/HdaIntelSoundHowto") to install ALSA from source, and then modify the alsa-base config file.

I have an Intel "Bad Axe"(D975XBX) motherboard, so I added the following line to /etc/modprobe.d/alsa-base:

options snd-hda-intel model=ref

I had a small problem with gnome-settings-daemon loading on reboot, but after another reboot, it went away.  I'm not sure how that all worked out.  Oh, and I had to change the Default Mixer Tracks from "Master" to "PCM" in System->Preferences->Sound to make the multimedia keys control volume correctly.

---

