---
title: "Intel ALC888 Analog Works Drear - No Digital Output"
date: 2009-06-30
forum: Multimedia Software
---

### Post by SedaliaSteve on 2009-06-30
(I'm trying to change the title from 'Drear' to 'Great'. Please forgive my fat fingers.)

I posted this in general but it seems more specific to here.

Most posts I've seen with show no sound but analog has worked since I furst installed it.

I have a Shuttle Prima XPC SP35 P2 barebones that I've installed 9.04 alternate on (for RAID1).

I've gotten the analog sound working but no luck with the digital SPDIF outputs. I borrowed some equipment from work to check them out and they are dead.

The How to tutorials helped get Pulse Audio and alsa installed. The volume control only shows an HDA Intel ALC888 Analog installed, The Pulse Audio manager shows:
alsa_output.pci_8086_293e_sound_card_0_alsa_playback_0
HDA Intel - ALC888 Analog
Index #0

Checking, I see:
***aplay -l***
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC888 Analog [ALC888 Analog]
Subdevices: 1/1
Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC888 Digital [ALC888 Digital]
Subdevices: 1/1
Subdevice #0: subdevice #0

***This is the only audio with lspci***
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
Subsystem: Holco Enterprise Co, Ltd/Shuttle Computer Device 3116
Flags: bus master, fast devsel, latency 0, IRQ 22
Memory at fdff8000 (64-bit, non-prefetchable) [size=16K]
Capabilities: [50] Power Management version 2
Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
Capabilities: [100] Virtual Channel <?>
Capabilities: [130] Root Complex Link <?>
Kernel driver in use: HDA Intel
Kernel modules: snd-hda-intel
[B][I]
cat /proc/asound/cards[/I][/B]
0 [Intel          ]: HDA-Intel - HDA Intel
                     HDA Intel at 0xfdff8000 irq 22

Any suggestions, threads or tutorials?

Steve

---

### Post by SedaliaSteve on 2009-07-05
Actually 'Drear' was a better description than my original intent of 'Great'. When I finally hooked it up to a real stereo it was horrifying. Total crap sound.

I kept trying and finally realized Alsa doesn't support the Intel ICH9 family. I was so upset I was seriously thinking about Windows!

I searched the Ubuntu support and found OSS: [https://help.ubuntu.com/community/OpenSound]("https://help.ubuntu.com/community/OpenSound").

I followed the directions. I also wiped out all the Pulse Audio and Alsa utilities I'd added. 

When I finished it came up flawlessly. The digital outputs worked. The sound of both analog and digital is bright and full range. Since I mean this to be a music server I finally have a system that can play music.

Steve

---

