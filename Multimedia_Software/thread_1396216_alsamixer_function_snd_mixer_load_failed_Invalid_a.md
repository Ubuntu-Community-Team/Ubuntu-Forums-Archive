---
title: "alsamixer: function snd_mixer_load failed: Invalid argument"
date: 2010-02-01
forum: Multimedia Software
---

### Post by tylersontag on 2010-02-01
```
alsamixer: function snd_mixer_load failed: Invalid argument
```

This is the error i get when trying to run alsamixer

I've tried running through the Comprehensive Sound Problem solution guide and have even built alsa from source and i'm still getting this problem whenever i run alsamixer.


The reason im needing to run alsa mixer is to get my HDMI out to carry sound with it.  Which isn't behaving as expected either

sudo lspci -v

```
01:00.1 Audio device: nVidia Corporation Device 0be3 (rev a1)
	Subsystem: Giga-byte Technology Device 34d5
	Flags: bus master, fast devsel, latency 0, IRQ 10
	Memory at f9e7c000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: [60] Power Management version 3
	Capabilities: [68] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Capabilities: [78] Express Endpoint, MSI 00

```

sudo aplay -l
```
card 0: Intel [HDA Intel], device 0: VT1708B Analog [VT1708B Analog]
  Subdevices: 2/2
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
card 0: Intel [HDA Intel], device 1: VT1708B Digital [VT1708B Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

My nvidia card should show up on aplay, but does not.  I'm running a Geforce 210 and per this page built alsa with the hda-intel driver [http://www.alsa-project.org/main/index.php/Matrix:Vendor-Nvidia](http://www.alsa-project.org/main/index.php/Matrix:Vendor-Nvidia)

I'm out of ideas at this point, so any advice is welcome

---

### Post by tylersontag on 2010-02-01
alright,  i just build the ALSA version 22, cause i had read that the Geforce 2XX series cards are patch into this version... and i took one step forward and 2 steps back :-D

lspci -v gives:

```
01:00.1 Audio device: nVidia Corporation Device 0be3 (rev a1)
	Subsystem: Giga-byte Technology Device 34d5
	Flags: bus master, fast devsel, latency 0, IRQ 28
	Memory at f9e7c000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: [60] Power Management version 3
	Capabilities: [68] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable+
	Capabilities: [78] Express Endpoint, MSI 00
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

```

So now its explicitly saying it sees my audio device and  knows what module to use.

However, aplay -l lists

```
tag@tagcenter:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****

```

Nada, nothing.

Now i have no sound, before i could still put out sound through my motherboard but no more :-/  When i look throuh the GUI 'Sound' item under system>Preference theres no devices listed under Hardware...

i tried adding the snd-hda-intel to /etc/modules but to no avail... it looks like i need to run the new equivalent of update-modules but i'm not sure what that is...

---

### Post by tylersontag on 2010-02-05
Just a little update, to anyone who might come across this same problem (This error, with a GEFORCE 2XX HDMI out card)

After having completely beat to hell any semblence of a sound system with a hodgepodge of various hacks i pulled together from various parts of the internets, i did a full remove --purge on anything with the word alsa in it.  I then pulled the latest stable ALSA driver (1.0.20), and compiled it on my box with cards=all-drivers.   After a restart, i had sound.

It was back to only working on my motherboard sound, but still having the alsamixer problem, feeling good that at least i had a bomb-shelter solution to get back to a workable state no mater what i did, but still slightly tired of messing with it after 3 days of hacking, i decided to try this same solution with the newst ALSA.

I had before (which messed up my system) pulled 1.0.22, so i tried the newer 1.0.22.1 this time, having before wanted to shy away from partial releases.   Dropped this bomb again, and not only did lspci show modules associated with my integrated and HDMI sound device, i still had sound!  Furthermore, alsamixer worked!   Unfortunatly, there was no HDMI bar for me to unmute, similarly aplay didn't list my HDMI device.

I've read that the next patch is suppost to have support for my video card.  So untill then, i'll stick with 1600x1200 with sound versus 1920x1080 in silence :-D

p.s- i built using all-drivers cause i was a little shakey on if i was using the right driver for my board (hda-intel)  after i got it working with all-drivers, thats the driver it chose for my devices.  So i think that may simply be a colinearity, so to speak.

---

### Post by gnznt on 2011-07-14
i think i can, i think i can, i think i can...

Ubuntu Lucid.

---

