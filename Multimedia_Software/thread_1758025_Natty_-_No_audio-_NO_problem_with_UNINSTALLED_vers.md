---
title: "Natty - No audio- NO problem with UNINSTALLED version"
date: 2011-05-14
forum: Multimedia Software
---

### Post by teutara on 2011-05-14
Hi there,

I know there are so many threads with same outline, but the thing i am asking may be a clue to these ubuntu experts. My rig is Dell 4030, with Intel Hda (IDT) audio card embedded. When i try Natty(or the earlier versions) on USB thumb drive, everything is OK. Even the wireless connection is faster. 

When i install Natty (earlier versions are non-problematic) things get messy. Absolutely no audio, i tried several things (alsa doc thing, purging the driver etc..) but have no solution,

My question is(on windows i am able to do it) can i somehow get the driver from live version and use it on installed version ? 

Thank you in advance..

---

### Post by lidex on 2011-05-14
Interesting. You can run the alsa-info script on each version and we can compare results for a possible fix.
Run this command in a terminal:
```
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh 
```
Choose the upload option and provide a link for the output.
[Terminal="Applications->Accessories->Terminal"]

---

### Post by shademere on 2011-05-18
Hello, I'm having the same problems. Here is the output from the above command:

[http://www.alsa-project.org/db/?f=202583b266cdd2557d83e92437944a5e21476aca]("http://www.alsa-project.org/db/?f=202583b266cdd2557d83e92437944a5e21476aca")

Sound used to work after I installed Natty (the day it was released), but sometime down the road (maybe two weeks ago?) it stopped.

Cheers

---

### Post by shademere on 2011-05-19
I got it working.

---

### Post by Shevraar on 2011-05-28
> **shademere said:**
> I got it working.
I'm having the same problem... Could you please explain how did you got it working?? Thanks in advance! 
Shevraar

---

