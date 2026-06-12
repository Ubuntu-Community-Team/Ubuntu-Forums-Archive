---
title: "Not so smooth video and sound breakage"
date: 2008-07-19
forum: Multimedia Software
---

### Post by Phastor on 2008-07-19
Well I finally did it.  I switched over to Ubuntu as my main OS.  However I'm having a few little annoyances along the way with video and sound.  Here are my system specs.

AMD Athlon 64 3500+ on a Gigabyte K8N board
nVidia GeForce 6600GT
1.5GB RAM

My video experiences has been less than par with not so crisp movement in Totem and choppy video in flash videos such as YouTube.  I'm also getting the oh-so wonderful choppy scrolling in Firefox.  These are symptoms I'm used to seeing in Windows while using generic drivers and not official ones from nVidia.  However, this is not Windows so I'm completely stumped on what may be causing these.

On the audio side of things, my sound likes to cut out and stop working on me occasionally.  Sometimes it will cut out completely, or cut out only on certain apps.  I have seen this happen after World of Warcraft crashes (still haven't gotten it tuned in yet.  I'll be making another post about this elsewhere), then sound from flash videos doesn't work.  Sometimes when I am running Banshee I will get the same thing.  The sound will not come back until I have rebooted or restarted Xserver.

Along with any suggestions on how to fix these problems, I'm also looking for some advise in optimizing my sound and audio settings.  Any help will be greatly appreciated.

---

### Post by Phastor on 2008-07-19
Sorry for the bump, but it got knocked back three pages without a reply and I'd really like some help on this if anyone can.

---

### Post by xc3RnbFO8P on 2008-07-19
Did you enable the restricted driver
in System> Administration> Hardware Drivers ?

---

### Post by Phastor on 2008-07-19
I did.

---

### Post by xc3RnbFO8P on 2008-07-19
Did make some hardware changes, processor?

---

### Post by Phastor on 2008-07-20
I'm sorry, I'm not sure if I understand that question fully.

---

### Post by Phastor on 2008-07-22
Well here's an update.  I read about and installed the nvidia-glx package and that pretty much solved all my issues.  Upon first installing it I noticed that it made the title bars on all windows go away, however this was fixed by turning off desktop effects.

Aside from that little glitch, my movies are playing smoothly, scrolling in Firefox is no longer choppy (still not 100% smooth), and I managed to get WoW running smoother than it does in Windows with these drivers.  However I'm still having problems with Flash videos.  They could still be smoother, and they are incredibly bad when played in full screen.

Still having issues with audio as well.  I think I have narrowed it down whenever I play my music.  Banshee and Totem both seem to kill sound.  They play the music fine, but sound for everything else dies, even after closing the music apps.  The only way I can bring the sound back is by rebooting.

---

