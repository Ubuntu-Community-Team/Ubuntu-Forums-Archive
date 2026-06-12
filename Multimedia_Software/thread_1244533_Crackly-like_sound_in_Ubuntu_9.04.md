---
title: "Crackly-like sound in Ubuntu 9.04"
date: 2009-08-19
forum: Multimedia Software
---

### Post by Lightning Jim on 2009-08-19
Just recently I muted my sound via the volume control system tray and later brought it out. Since then ALSA has been playing crackly-like sound when it's playing a sound. OSS was doing fine until recently also.

Here's my ALSA Info script if it helps:
[http://www.alsa-project.org/db/?f=21c289a8aadc2d00ba051ca5994d113e6f5cd2d5](http://www.alsa-project.org/db/?f=21c289a8aadc2d00ba051ca5994d113e6f5cd2d5)

Note: Totem plays fine and the system works fine in Windows also.
Also Ubuntu 9.04 x64.

Update: I started jackd (after configuring it) and OSS is back. ALSA still doesn't work.
Update 2: Autodetect seems to default to ALSA as I get the crackly-like sound then also.

---

### Post by haaxerei on 2009-08-19
What Kernel do you use?

i had also some problems with the sound and an upgrade to the kernel
2.6.28-14-generic
helped...

---

### Post by Sam Lars on 2009-08-19
Check your PCM level in the alsa mixer. If it's all the way down, it tends to just play crackles and pops.

---

### Post by Lightning Jim on 2009-08-19
> **Sam Lars said:**
> Check your PCM level in the alsa mixer. If it's all the way down, it tends to just play crackles and pops.

That did it. Thanks.

I don't know how the PCM level got turned down as I didn't do it myself.

UPDATE: Now I can't hear anything played in Firefox or MPlayer. VLC and Totem I can hear.

---

### Post by Lightning Jim on 2009-08-20
I think I finally fixed it I added the options of the proper module to the alsa-base.conf as specified in the [SoundDebugging]("https://help.ubuntu.com/community/SoundTroubleshooting") page (exactly that since I have a newer version of the same audio card). After restarting ALSA it worked.

---

