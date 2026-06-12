---
title: "No Sound / Trouble with Sound Cards"
date: 2009-07-03
forum: Multimedia Software
---

### Post by beartofear on 2009-07-03
Hi everyone I need a little help with a lack of sound issue.

I installed Kubuntu on Dell Optiplex 960 and haven't had sound since installation.

In Windows I'm told I have a SoundMax Integrated Digital High Definition Audio.

When I tried to use the sound solutions guide I get the following:

aplay-1
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: HDA Generic [HDA Generic]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

from the lspci -v 

00:1b.0 Audio device: Intel Corporation ICH10 HD Audio Controller (rev 02)
        Subsystem: Dell Unknown device 0276
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at febdc000 (64-bit, non-prefetchable) [size=16K]


Frankly at this point I'm stuck (and I'm a noob).  I could really use some help here.

-Josh

---

### Post by philcamlin on 2009-07-03
sudo apt-get update 

sudo apt-get upgrade

does that get sound to work ?

sometimes you have to upgrade to get it wo work cause mine had to

---

### Post by beartofear on 2009-07-03
I have done both and this didn't fix the problem.

-Josh

---

