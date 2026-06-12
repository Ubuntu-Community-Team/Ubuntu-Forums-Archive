---
title: "subwoofer not working"
date: 2007-07-15
forum: Multimedia &amp; Video
---

### Post by rubengomes on 2007-07-15
--------------------------------------------------------------------------------

Hi all!!
I installed this week ubuntu 7.04 but I cant make my subwoofer work. Itried all like other foruns, messing in alsa, messing in alsamixer in terminal but nothyng.... any ideas??.
I have 5.1 sound system with nvidia nforce3 mobo.
Sory about my english...
Thanks

---

### Post by Turboaaa2001 on 2007-07-15
Have you tried going through the package manager ( System -> Administration -> Synaptic Package Manager) and searching for suround sound support? Also try another media player or check the media player settings?

I gotta go, I have more so I will be back.

---

### Post by rubengomes on 2007-07-16
I finnaly found a solution searching web... :popcorn:

Just made a file named .asoundrc and write inside:

pcm.!default {

type plug

slave.pcm "surround51"

slave.channels 6

route_policy duplicate

}


Then saved it in my home folder.
Fibnally I have 100% working sound with subwoofer :guitar:
I hope this helps many others!

---

### Post by rexxxlo on 2007-12-06
does this work ?    

how do you control the volume of the sub?

---

