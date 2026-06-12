---
title: "Can't rip CDs in Kubntu 8.04"
date: 2008-09-21
forum: Multimedia Software
---

### Post by bowens44 on 2008-09-21
I am trying to rip CDs to MP#s in Kubuntu 8.04. Sound Juicer doesn't give me the option for MP3 in the output format drop down. K3B give me an error that says command failed then lists the lame command and error while encoding track one.

I have the gstreamer good , bad and ugly plugins installed.

thank you for in advance....

---

### Post by bowens44 on 2008-09-21
Ok , I this is now working.
Solution:

sudo apt-get install gstreamer0.10-plugins-ugly-multiverse

---

