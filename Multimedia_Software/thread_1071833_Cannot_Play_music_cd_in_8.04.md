---
title: "Cannot Play music cd in 8.04"
date: 2009-02-16
forum: Multimedia Software
---

### Post by wah fun on 2009-02-16
I have installed ubuntu 8.04 as a guest OS on an xp box running virtualbox 2.0.6. I have set all the settings in virtualbox to enable audio. I have installed guest additions. Videos work fine with sound but I cannot play music cd's. I have tried all settings in sound preferences with no luck. 

Problem: after inserting music cd, rythmbox just pauses and never reads the cd (activity light just stays constant as if rythmbox cannot read the cd). Installed vlc but no help here either. Don't want to try too many programs until I get some valid input as to the possible problem.

System Info: Dell box with XP SP2, 2 GB ram (960 allocated to the ubuntu guest OS) running at 2 mhz.

Ubuntu has all updates.

So far, searches for a resolution have not turned up anything relevant. Your help would be appreciated. It would seem to me that since the movie videos play with sound that the music cd's would too.

Would really appreciate your input IF you have had the problem in the same scenario as I have explained AND you have resolved the problem.

Thx in advance for your willingness to help.

---

### Post by andrew.46 on 2009-02-19
Hi,

Seems a little odd. Have you tried accessing music cds from the commandline?

```
$ mplayer -cache 2048 cdda://
```

Worth a try?

Andrew

---

