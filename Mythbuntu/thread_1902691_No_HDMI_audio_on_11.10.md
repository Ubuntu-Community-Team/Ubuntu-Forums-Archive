---
title: "No HDMI audio on 11.10"
date: 2011-12-31
forum: Mythbuntu
---

### Post by AndrewWalker on 2011-12-31
I'm trying to get Mythbuntu 11.10 x86_64 working and I'm unable to get HDMI audio to function. 
The machine I'm using is an Emachines ER1401 with Nvidia graphics and has both optical SPDIF and aledgedly HDMI audio output. The devices are as listed

**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC662 rev1 Analog [ALC662 rev1 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC662 rev1 Digital [ALC662 rev1 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

But when I try alsamixer it lists 3 SPDIF devices, S/PDIF, S/PDIF Default and S/PDIF 1 but all are active (i.e not muted).
All the options seem to be available in settings for HDMI but nothing I do gets any sound out. There is nothing in dmesg at all about HDMI and I've tried altering /etc/asound.conf as a few people have suggested but no change. Am I missing a kernel module or something? I've tried everything on this forum and spent hours trying, I've even tested the cable and TV out of desperation!

---

### Post by nickrout on 2011-12-31
What choices are you given in mythtv when you scan for audio devices?

Also which nvidia drivers are you using?

---

### Post by AndrewWalker on 2011-12-31
That's the crazy thing, the options appear in audio devices as HDMI, they just don't work! I get no errors, no messages, everything seems fine except no sound. I'm using the standard nvidia drivers with 11.10 which I think are version 290. I've even tried to get audio working with gnome desktop which also shows the drivers and everything appears ok except no sound when I select test speakers. I'm getting to the point where I'm going to have to install Windows 7 just to prove the hardware actually works!

---

### Post by nickrout on 2012-01-01
> **AndrewWalker said:**
> That's the crazy thing, the options appear in audio devices as HDMI, they just don't work!

I repeat my question, what devices does myth show after you scan for audio devices?> 

 I get no errors, no messages, everything seems fine except no sound. I'm using the standard nvidia drivers with 11.10 which I think are version 290. I've even tried to get audio working with gnome desktop which also shows the drivers and everything appears ok except no sound when I select test speakers. I'm getting to the point where I'm going to have to install Windows 7 just to prove the hardware actually works!

I assume you have run alsamixer and made sure the appropriate device is not muted?

---

### Post by ian dobson on 2012-01-01
Hi,

May be try using aplay from the terminal to find out which audio device is the correct one.

See [http://manpages.ubuntu.com/manpages/intrepid/man1/aplay.1.html](http://manpages.ubuntu.com/manpages/intrepid/man1/aplay.1.html)

Regards
Ian Dobson

---

