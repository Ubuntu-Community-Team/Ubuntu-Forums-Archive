---
title: "Sound choppy after last wine update"
date: 2008-10-11
forum: Multimedia Software
---

### Post by tonark on 2008-10-11
Right after the last wine update (1.1.6) the sound in World of Warcraft is extremely choppy.  Other non-wine apps (such as Pandora in Firefox) are fine.   Anyone else notice this?  Any ideas how to fix it?

---

### Post by beg1689 on 2008-10-11
Same problem here, 1.1.6 has made my audio choppy with steam games. My suggestion is to revert to 1.1.5 for the time being.

---

### Post by spicydonuts on 2008-10-14
same exact issue

i've never had to downgrade, is there a process i should go through to make it clean and not mess anything up?

it worked so well before, i'll be sad if i can't get it back... (besides a couple glitches like no voice chat in steam, which i was hoping 1.1.6 would help with...)

anyone not having the stuttering sound problem?

i'm using alsa and pulseaudio (fixed) on ubuntu 8.04 x64
and latest nvidia drivers

---

### Post by Canislupus on 2008-10-15
Same issue here.

---

### Post by kostkon on 2008-10-15
Same for me. It's a regression and I want to believe that it will be solved in the next version.

---

### Post by markbuntu on 2008-10-15
Have you seen this:

[http://pulseaudio.org/wiki/PerfectSetup](http://pulseaudio.org/wiki/PerfectSetup)

There are directions for wine in there somewhere. Basically it says to start wine with 
```

padsp wine

```

and then tell wine to use OSS.

You can also edit the /etc/pulse/daemon.conf file to eliminate stuttering. At the end of the file are two lines like this:
```

;default-fragments = 5
;default-fragment-size-msec = 25

```
Change them to look like this :
```

default-fragments = 8
default-fragment-size-msec = 5

```
Save the file and restart Pulse Audio.

These are easy things to try as they can be easily changed back.

---

