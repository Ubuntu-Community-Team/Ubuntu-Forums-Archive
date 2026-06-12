---
title: "Still more problems. I am about ready to switch to... dare I say it?"
date: 2009-04-29
forum: Multimedia Software
---

### Post by The_Real_Anna on 2009-04-29
Since my upgrade to Jaunty did not work out (too many problems). I went back to my old tried and true: Hardy Heron, then upgrade to Intrepid Ibex (I <3 Intrepid). But lo and behold, I am still having problems.

Everything went fine. But after installing updates to Firefox and such (the Update Manager Gods told me so) I now have problems with sound and video. Problems I have never had before.

1. No sound when I play online videos. Sometimes I have sound, but most times than not I don't. And yes I have checked my sound settings and ect.

2. Videos tend to start and stop. WTH?

3. Firefox issues. Firefox hangs up and freezes. I have to force quit, THEN go into System Monitor to actually end Firefox.

---

### Post by khelben1979 on 2009-04-29
If you go more in detail and explain exact which applications which don't work well and what video formats which works bad, then there will be easier to help you out. ;)

I think it doesn't really matter what version of Ubuntu you are using in the long run. Just try to understand your system and how it works and go from there. Have patience.

If the web browser works bad, figure out what web techniques which is being used on the web sites and make your conclusions from there and ask if you're uncertain on what Linux components which must work for different tasks such as flash contents or encapsulated video clips.

Also, using many Firefox addons can cause the browser to be unstable.

If you are ready to give up on Ubuntu, look [here]("http://en.wikipedia.org/wiki/Comparison_of_Linux_distributions") for further alternatives if you still want to run Linux.

---

### Post by The_Real_Anna on 2009-04-29
I have barely any add-ons with Firefox.

---

### Post by khelben1979 on 2009-04-29
> **The_Real_Anna said:**
> 2. Videos tend to start and stop. WTH?

3. Firefox issues. Firefox hangs up and freezes. I have to force quit, THEN go into System Monitor to actually end Firefox.

Have you tried to download the flash player from the Adobe website instead of installing it from within the Ubuntu system?

Also there might be a problem with your video drivers. Open source video drivers is always slow. I would recommend that you take a look at your sound settings with [alsamixer]("http://en.wikipedia.org/wiki/Alsamixer"). And if it isn't installed:
```
sudo apt-get install alsamixer
```

A quick way of killing GUI:s is by using the [xkill]("http://en.wikipedia.org/wiki/Xkill") command, I think you'll like it. Just type the command from some execute command prompt from either the system menu bar or from a text shell such as [xterm]("http://en.wikipedia.org/wiki/Xterm") or similiar. Sometimes it's not enough to kill it entirely and that's the only negative drawback I can think of using the command right now.

---

### Post by ausmuso on 2009-04-29
Have you ever considered that the underlying problem may not be with Jaunty, or with Intrepid, but with the fact that you tried to do an upgrade?

I have tried upgrades with several distros and it's never worked for me. Something always gets broken in the translation.

My suggestion would be to have a cup of coffee end a good cry, reformat your partitions and start from scratch with a clean install. You may find that most of your problems have disappeared.

You may think it takes longer that way but you avoid a lot of hassles!

---

### Post by khelben1979 on 2009-04-29
> **ausmuso said:**
> Have you ever considered that the underlying problem may not be with Jaunty, or with Intrepid, but with the fact that you tried to do an upgrade?

I have tried upgrades with several distros and it's never worked for me. Something always gets broken in the translation.

Upgrades works pretty good with Debian and never forces a user to do a complete reinstallation.

> 
My suggestion would be to have a cup of coffee end a good cry, reformat your partitions and start from scratch with a clean install. You may find that most of your problems have disappeared.

You may think it takes longer that way but you avoid a lot of hassles!

And considering if Ubuntu is the right choice, hmm..

---

### Post by Cresho on 2009-04-29
I ran into lots of problems myself.  I went back to hardy heron.

FLash was broken because it played like 5fps, etqw was slow, other than that, everything was fine.

I'll wait for the next LTS.

---

