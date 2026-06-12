---
title: "Help needed with PNY NVS 440 (nvidia) quad head ... kernel panics"
date: 2007-05-04
forum: Multimedia &amp; Video
---

### Post by nvs440 on 2007-05-04
I am new to ubuntu, but very experienced with Unix.

I have a shuttle sd11g5 with a PNY NVS 440 quad-head card in the 16x pciE slot.  It has two nvidia GPUs on it.

Booted off of 7.04 install disc, and it won't even start - I choose install, and it starts to boot and just hangs.

So then I got the alternate CD and successfully installed using text mode.

The resulting system cannot boot at all - using generic or recovery kernel.  When I try to boot it just kernel panics at different spots.  Caps lock key won't toggle LED anymore, so it is definitely hard locked.

So I booted off the alternate CD again and went into rescue mode.  I got a shell prompt and ran:

sudo apt-get install nvidia-glx nvidia-kernel-common
sudo nvidia-xconfig

and then rebooted.  Still will not boot - just kernel panics.  So at this point there is no getting into the system at all - the kernel panics almost immediately so I cannot get a shell unless I go into rescue mode.

I have no idea where to go from here.  Help ?

---

### Post by nvs440 on 2007-05-04
Wow this is a busy forum ... bump.

---

