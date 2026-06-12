---
title: "Recorded sound stutters"
date: 2009-12-26
forum: Multimedia Software
---

### Post by kencamargo on 2009-12-26
Hello,

I am using Karmic 64 bits. I went through a lot of loops to (kinda) get sound working on my desktop, which has an onboard soundcard. I can't get the sound recorder to record properly from the microphone, every attempt ends up with a stuttering playback that would possibly be terrific if I were aspiring to enter the rap arena, but that's not the case. Skype won't work either; I can hear the test call, but don't get anything out.

I've already upgraded pulseaudio from the launchpad, tinkered with all possible settings both under pulseaudio's volume control and alsamixer, to no avail.

The relevant configuration follows:

aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: VT82xx [HDA VIA VT82xx], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: VT82xx [HDA VIA VT82xx], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

lspci -v
80:01.0 Audio device: VIA Technologies, Inc. VT1708/A [Azalia HDAC] (VIA High Definition Audio Controller) (rev 10)
    Subsystem: ASUSTeK Computer Inc. Device 81b3
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Memory at bfffc000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

Any help will be appreciated.

An excellent 2010 for all,
Ken

---

