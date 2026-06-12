---
title: "Audio resets master to 70% when switching between watching media and live TV"
date: 2008-05-11
forum: Mythbuntu
---

### Post by whosmatt on 2008-05-11
When switching between watching TV and videos, I often have to run alsamixer in a terminal window to get the master volume back up so that the output is similar to the other components in my system.  The volume control on my streamzap remote seems to control the PCM "fader" in alsamixer, which is fine, but I want the master to stay where I set it.  Is anyone else having this problem?

System is

Mythbuntu 8.04

lspci reports the audio controller as:

Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)

-Matt

---

### Post by wilberfan on 2008-05-12
I don't watch live TV with my Hardy Mythbuntu install, but I'm having this same problem when I watch any recordings I've made from 'live' TV.   (My volume resets to 69%.)

If I have recorded three shows, I'll have to get up and manually push the slider back up where I set it that last time in between the playback of each show...  :confused:

---

### Post by db260179 on 2008-05-13
You have to change the audio settings in mythtv.

Start mythtvfrontend, goto Setup, General, Page 3, change the default levels (default is 70%)

[http://mythtv.org/wiki/index.php/User_Manual:Detailed_configuration_Frontend#General](http://mythtv.org/wiki/index.php/User_Manual:Detailed_configuration_Frontend#General)

Hope this helps? 

> **whosmatt said:**
> When switching between watching TV and videos, I often have to run alsamixer in a terminal window to get the master volume back up so that the output is similar to the other components in my system.  The volume control on my streamzap remote seems to control the PCM "fader" in alsamixer, which is fine, but I want the master to stay where I set it.  Is anyone else having this problem?

System is

Mythbuntu 8.04

lspci reports the audio controller as:

Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)

-Matt

---

### Post by whosmatt on 2008-05-13
> **db260179 said:**
> You have to change the audio settings in mythtv.

Start mythtvfrontend, goto Setup, General, Page 3, change the default levels (default is 70%)

[http://mythtv.org/wiki/index.php/User_Manual:Detailed_configuration_Frontend#General](http://mythtv.org/wiki/index.php/User_Manual:Detailed_configuration_Frontend#General)

Hope this helps?

Absolutely.  And now I feel kind of dumb.

---

### Post by wilberfan on 2008-05-13
> **db260179 said:**
> 

Hope this helps?

Dude...  You *hope* this helps?!   Only, like, *completely*!

\\:D/

---

### Post by db260179 on 2008-05-13
:lolflag:

> **wilberfan said:**
> Dude...  You *hope* this helps?!   Only, like, *completely*!

\\:D/

---

