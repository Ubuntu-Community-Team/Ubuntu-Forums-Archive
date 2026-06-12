---
title: "Sound buzzing and clicking"
date: 2008-08-10
forum: Multimedia Software
---

### Post by Vicker3000 on 2008-08-10
I have just recently installed Ubuntu on my system.  There seems to be some kind of conflict with my sound driver.  Sound plays back just fine, except that I can hear buzzing and clicking.  I'm using an old Soundblaster Live! sound card.  I'm also using an Nvidia 8600 video card.

---

### Post by Mzungu666 on 2008-08-14
Oh yeah I have the same problem, haven't found the solution yet

---

### Post by entropius on 2008-08-15
I have the same problem too, using an integrated sound chipset (Nvidia) on an Asus motherboard.

Also possibly relevant is that the processor is a Phenom.

This happens for all sounds. Switching from PulseAudio to ALSA (and back) doesn't help.

I've read a report somewhere that this could be related to the new scheduler in 8.04, but want to exhaust all my other options before I recompile a kernel.

Any ideas?

---

### Post by markbuntu on 2008-08-15
One thing that causes this problem for a lot of people is that their microphone is not muted in the sound mixer or the mic boost is on.

---

