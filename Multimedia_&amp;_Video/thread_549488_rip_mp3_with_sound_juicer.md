---
title: "rip mp3 with sound juicer"
date: 2007-09-12
forum: Multimedia &amp; Video
---

### Post by Chymera on 2007-09-12
i already succeeded to rip and encode files to the mp3 format witrh grip. However i find grip ugly and would prefer to use sound juicer.
I followed the instructions under "help" and created a new profile. But, even after restarting sound juicer, i don't see it in my list. I tried to modify the entry of an already existing profile and it disappeared too. 
Yes, i did click the "active" box.

---

### Post by Chymera on 2007-09-19
suggestions?

---

### Post by blueturtl on 2007-09-20
Using either Synaptic or apt-get install the following package:

gstreamer0.10-plugins-ugly-multiverse

After this open Sound-Juicer, go into Edit->Preferences and at the bottom of the dialog where it has a selectionbox for output format you should now find the preset: 'CD Quality MP3 Audio'. Select and hit apply and off you go!

---

### Post by wormser on 2007-10-10
> **blueturtl said:**
> Using either Synaptic or apt-get install the following package:

gstreamer0.10-plugins-ugly-multiverse

After this open Sound-Juicer, go into Edit->Preferences and at the bottom of the dialog where it has a selectionbox for output format you should now find the preset: 'CD Quality MP3 Audio'. Select and hit apply and off you go!

Installing gstreamer0.10-plugins-ugly-multiverse made it work for me.  Thanks.

---

