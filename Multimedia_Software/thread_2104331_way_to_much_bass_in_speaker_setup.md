---
title: "way to much bass in speaker setup"
date: 2013-01-12
forum: Multimedia Software
---

### Post by jimbean on 2013-01-12
way to much bass in speaker setup
ubuntu 12.10
Advanced Linux Sound Architecture Driver Version 1.0.25.
{/sbin/lsmod}
vice
k8temp                 12842  0 
soundcore              14599  1 snd
i2c_nforce2            12869  0 
snd_page_alloc         14036  2 snd_hda_intel,snd_pcm
mac_hid                13037  0 
lp                     13299  0 
parport                40753  3 parport_pc,ppdev,lp
hid_generic            12445  0 
hid_logitech           22040  0 
ff_memless             12877  1 hid_logitech
usbhid                 41702  1 hid_logitech
hid                    82142  3 hid_generic,hid_logitech,usbhid
firewire_ohci          35521  0 
firewire_core          57492  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
pata_amd               13750  2 
sata_nv                22993  0 
forcedeth              57756  0 
usb_storage            39350  1 
floppy                 55444  0 
lspci -v | grep audio 
nothing
{uname -r}
3.5.0-21-generic
cat /proc/asound/cards
 0 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xdfff0000 irq 20
 1 [NVidia_1       ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xdeffc000 irq 16
{cat /proc/asound/oss/sndstat}
Sound Driver:3.8.1a-980706 (ALSA v1.0.25 emulation code)
Kernel: Linux ***-******** 3.5.0-21-generic #32-Ubuntu SMP Tue Dec 11 18:52:46 UTC 2012 i686
Config options: 0

Installed drivers: 
Type 10: ALSA emulation

Card config: 
HDA NVidia at 0xdfff0000 irq 20
HDA NVidia at 0xdeffc000 irq 16

Audio devices: NOT ENABLED IN CONFIG

Synth devices: NOT ENABLED IN CONFIG

Midi devices: NOT ENABLED IN CONFIG

Timers:
31: system timer

Mixers: NOT ENABLED IN CONFIG
{Chip: Realtek ALC882}

---

### Post by jimbean on 2013-01-12
nevermind {animal} chewed satellite speaker wires

---

