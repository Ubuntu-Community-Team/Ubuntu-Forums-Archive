---
title: "Mixers detect sound but nothing plays"
date: 2010-02-07
forum: Multimedia Software
---

### Post by helgatheviking on 2010-02-07
I've tried walking myself through all the sound help threads, but I am not having any luck.  Sound was fine a few days ago.  But now I get nothing.  I uninstalled and then reinstalled both alsa and pulseaudio... and their respective mixers bounce around like they recognize sound is being made, but nothing comes out of the speakers.  sound does work in windows so the speakers aren't blown.  nothing is muted to my knowledge... alsa and pulse mixers are not on mute.  output is set to Internal Audio and not HDMI stereo, though I never know which profile to be using.. i've pretty much tried them all to no avail.  

results of aplay -l
```

**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

```

results of lspci -v

```
01:05.1 Audio device: ATI Technologies Inc Device 970f
	Subsystem: Hewlett-Packard Company Device 3638
	Flags: bus master, fast devsel, latency 0, IRQ 19
	Memory at f2310000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

```

i get stuck on step 3 of the comprehensive sound repair thread:
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

idk what my chipset is.  nothing is listed at: 
[http://www.alsa-project.org/main/index.php/Matrix:Vendor-ATI](http://www.alsa-project.org/main/index.php/Matrix:Vendor-ATI)
for snd-hda-intel.  but since my sound WAS working so I can assume that I used to have a driver that worked properly.  

when i try step 4 i get
```

sudo modprobe snd-hta-intel
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base.conf.save, it will be ignored in a future release.
FATAL: Module snd_hta_intel not found.

```

I have an HP dv7-3057nr laptop with an ATI soundcard.  I'm running Karmic.. and not at all too happy with it!  (this is not my first problem w/ karmic).  i am running the 32bit edition even though my PC is 64bit capable.  

idk what else to report, what else do you need to know?  what else do you suggest?  many thanks in advance.

---

### Post by Yellow Pasque on 2010-02-07
The driver is snd-hda-intel, you typo'd.

---

### Post by helgatheviking on 2010-02-07
you're right.  tried again and got this

```

sudo modprobe snd-hda-intel
[sudo] password for helga: 
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base.conf.save, it will be ignored in a future release.
helga@helga-laptop:~$ 

```

---

### Post by Yellow Pasque on 2010-02-07
Ok, the module loaded (the warning is insignificant). Does sound work then?
Maybe you need to restart alsa:
```
cd /etc/init.d/
sudo ./alsa-utils restart
```

---

