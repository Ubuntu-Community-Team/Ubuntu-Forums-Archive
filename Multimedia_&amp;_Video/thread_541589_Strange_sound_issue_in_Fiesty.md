---
title: "Strange sound issue in Fiesty"
date: 2007-09-03
forum: Multimedia &amp; Video
---

### Post by skinnymonkey on 2007-09-03
I have two _completely_ different machines running Fiesty server w/ apache2, php5, mpd and mpc. That's it.

They are both being used as music players 24/7 for phone on hold and waiting rooms.

Sound works perfectly, and so does mpd.... for not a second more (or less) than 6 hours. :confused: MPD continues to play the music files and the machine still responds to everything, there's just no sound from the audio cards.. If I reboot or  simply restart mpd it works again for another six hours.

I've used the noapic boot option and I've disabled apic in BIOS. Also, all BIOS power saving features have been turned off. I've tried various versions of the kernel  (standard/server/gutsy) and different versions of alsa. Additionally I've disabled cron jobs in case something else was interfering. 

I have not been able to find any errors or info in the logs that look related.

My knowledge is at it's end as to why this would be happening. Any help is MUCH appreciated.

---

