---
title: "No sound Ubuntu 8.04 - 10.10"
date: 2011-01-16
forum: Multimedia Software
---

### Post by rjb-356 on 2011-01-16
I'm writing in frustration.  I love Ubuntu and having been using it regularly as my primary OS since 8.04.  I'm not a newbie, but I'm no expert, I'm just a user who wants things to work the way they should without much effort on my part, because I have “real” work to get done using this wonderful tool (my pc).

When I first installed 8.04, sound was not an issue.  I don't remember when, but after some new version fresh install, I had to use the Ubuntu Forums Comprehensive Sound Problem Solutions Guide and would, at some point, get sound working.  But after so many changes, I never new which “fix” solved the problem for that Ubuntu distribution.

Now, I can't get my sound to work no matter what I do, including complete reinstalls.  I have a multi boot system which includes currently 8.04, 9.04, 10,10, WinXP and Win7.  Sound works fine in Windows.  I now CANNOT get sound to even work in 8.04, which originally would work after the initial install.

Ubuntu/Linux should not go backwards.  Sound that worked in previous versions should continue to work in later versions.  For the last few months I've had to rely on Windows (Oh No), as I can't get sound to work in Ubuntu (any version).

I've tried all the solutions from the Guide plus Google searches.  I've made an image of the base install plus all updating for all Ubuntu distributions, because after some "fixes" I lost all sound hardware or alsa, or even worse.

One interesting anomaly is that when Ubuntu starts, during boot up I get clicks from the sound system speakers.  This is after initial POST, and during the actual booting process.

This is so frustrating, as I said before.  Nothing I've done gets sound to work.  I wasted days trying.  It's not like my sound hardware is unique.  So, I'm tired and am looking for a real working solution, not some adventure into convoluted fixes that don't fix anything and break more more that they fix.

Thanks in advance for any constructive, hopefully, definitive solution.  Or at the very least a simple explanation of why, what I assume to be fairly standardized sound hardware, should not work on my pc.  This isn't the dark ages of Linux, where some hardware could be a real challenge.

I'm hoping that someone has finally solved, what from Google searches appears to be a prevalent problem now, for similar hardware setups.  My sound hardware info is as follows:

I have an ASUS P5N-EM HDMI motherboard with sound identified by the manufacturer as: 

Realtek ALC883 8-channel CODEC, Supports S/PDIF out interface, Supports jack-detect and Anti Pop Function, Supports VISTA Premium OS

aplay -l displays:

rjbm@asus-p5n-em-umd:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC883 Digital [ALC883 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

The audio section of lspci -v is as follows:

00:09.0 Audio device: nVidia Corporation MCP73 High Definition Audio (rev a1)
	Subsystem: ASUSTeK Computer Inc. Device 829f
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
	Memory at efff4000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: <access denied>
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

End Hardware Description.

---

### Post by pdaalder on 2011-02-16
Just spend 2 days to understand the problem. no luck. I understand your frustration.

I hope somebody has some clues. Exhausting to spend hours/days to get some basic functionality to work

---

