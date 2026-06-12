---
title: "Setting up MythTv and Plextor PX-M402u"
date: 2007-08-08
forum: Multimedia &amp; Video
---

### Post by feeman_4_life on 2007-08-08
Hi,

I've pretty much referred to every guide on the forums here, plus some additional ones on google.  However I am having an *extremely* difficult time getting this setup to work being a Ubuntu novice.
I went through the official Ubuntu MythTV guide, only to have the MythTv frontend not loading up on me.

I just want to record convert some VHS tapes to DVD, that's all.  I don't need to record tv (not that my plextor convertx supports it).

Has anybody done this set up before and can give me some pointers?  Thank you very much! =)

---

### Post by tgm4883 on 2007-08-08
You don't need MythTV for what you want to do.  All you need to do (providing the  Plextor PX-M402u is supported in linux) is this.  I'm not sure what the plextor shows up as, but for my PVR-150 its 

cat /dev/videoX filename.mpg

---

### Post by feeman_4_life on 2007-08-09
Is that all there is to it?

I plug in my audio and SVideo to the source, and enter that command, and I record my audio and video?

---

### Post by tgm4883 on 2007-08-09
Can you post the output of this

ls /dev/video*

and also the output of this 

lspci

---

