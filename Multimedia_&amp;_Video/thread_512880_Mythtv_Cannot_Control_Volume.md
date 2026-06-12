---
title: "Mythtv Cannot Control Volume"
date: 2007-07-29
forum: Multimedia &amp; Video
---

### Post by gearshifter on 2007-07-29
The volume control in MythTV is not working.

It worked prior to a Motherboard/RAM/CPU change today.  All the sound settings look to be alright because sound is working and controls on my keyboard are doing their job as well.

The sound on myth works just volume control and mute no longer work.


Any ideas?

Thanks,
Jason


edit:  PCM and master are the only mixer controls i can select.  In voleume control from the task bar, the name of the mixer that changes audio volume is called "front" and i dont see a pcm option in edit>preferences...


Master doesn't exist either.

---

### Post by HyperY2K on 2007-12-30
I've got the same issue. I cannot control my volume within mythtv, in the normal gnome desktop volume control works...

Any suggestions?

---

### Post by joes_meat on 2008-04-29
That makes three!

Volume bar goes up and down, but the sound stays the same.

---

### Post by joes_meat on 2008-04-29
Fixed: Changing Mixer Device from /dev/mixer to ALSA:default fixed the problem.

Fresh install of Mythbuntu 8.04

---

### Post by gearshifter on 2008-04-30
you can actually modify the name of the volume control inside myth.  Just change the name to the control you use in gnome to change volume.

---

