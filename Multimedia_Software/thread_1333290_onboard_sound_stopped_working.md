---
title: "onboard sound stopped working"
date: 2009-11-21
forum: Multimedia Software
---

### Post by Liandre on 2009-11-21
Hey all

I recently upgraded my soundcard to the Asus Xonar DS, however I found out the card is not compatable with ALSA. So I thought I would revert back to my onboard Realtek ALC889A codec, however now that is not working!

Both the Xonar DS and Realtek onboard work perfectly in windows. I tried following the [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449) guide and made a note of what I did step by step if that helps ...

aplay -l

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC889A Analog [ALC889A Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC889A Digital [ALC889A Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

lspci -v

00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
    Subsystem: Giga-byte Technology Device a102
    Flags: bus master, fast devsel, latency 0, IRQ 22
    Memory at fbff8000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

0d:01.0 Multimedia audio controller: C-Media Electronics Inc CMI8788 [Oxygen HD Audio]
    Subsystem: ASUSTeK Computer Inc. Device 838e
    Flags: bus master, medium devsel, latency 32, IRQ 10
    I/O ports at ee00 [size=256]
    Capabilities: <access denied>

sudo modprobe snd-hda-intel
sudo gedit /etc/modules
added snd-hda-intel
alsamixer - increased all
sudo alsactl store
grep 'audio' /etc/group
shows: audio:x:29:pulse
sudo gedit /etc/group
changed audio:x:29:pulse:username
still nothing in Totem, VLC

I've also updated ALSA using [http://ubuntuforums.org/showthread.php?t=1046137](http://ubuntuforums.org/showthread.php?t=1046137)

If it helps my System Spec is as follows ...

CPU: Core i7 920 @ 3.8GHz 
Motherboard: Gigabyte EX58-UD5 Intel X58
RAM: Corsair XMS3 6GB PC3-12800C9 DDR3
GPU: BFG GeForce GTX 295 1792MB GDDR3
HD: VelociRaptor 300GB 10,000RPM
Soundcard: Asus Xonar DS + Onboard Realtek ALC889A
OS: Windows 7 64-Bit + Ubuntu 9.10 64-Bit

Thanks in advance 

Lia

---

### Post by Liandre on 2009-11-23
If I purchased another sound card, say the Xonar D2X, could I run my speakers through the D2X (compatable with ALSA) and headphones through the DS (not compatable with ALSA)?

That is if I can't run my speakers through the onboard.

Cheers all

Lia

---

### Post by Liandre on 2009-11-23
I did a fresh install of Ubuntu and now the sound works. Not sure why the onboard sound stopped working after installing the Xonar DS. Oh well.

Lia

---

