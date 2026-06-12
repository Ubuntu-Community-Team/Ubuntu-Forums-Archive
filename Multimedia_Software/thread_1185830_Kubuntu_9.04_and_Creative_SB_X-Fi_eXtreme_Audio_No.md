---
title: "Kubuntu 9.04 and Creative SB X-Fi eXtreme Audio Notebook"
date: 2009-06-12
forum: Multimedia Software
---

### Post by s.maciek on 2009-06-12
So as in the topic. I do need you help guys. I own this sound card and I really would love to use it's power under Linux, not only on Windows where it is fully-supported.
So from the beginning ...
I have tried to install 1.00 drivers delivered by Creative, compiled it whole, but after rebooting it did not work as it should to.

I have found that new driver for this stuff just came out ( month ago ) so this topic is fresh and it can help many pother ppl if we will solve it out ! 
The name of driver is **snd_ctxfi**. Downloaded it, then
```
$ ./configure
$ sudo make ; sudo make install
```
I think all went okay, because there were no Error messages ...
But there were also no effect. There were no things to turn on at sound properties.
When I used a script for checking all info about alsa it have shown :
```
!!Loaded ALSA modules
!!-------------------

snd_hda_intel

```
You can found it whole at [LINK]("http://www.alsa-project.org/db/?f=06d1b5d03da3b6772f70b699bda192a30c270316").
It seems the driver was not fully loaded or it do not work property.
Also alsa have not loaded snd_ctxfi module - it should be loaded.
Interesting thing, can be also this one :
```
!!Soundcards recognised by ALSA
!!-----------------------------

 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xdf400000 irq 22
 1 [Generic        ]: HDA-Intel - HD-Audio Generic
                      HD-Audio Generic at 0xd9100000 irq 17


!!PCI Soundcards installed in the system
!!--------------------------------------

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
0a:00.0 Audio device: Creative Labs [SB X-Fi Xtreme Audio] CA0110-IBG

```
When I tried :
```
$ sudo modprobe snd-ctxfi
[sudo] password for macio:
FATAL: Error inserting snd_ctxfi (/lib/modules/2.6.28-11-generic/kernel/sound/pci/ctxfi/snd-ctxfi.ko): Unknown symbol in module, or unknown parameter (see dmesg)

```
Where do I make a mistake ? What should I do to make it work ?
It seems, the system can see the sound card but I have installed the drivers wrong, or I just missed something. Can you help me guys please ? I feel it can be solved but I do need urs brain storm !

P.S.
Command :
```
$ lspci -v
```
Have shown in 2 last "lines":
```
07:00.0 PCI bridge: Creative Labs Device 7006
        Flags: bus master, fast devsel, latency 0
        Bus: primary=07, secondary=0a, subordinate=0a, sec-latency=0
        Memory behind bridge: d9100000-d91fffff
        Capabilities: <access denied>
        Kernel modules: shpchp

0a:00.0 Audio device: Creative Labs [SB X-Fi Xtreme Audio] CA0110-IBG
        Subsystem: Creative Labs Device 0018
        Flags: bus master, fast Back2Back, medium devsel, latency 0, IRQ 11
        Memory at d9100000 (32-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel modules: snd-hda-intel

```

Sorry for my English. I know it's bad, still learning :), hope it is understandable on enough level.

---

