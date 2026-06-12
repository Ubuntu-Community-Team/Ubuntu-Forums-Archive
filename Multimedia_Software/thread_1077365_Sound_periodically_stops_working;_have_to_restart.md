---
title: "Sound periodically stops working; have to restart"
date: 2009-02-22
forum: Multimedia Software
---

### Post by sondosia on 2009-02-22
Title says it all. About once a day, ALL the sound on my computer stops working and I have to restart the system to get it back. If I start Amarok during this period, I get a "xine unable to initialize audio drivers" message. Anybody know what's going on?

---

### Post by tamman2000 on 2009-02-22
I don't have a fix for you.  But I have the same problem.

Instead of restarting you should be able do a```
sudo lsof |grep pcm
``` and then kill -9 everything that comes up.  After that you need to restart ALSA ```
sudo /etc/init.d/alsa-utils restart
```

I got this from [http://andytseng.com/?p=84](http://andytseng.com/?p=84)...

I was wondering if you could provide some details about your installation of ubuntu so perhaps similarities between our machines could help isolate the source of this problem.  

My machine was originally a 6.10 machine and it has been through all of the upgrades along the way to 8.10.  Somewhere along the way (either 7.10 or 8.04, I can't remember) I had some problems with audio, which as I recall were related to pulseaudio.  I had to change something to get audio working on my machine, but sadly I can't remember what that was...

Does any of that sound familiar to you?

If anyone who understands linux audio could help us out that would be great.  I can post any info about my system that could help, as long as you tell me what you need to see, and how to get that info.

-Tamman2000

---

### Post by sondosia on 2009-02-22
Thanks; I'll try that next time this sound thing happens.

I originally had 7.10, I think, and then upgraded to 8.04 and 8.10. I'm not sure when this problem began, but it definitely started with the 8.** systems. I've always had sound problems in Amarok, but they used to be confined to just that application and restarting it solved the problem. Now it's a system-wide thing.

Other than that, I don't think I had any other significant audio problems...definitely not something like yours where something had to be reconfigured. But it sounds like we both started having the problem at around the same time.

---

