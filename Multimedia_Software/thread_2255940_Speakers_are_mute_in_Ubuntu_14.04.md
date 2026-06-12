---
title: "Speakers are mute in Ubuntu 14.04"
date: 2014-12-08
forum: Multimedia Software
---

### Post by ernsttremel on 2014-12-08
My speakers are displaying music and sound correctly in Windows XP and in Windows 8.1.

In Ubuntu 14.04 however I can not hear anything through the speakers. When I navigate to pulse audio volume control (pavucontrol) "Playback", I get to see every level rashes, but no sound. Whether I test noise test or if I play any sound files under different players.

I think there must be somewhere a command in Ubuntu 14.04 to set the speakers to be heard, will say to unmute them.

But I do not know where?

---

### Post by ajgreeny on 2014-12-08
Go to the output devices tab of pavucontrol and see if that shows the level of **Analogue output** and **Headphones** as mine does.  That may be where the volume is set too low, not in playback.

---

### Post by ernsttremel on 2014-12-09
In pavucontrol shows the level of **Analogue output** and **Headphones. And I set the volume higher. But still the speakers are mute. Is there any terminakl command to fix the problem?**

---

### Post by ajgreeny on 2014-12-09
I'm sure there must be a terminal command but I don't know it.  You could, however, check using **alsamixer** in terminal to check that the levels of outputs are not set too low or muted in that.

Move from slider to slider, and raise and lower levels with the cursor keys;
Mute and unmute with the "M" key.
Tab will move you from "playback" to "capture".
Esc will save and exit.

---

### Post by ernsttremel on 2014-12-09
Thank you.
But this didn't solve the problem. My speakers still are mute.

---

### Post by ernsttremel on 2014-12-09
Do you think that my soundproblem could be solved if I install Ubuntu 14.04 totally new, will say after having fomatted the hard disk drive where Ubuntu 14.04 had be installed before?

cf. [http://forum.ubuntuusers.de/topic/probleme-beim-update-von-ubuntu-13-10-auf-14-0/](http://forum.ubuntuusers.de/topic/probleme-beim-update-von-ubuntu-13-10-auf-14-0/)

---

### Post by Yellow Pasque on 2014-12-10
> Do you think that my soundproblem could be solved if I install Ubuntu 14.04 totally new
Try it on a DVD-R or USB stick before overwriting your install.

You may want to give some more info and tell us what device you're trying to use: [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)

---

