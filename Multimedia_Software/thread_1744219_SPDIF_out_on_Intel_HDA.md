---
title: "SPDIF out on Intel HDA"
date: 2011-04-30
forum: Multimedia Software
---

### Post by bhobw on 2011-04-30
Hi,

Struggling to get the optical output working on an :
Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 04)

Within the sound preferences I have only analog options: Surround 5.0, 5.1 etc etc, nothing digital.

I have this:

lspci -s 00:1b.0 -vn


00:1b.0 0403: 8086:2668 (rev 04)
    Subsystem: 1297:c781
    Flags: bus master, fast devsel, latency 0, IRQ 42
    Memory at c0200000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [50] Power Management version 2
    Capabilities: [60] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
    Capabilities: [100] Virtual Channel
    Capabilities: [130] Root Complex Link
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

The sound card is built onto the MB. There is an optical input and an optical output port at the back of the machine, so definitely capable.

From reading around I added to the bottom of 'alsa-base.conf':
options snd-hda-intel model=auto

This helped originally by providing me with more 'surround' options, but still nothing digital.

Has anyone any ideas what to try next?

Running Maverick - 2.6.35-28-generic

Thanks
BHOBW

---

### Post by lidex on 2011-05-01
Try using alsamixer or gnome-alsamixer to unmute spdif or iec958.
Reference:
[http://alsa.opensrc.org/DigitalOut](http://alsa.opensrc.org/DigitalOut)

**Alsamixer**
Using a Terminal="Applications->Accessories->Terminal"
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.

**Gnome-alsamixer**
Using Alt+F2 run dialog
```
 gnome-alsamixer 
```
**Use 'Edit -> Sound Card Properties' menu to enable elements.**
Soundcard tab to select / adjust levels.
To install:
```
sudo apt-get install gnome-alsamixer
```

---

