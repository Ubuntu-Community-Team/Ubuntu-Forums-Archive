---
title: "Alsa HELL: Need troubleshooting ideas"
date: 2010-12-20
forum: Multimedia Software
---

### Post by effenberg0x0 on 2010-12-20
**The Problem:**
I use a HTPC running Ubuntu for about 2 years and just recently upgraded to 10.10. 
Video still works flawlessly, for any format mplayer can handle (NVIDIA VDPAU). 
***Audio is only ok on the audio-out jack of the onboard card. It is scratchy and high-pitched on the HDMI port of the off-board Video Card (NVIDIA)***. 

**The Specs**
OS: Ubuntu 10.10, cron daily sudo apt-get update && sudo apt-get upgrade (up-to-date)
CPU: Pentium Dual CPU E2140 @ 1.60GHz
Motherboard: ECS 945GZ/CT-M
RAM: 4GB
Audio: 00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
Video: 
	-Onboard (not-in-use)
	-Nvidia GeForce 9500GT (driver version 260.19.21)
ALSA Version: 1.0.23 (default ubuntu install)   	
Alsa-info located at: [http://www.alsa-project.org/db/?f=cb21ef660ccdbf9e50ab322c5650f42e532fa911](http://www.alsa-project.org/db/?f=cb21ef660ccdbf9e50ab322c5650f42e532fa911)

**Diagnose**
- I don't see anything NVIDIA on aplay -l:
```

al@HOME-OFFICE:/etc$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```
- Yet I see the card on lspci:
```

00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
        Subsystem: Elitegroup Computer Systems Device 2918
        Flags: bus master, fast devsel, latency 0, IRQ 41
        Memory at f9f38000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>
        Kernel driver in use: HDA Intel
        Kernel modules: snd-hda-intel

01:00.0 VGA compatible controller: nVidia Corporation G96 [GeForce 9500 GT] (rev a1) (prog-if 00 [VGA controller])
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at fd000000 (32-bit, non-prefetchable) [size=16M]
        Memory at c0000000 (64-bit, prefetchable) [size=512M]
        Memory at fa000000 (64-bit, non-prefetchable) [size=32M]
        I/O ports at dc00 [size=128]
        [virtual] Expansion ROM at fea80000 [disabled] [size=512K]
        Capabilities: <access denied>
        Kernel driver in use: nvidia
        Kernel modules: nvidia, nvidia-current, nouveau, nvidiafb


```
- I can output crappy sound to HDMI using somewthing like mplayer -fs -ao alsa:device=hw=0.1 "$1". using hw=0.0 audio goes out through audio-out jack perfectly quality.

**Failed attempts to fix**	
- Upgrading alsa through script: [http://ubuntuforums.org/showthread.php?t=1046137](http://ubuntuforums.org/showthread.php?t=1046137)
	-To latest snapshot (using -s option): Compiles OK but no snd moule is loaded after boot. No soundcard detected.
	-To current (using -d option): Won't compile, many errors.

- Setting up options at /etc/alsa-source
	- option snd-hda-intel - no luck
	- snd-hda-intel enable-msi=0 - no luck
	- snd-hda-intel enable_msi=0 probe_mask=0xffff - no luck
	
- Setting up options at /etc/modprobe.d/alsa-base.conf
	- options snd-hda-intel model=3stack - no luck
	- options snd-hda-intel model=5stack - no luck
	- options snd-hda-intel model=ICH7 - no luck

---

### Post by BicyclerBoy on 2010-12-21
I believe you need the nvidia 260 driver to get hdmi audio working.

I installed alsa 1.023 (compiled) on *bunto 10.04 & still need the newer video driver for the hdmi devices to appear.

You can still get by with s/pdif if 2ch PCM, AC3 & DTS are good enough.

---

