---
title: "[SOLVED] Poor sound quality w/ HDA ATI SB AD198X"
date: 2008-12-27
forum: Multimedia Software
---

### Post by Piraja on 2008-12-27
Dear all,

I'm getting very bad audio playback quality with this setup: 

```
aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: SB [HDA ATI SB], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

From sudo lspci -v output:

```
Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
	Subsystem: Hewlett-Packard Company Device 3613
	Flags: bus master, slow devsel, latency 64, IRQ 16
	Memory at 94400000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [50] Power Management version 2
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

```

This is a brand new HP Compaq 6735S laptop, dual booting Windows Vista & Ubuntu Intrepid 64-bit. Sound is good in Vista, but in Ubuntu it gets distorted. Any suggestions?

Regards,

Piraja

---

### Post by Piraja on 2008-12-27
Even though I still hear some static noise listening to a certain Zappa recording,* it seems that the problem found its solution in the thread [HOWTO: PulseAudio Fixes...]("http://ubuntuforums.org/showthread.php?t=789578") &#8212; kudos to psyke83 for that!

*) This time I think it's the live recording (*Trance Fusion*) and not my equipment...

**Edit / Addition**: Better, but not perfect... Now Aqualung behaves badly: doesn't respond to pressing the "Stop" button, except with a delay, and then stifles when I touch GNOME's volume control. Yet, I can always use MOC as a gapless player. The situation is way better anyway now.

---

### Post by Piraja on 2009-01-03
The best of solutions and the easiest was yet to come: [adding just one line to the alsa-base file]("http://ubuntuforums.org/showpost.php?p=6488371&postcount=1293").

---

