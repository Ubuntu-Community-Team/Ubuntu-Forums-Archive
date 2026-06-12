---
title: "Karmic Not Detecting Laptop Speakers?"
date: 2009-11-05
forum: Multimedia Software
---

### Post by threetwoone on 2009-11-05
After a clean install of 9.10 my sound stopped working through my laptops speakers (the headphones are fine) (it's an Asus g1sn-b1).  It has an "Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)", using the alc1200 chipset.

Ive tried:

[LIST]
[*]editing /etc/modprobe.d/alsa-base.conf and adding "options snd-hda-intel probe_mask=1" (it supposedly fixed similar issues for the alc1200 with alsa 1.0.17ish) however it had no effect.
[*]I also tried "options snd-hda-intel model=xxx" using a variety of similar Asus models.  /usr/share/doc/alsa-base/driver/ALSA-Configuration.txt.gz does not list anything for the alc1200.
[*]made sure nothing was muted in alsamixer
[/LIST]
Messing around in the alsamixer I tried to disable headphones and my sound stopped altogether (obviously).  But When I looked up at the sound icon on the toolbar it was greyed out, when I mute just headphones in the alsamixer the sound for my whole system gets muted!  I.E. it isn't even trying to play through something else.  So I think that my speakers have not been detected.  Also when I select headphones from the list in sound preferences is mutes "front" and I lose all sound (again suggesting it things that there is only headphones?!?!).

Does anyone know what I should do to try and fix it?  Any help would be appreciated.

---

### Post by threetwoone on 2009-11-21
There is no "front speaker" device like there was in 9.04.  So it does look like it isn't detecting my speakers.  Does anyone know how to go about fixing this?  I also managed to mess up pulseaudio and I had to remove it but now I'm back to where I was before.
Again any help would be appreciated.

---

### Post by threetwoone on 2009-12-25
Fixed...wow that took me a long time.  All that needs to be does is add "options snd-hda-intel model=3stack-dig" to /etc/modprobe.d/alsa-base.conf.  I will get this added this to [http://ubuntuforums.org/showthread.php?t=1043568](http://ubuntuforums.org/showthread.php?t=1043568).

---

