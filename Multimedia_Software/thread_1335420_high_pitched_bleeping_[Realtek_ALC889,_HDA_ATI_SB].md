---
title: "high pitched bleeping [Realtek ALC889, HDA ATI SB]"
date: 2009-11-23
forum: Multimedia Software
---

### Post by Thom- on 2009-11-23
Hello guys,

this problem just makes me crazy - i get headaches from that awful sound.

When the system doesn't transfer any sound to the soundcard after a few seconds a high pitched bleeping appears. It sounds like a very small dental drill. 
The sound stopps if i play something (e.g. TV -> mythtv or VLC or any system sound). The sound also stopps for a few seconds when i change anything in the mixer (lowering the level, muting something) followed by a quick, loud snap. 

I already muted any microphone inputs, but it didn't help.
My system is the standard system of a htpc 1,5 years ago (AMD 780g chipset (Gigabyte GA-MA78GM-S2H), AMD 4850e cpu), Ubuntu 9.10 
The problem stopped as i deleted the alsa packages (but I now have no sound). 
I have a win xp on my system, too... no problems there.

I would be very pleased if someone could help me with that problem.
Greetings
-Thom

---

### Post by Thom- on 2009-11-23
Well, if I had known, that one post in the ubuntuforums would help me that fast I could have avoided 2 weeks of headache.

Just ~2 hours after my posting i've finally found the solution:
the problem is the power saving mode of the sda-hda-intel module.

we have to change in the file */etc/modprobe.d/alsa-base.conf*  the last line:
```
options snd-hda-intel power_save=10 power_save_controller=N  
```

to

```
options snd-hda-intel power_save=0 power_save_controller=Y  
```

after an ```
alsa force-reload
``` the nasty noise will finally stop.

Unfortunately all powere saving functions related to the sound device will stop too, but i think its a price worth to pay for a headache free system ;)

At least my posting brought me luck to find the solution by myself. :D
I hope this will help someone in the future.

Greetings
-Thom

---

### Post by wandalalakers on 2009-11-23
I have a Realtek ALC662 and I have the same problem.  I'm going to try your fix.  Whenever the sound starts, I just lower my mixer volume.

---

