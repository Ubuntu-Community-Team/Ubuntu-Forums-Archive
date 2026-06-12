---
title: "Bad Directory Name in /sys/devices"
date: 2009-03-17
forum: Multimedia Software
---

### Post by pgmer6809 on 2009-03-17
I have a SB Audigy card that I cannot get to record sound.
Playback is OK, but running all of the usual tools only gets me error msgs.
I have corresponded with the maintainer for the ALSA driver for this card, but so far no solution.
I was wondering if the following could be part of the problem.
Under /sys/devices there is a directory with a comma in the name. This directory name string shows up in alsamixer tabs etc. and then when I try to use it I get error messages about invalid characters in a file name. 

Question: Can I just go to /sys/devices and issue a mv cmd to rename the directory to something with no commas in it?

Below is the output of the lspci cmd and the ls cmd for the relevant directory. lspci looks OK. ls shows the name: STAC9750,51.

 lspci -v -s 0000:00:0c.0
00:0c.0 Multimedia audio controller: Creative Labs SB Audigy (rev 04)
        Subsystem: Creative Labs SB Audigy 2 ZS (SB0350)
        Flags: bus master, medium devsel, latency 64, IRQ 18
        I/O ports at a800 [size=64]
        Capabilities: [dc] Power Management version 2

root@shadow:/sys/devices/pci0000:00# ls -R 0000:00:0c.0
0000:00:0c.0:
0-0:STAC9750,51       device      modalias   sound:admmidi    sound:hwC0D2    sound:midiC0D3  sound:pcmC0D2p  subsystem_device
broken_parity_status  driver      msi_bus    sound:amidi      sound:midi      sound:pcmC0D0c  sound:pcmC0D3p  subsystem_vendor
bus                   enable      power      sound:controlC0  sound:midiC0D0  sound:pcmC0D0p  sound:pcmC0D4c  uevent
class                 irq         resource   sound:dmmidi     sound:midiC0D1  sound:pcmC0D1c  sound:pcmC0D4p  vendor
config                local_cpus  resource0  sound:hwC0D0     sound:midiC0D2  sound:pcmC0D2c  subsystem

ANd here is the error message reported by GNOME ALSA mixer application:

Bad key or directory name: "/apps/gnome-alsamixer/display_mixers/SigmaTel_STAC9750,51": `,' is an invalid character in key/directory names

---

