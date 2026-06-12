---
title: "Sounds problems with HD audio :("
date: 2007-08-13
forum: Multimedia &amp; Video
---

### Post by eeeeepuk on 2007-08-13
Hi, everyone. I've just upgraded to a brand new computer and have all but finished setting Ubuntu up on it, but I'm getting the occasional sound problems which are keeping  me from dumping the old system permanently.

As Ubuntu Feisty didn't give me any sound out of the box, I've manually built Alsa with support for my sound card (a RealTek HD audio device). This works fine most of the time, but occasionally the sound will 'stick' - that is to say, the system will play the same half-second or so of sound over and over ad infinitum. I can normally stop the sound with "sudo /etc/init.d/alsasound stop", but any attempt to restart it just causes the same effect the next time the sound is played.

Though I've used Linux for a while, I've never had to do any debugging (it's generally all just 'worked' for me), so any help in how I even start tracking this problem down, let alone in fixing it, is greatly appreciated!

---

