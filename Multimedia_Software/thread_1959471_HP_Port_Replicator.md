---
title: "HP Port Replicator"
date: 2012-04-15
forum: Multimedia Software
---

### Post by djheadley on 2012-04-15
I'm running 10.04 on an older Pavillion dv6000 that has lost the on-board sound system.  I bought an HP Port Replicator (part # nk398aa) - I also needed more usb ports.  Everything works except the sound. The sound does work in Vista. 

I would like to fix this without having to do a re-install so close to 12.04 release.  Any suggestions?

---

### Post by BicyclerBoy on 2012-04-16
How have you determined the on-board sound is missing ?

aplay -l
lsmod | grep snd

Install pavucontrol & have a go at finding/selecting as default an audio device.

---

### Post by djheadley on 2012-04-19
I ended up doing a re-install because I messed things up royally.  

The Port Replicator works perfectly now.  I do have to keep the volume control turned way down, especially when using headphones.

Thanks anyway :-)

---

