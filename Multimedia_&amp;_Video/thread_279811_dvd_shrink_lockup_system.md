---
title: "dvd shrink lockup system"
date: 2006-10-18
forum: Multimedia &amp; Video
---

### Post by gargoyle on 2006-10-18
I just installed Wine and DVDshrink (Win version) and started to use it.

However I seem to be having a problem with the system locking up once DVDShrink starts to encode the dvd. It gets part way into the encode and thats it.

The whole thing locks up. Can not move mouse or use keyboard.
Nothing, have to hit system reset on computer.

I have installed VLC and dvd rom works to watch movies.

The system is ECS P4vxms ver 1.0
Radeon RV100 QV (Radeon 700/VE)
Intel P4 1.7GHz
512Mb Ram

Ubuntu Dapper Drake
Wine 0.9.9-ubuntu( downloaded and installed Synaptic)

Any ideas as what to check out?

---

### Post by an.echte.trilingue on 2006-11-05
I know this post is old, but maybe I can still help you.

I would bet euros to dollars that the problem is in your video card, especially if other things are causing the lock up.  I suggest you look up how to use this command:

```
sudo dpkg-reconfigure xserver-xorg
```

Also, I honestly do not understand why people prefer DVDshrink in wine to dvd::rip.  On the surface, dvdshrink is easier (and a bit faster), but wine adds such a layer of confusion that to me it is worth an hour of time learning to use dvd::rip than to try to track down all the issues wine can cause.  Also, dvd::rip gives you many more options.  If you haven't tried it, just install dvdrip with synaptic, and be sure to install both all of the required and the suggested packages, read the documentation [here]("http://www.exit1.org/dvdrip/") and rip away.

Take care,

-mat

Edit:  I am pretty sure that the Radeon 700 is very poorly supported in Linux.  That would explain your lock up.

---

