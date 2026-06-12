---
title: "Assign multimedia key to ONLY Master"
date: 2010-12-07
forum: Multimedia Software
---

### Post by casperlingus on 2010-12-07
I just installed a 5.1-capable sound card in Ubuntu 10.04, and was pleasantly surprised that I could select Analog5.1 from the sound menus and all the speakers produce sound.  

I have the gnome-alsamixer installed, and have found the "sweet spot" for Master, PCM, Front, Rear, and Ctr/Sub.  Playing music sounds just right when I set everything manually like this. 

However, adjusting the volume with the multimedia keys is complete garbage.  It jumps all over the place, moving PCM-Front-Rear-Ctr/Sub all at once, usually only max or nothing, and actually doesn't even change the Master at all.  Sometimes it sets master to mute, or moves the "side" channel (whatever that does).  Basically my multimedia keys are completely useless.

I can't find anywhere that allows me to lock/freeze some channels, and select which channels to adjust with the MM keys.   What am I missing?  Is the pulseaudio misbehaving?  Would I be happier without pulseaudio?  What config files/options need to be changed.

Thanks,
Casper

---

### Post by casperlingus on 2011-02-13
BUMP!  The audio control is **completely** broken and unusable.  There's gotta be a way to turn off whatever stupid process keeps messing with my volume control!  I tried removing pulseaudio, but that wants to remove everything on my computer.  

I have made a custom python script which explicitly reads and sets the volumes using "amixer", and it **does** in fact change the volumes **for 1/10 of a second** before whatever other process changes the mixers to garbage (usually master->0, pcm->100%, and randomly for everything else).  All I want to do is kill whatever is doing this!

Occasionally this process does disappear, and I can control the volumes without interference, which is such pure heaven (my script is perfect, if this other process wasn't interfering).  Then I reboot and it comes back.  ARGH

---

