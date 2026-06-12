---
title: "Problem with microphone in Karmic"
date: 2009-11-09
forum: Multimedia Software
---

### Post by Ikka3990 on 2009-11-09
I am using Ubuntu 9.10 on a Lenovo Ideapad laptop and haven't been able to make the microphone work on my system.
( I know that there have been countless threads on sound problems on ubuntu before, and I have gone through many of them but I am still facing problems.)

lspci | grep Audio
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
01:00.1 Audio device: ATI Technologies Inc RV620 Audio device [Radeon HD 34xx Series]

relevant sections of hwinfo and lspci -v
hwinfo:
PCI 100.1: 0403 Audio device
  [Created at pci.318]
  UDI: /org/freedesktop/Hal/devices/pci_1002_aa28
  Unique ID: NXNs.STtQy1vl51C
  Parent ID: vSkL.KcfarPM+5y9
  SysFS ID: /devices/pci0000:00/0000:00:01.0/0000:01:00.1
  SysFS BusID: 0000:01:00.1
  Hardware Class: sound
  Model: "ATI RV620 Audio device [Radeon HD 34xx Series]"
  Vendor: pci 0x1002 "ATI Technologies Inc"
  Device: pci 0xaa28 "RV620 Audio device [Radeon HD 34xx Series]"
  SubVendor: pci 0x17aa "Lenovo"
  SubDevice: pci 0x3d9f 
  Driver: "HDA Intel"
  Driver Modules: "snd_hda_intel"
  Memory Range: 0x96110000-0x96113fff (rw,non-prefetchable)
  IRQ: 17 (1159 events)
  Module Alias: "pci:v00001002d0000AA28sv000017AAsd00003D9Fbc04sc03i00"
  Driver Info #0:
    Driver Status: snd_hda_intel is active
    Driver Activation Cmd: "modprobe snd_hda_intel"
  Config Status: cfg=new, avail=yes, need=no, active=unknown
  Attached to: #12 (PCI bridge)

lspci -v:
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
    Subsystem: Lenovo Device 3a0d
    Flags: bus master, fast devsel, latency 0, IRQ 22
    Memory at 96200000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

01:00.1 Audio device: ATI Technologies Inc RV620 Audio device [Radeon HD 34xx Series]
    Subsystem: Lenovo Device 3d9f
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Memory at 96110000 (32-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

NOTE: I have already installed alsamixer and unmuted the mic so please do not suggest that.

---

### Post by Ikka3990 on 2009-11-13
Bump.

---

### Post by koba101 on 2009-11-26
I've got the same situation, output works fine, but mic doesn't 

I got a dell inspiron laptop

---

### Post by TDK800 on 2009-11-27
Everyone, try this, fixes mic, with skype too, and pulseaudio is still installed: [http://ubuntuforums.org/showthread.php?p=8397068](http://ubuntuforums.org/showthread.php?p=8397068)

---

### Post by koba101 on 2009-11-27
that worked for me fine....should we mark this thread as SOLVED?

---

### Post by ok_dr on 2009-11-29
> **koba101 said:**
> that worked for me fine....should we mark this thread as SOLVED?

It should work for ikka in order to be marked as solved. It hasn't worked for me by the way.

---

### Post by Ikka3990 on 2010-12-25
So it was just that Ubuntu repositories weren't installing the latest alsa package by default? Come on!!
x-(

---

### Post by lidex on 2010-12-25
Alsa is integrated into the kernel, so you only get the version that it comes with unless you compile it yourself. New hardware coming out all the time - it's the nature of the beast. Is your problem solved?

---

### Post by Ikka3990 on 2010-12-25
Yes. The mic has worked perfectly since I installed the latest alsa from [http://www.alsa-project.org/](http://www.alsa-project.org/)

---

