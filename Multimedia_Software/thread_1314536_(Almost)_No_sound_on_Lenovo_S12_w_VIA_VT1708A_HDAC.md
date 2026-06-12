---
title: "(Almost) No sound on Lenovo S12 /w VIA VT1708/A HDAC"
date: 2009-11-04
forum: Multimedia Software
---

### Post by adampaetznick on 2009-11-04
I have an Ubuntu 9.10 install on a Lenovo Ideapad S12 with VIA Nano (not Intel Atom) processor.  On some reboots audio output works initially (e.g. the alert sound at gdm login, or an alert or two once I login).  After that, nothing.

lscpi -v shows: 
00:14.0 Audio device: VIA Technologies, Inc. VT1708/A [Azalia HDAC] (VIA High Definition Audio Controller) (rev 20)
        Subsystem: Lenovo Device 389a
        Flags: bus master, fast devsel, latency 0, IRQ 17
        Memory at f5500000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: [50] Power Management version 2
        Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
        Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
        Capabilities: [100] Virtual Channel <?>
        Capabilities: [130] Root Complex Link <?>
        Kernel driver in use: HDA Intel
        Kernel modules: snd-hda-intel

aplay -l shows:
card 0: VT82xx [HDA VIA VT82xx], device 0: ALC269 Analog [ALC269 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

I have confirmed that my user is in the 'audio' group.  Any ideas?  Anyone else with an Ideapad S12, or this card having similar issues?

---

### Post by yoshiki2 on 2009-12-12
I'll be honest with you... I could never make my lenovo work with ubuntu 9.10 (no wired connection available). But everything works out of the box with mandriva 2010 one... Just give it a shot. Am using that on my lenovo and ubuntu on my laptop... So far I like both Distros.

---

### Post by Lokodi Balazs Levente on 2010-01-19
I have the same sound card with same problem on Ubuntu Carmic ... almost no sound and i can't find any solution , somebody heeeeeeelp :confused::confused::confused:
my config is: Amilo La 1703 (suchs) 2gb memory/Shempron 3500+ 64bit vga (via chrome9) onboard 128mb from system, sound VT1708/A with Ubuntu 9.10 Carmic 32bit.

---

