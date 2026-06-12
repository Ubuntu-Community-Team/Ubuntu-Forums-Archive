---
title: "No Sound (Most the time) and linux header issue"
date: 2007-05-29
forum: Multimedia &amp; Video
---

### Post by twistedtwig on 2007-05-29
Hi all,

I am having trouble with getting sound to work (like others).. I have a creative Audigy 2 ZS (emu10k1 driver, I think) sound card.

I have looked at a lot of threads, I have tried alsamixer.  I have been working through this

[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

guide which seems cool but have hit a problem.  I worked all the way through to:

Using alsa-source

and did the following command:

sudo apt-get install build-essential linux-headers-$(uname -r) module-assistant alsa-source

but I got the following and slightly worrying output:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package linux0headers-2.6.20-16-generic

```

I don't know where to go from here really.  Googled the last line but got nothing at all.

Any thoughts, suggestions, ideas?

Thanks all :)

---

### Post by twistedtwig on 2007-05-29
got the sound working with this link

[http://ubuntuforums.org/showthread.php?t=457761&highlight=audigy](http://ubuntuforums.org/showthread.php?t=457761&highlight=audigy)

but the no headers bit worries me

---

