---
title: "Speakers REALLY low"
date: 2009-07-04
forum: Multimedia Software
---

### Post by Swooper86 on 2009-07-04
Installed Kubuntu on my Dell Inspiron 1520 laptop recently. One thing that bugs me is that the speakers sound MUCH lower than before, when I had windows on it. If I'm listening to a low track (like classical/filmscore music tends to be) with the computer on my lap, I can just barely hear it even if the system sound is at 100%, that's how low it is. Anyone know a fix to this? I'm thinking there has to be a command I can type in to force the speakers to be a little louder, right?

---

### Post by Swooper86 on 2009-07-05
I hope I'm not breaking any forum rules by bumping this a bit, but it's off the first page and no replies :( Anyone?

---

### Post by raboofje on 2009-07-05
Is it an intel card? Did you see [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto) ?

---

### Post by PARO on 2009-07-05
I've had this happen to me a couple times on Gnome when i installed or first used some new a/v software. The master volume stayed maxed out, but the PCM level became set really low. Not sure why, but I guess it wouldn't hurt to check your mixer and make sure thats not the case for you too. Good luck.

---

### Post by ddrichardson on 2009-07-05
I've a Dell 1545 and for reasons I haven't fathomed, the highest volume in Linux is always whatever Windows had last.  So if Windows was at 50% - that's the highest volume in Linux.

---

### Post by raboofje on 2009-07-06
A quick google ( [http://www.zerobeat.in/debian-gnulinux-on-dell-inspiron-1520/](http://www.zerobeat.in/debian-gnulinux-on-dell-inspiron-1520/) )  confirms this is an intel HDA card. Following the docs at [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto) should probably take care of the problem.

---

