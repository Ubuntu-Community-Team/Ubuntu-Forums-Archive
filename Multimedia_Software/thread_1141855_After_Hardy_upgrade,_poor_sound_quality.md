---
title: "After Hardy upgrade, poor sound quality"
date: 2009-04-28
forum: Multimedia Software
---

### Post by alnilamski on 2009-04-28
Hey all,

I recently upgraded all the way from Dapper to Hardy. Technically, it was a clean install.

So I don't recall ever having done anything special in Dapper for my sound card, and the sound quality was always pristine. By the way, I have a:
```
05:04.0 Multimedia audio controller [0401]: Creative Labs SB Audigy LS [1102:0007]
	Subsystem: Creative Labs Unknown device [1102:1007]
	Flags: bus master, medium devsel, latency 64, IRQ 16
	I/O ports at d8a0 [size=32]
	Capabilities: [dc] Power Management version 2

```

So ever since I installed hardy heron, the sound works, but it sounds really noticeably bad, with clipping - as if I had crappy tiny speakers that I was overdriving, but the speakers themselves still work great on my alternate XP boot.

I use XMMS to listen to music, if that helps, but the sound quality problem occurs regardless of program.

Also, it now gets mad when I try to have two programs using sound at once (i.e. Gmail's chat beeps and music), which it never used to mind in Dapper, but my main concern is the sound quality.

Can anyone help? Thanks!
-Alnilam

---

### Post by hansdown on 2009-04-28
Hi alnilamski.

When you click system> preferences> sound> devices the screen looks similar to this.

You can change the settings and test how they work.

---

### Post by markbuntu on 2009-04-28
Welcome to the now...
To get you sound dialed in in Hardy, which is way different than Dapper, read this:

[http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506)

If your sound is still scratchy or stuttering you can edit these lines in the file /etc/pulse/daemon.conf to look like this

```

default-fragments = 5
default-fragment-size =25

```
There are also some sound cards/chips that can only be fixed with an ALSA upgrade so you may want to consider that if this does not work for you.

If you are still having problems then you need to go here

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

### Post by alnilamski on 2009-04-30
Thanks, that guide worked great except that my sound only works if I ignore their step about setting Preferences>Default Sound Card to CA0106 (my card) instead of PulseAudio. I can use sound in multiple applications at once and everything. Also, I found that sound quality gets better if I turn the system volume control DOWN and my speakers UP to compensate.

Thanks again!
-alni

---

