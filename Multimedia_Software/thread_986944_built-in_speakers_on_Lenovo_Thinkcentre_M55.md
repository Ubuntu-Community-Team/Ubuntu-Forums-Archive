---
title: "built-in speakers on Lenovo Thinkcentre M55"
date: 2008-11-19
forum: Multimedia Software
---

### Post by minaev on 2008-11-19
How do I enable the built-in speakers on Lenovo Thinkcentre? ALSA works fine through the headphones, but I can't send the output to the speakers. Any ideas?

Thank you.

---

### Post by minaev on 2008-11-19
The solution was found here:

[http://tlgu.carmen.gr/gnulinuxtips/GNU-Linux%20on%20the%20Lenovo-IBM%20ThinkCentre%20A55.html](http://tlgu.carmen.gr/gnulinuxtips/GNU-Linux%20on%20the%20Lenovo-IBM%20ThinkCentre%20A55.html)

I added the line

options snd-hda-intel position_fix=1 model=3stack

to /etc/modprobe.d/alsa-base, rebooted... But still no sound. Then I played a while with alsamixer, then tweaked aumix, and finally, it was working :)

---

