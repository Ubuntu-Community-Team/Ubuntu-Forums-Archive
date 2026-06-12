---
title: "Video Help Please"
date: 2007-05-21
forum: Multimedia &amp; Video
---

### Post by LGer on 2007-05-21
I'm sure that you'll need more information but to start I'll explain the problem.... If I do a "cat /dev/video0 > test.mpg" my video card works fine. I can get tv with "mplayer /dev/video0" and it looks just fine. MythTV,  XawTv, and TVTime won't run. None of them see my capture card. TVTime gives me the message that it can not open the capture device /dev/video0, XawTv just times out and does nothing, and MythTV sees the card but won't accept it. My capture card is a Hauppauge 150PVR and my video is on board Nvidia. Thanks....

---

### Post by gwoodard on 2007-05-21
Just stick to mplayer since it isn't giving you problems

---

### Post by vigleik on 2007-05-21
> **gwoodard said:**
> Just stick to mplayer since it isn't giving you problems

That's not really helpful, as MythTV has a *lot* more functionality than mplayer. I think the fact that xawtv and tvtime won't work is normal, but MythTV really should work. My guess is that you didn't set up MythTV correctly. Poke around in mythtv-setup and see if you set the right input for your 150pvr. I think you both have to specify something like "Tuner 1" and "/dev/video0".

If it still doesn't work, start mythbackend and mythfrontend from the command line and try to watch live TV. The error messages you get should give you some insight into the problem.

By the way, I'm amazed at how much easier it is to set up MythTV now than it was a couple of years ago. The guide at [https://help.ubuntu.com/community/MythTV](https://help.ubuntu.com/community/MythTV) really makes the whole experience much less painful. If nothing else works I'd consider a fresh install using that guide.

---

### Post by newlinux on 2007-05-22
> **LGer said:**
> I'm sure that you'll need more information but to start I'll explain the problem.... If I do a "cat /dev/video0 > test.mpg" my video card works fine. I can get tv with "mplayer /dev/video0" and it looks just fine. MythTV,  XawTv, and TVTime won't run. None of them see my capture card. TVTime gives me the message that it can not open the capture device /dev/video0, XawTv just times out and does nothing, and MythTV sees the card but won't accept it. My capture card is a Hauppauge 150PVR and my video is on board Nvidia. Thanks....

I assume you are using Feisty (Ubuntu 7.04)? How did you try setting up the card in MythTV. It should be as an Mpeg encoder card. What you say it won't accept it what do you mean?

Also, unless something has changed recently, tvtime does not work with hardware encoding cards.

---

