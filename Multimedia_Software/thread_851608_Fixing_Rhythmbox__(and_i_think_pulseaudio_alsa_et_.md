---
title: "Fixing Rhythmbox  (and i think pulseaudio alsa et all)"
date: 2008-07-06
forum: Multimedia Software
---

### Post by FishRCynic on 2008-07-06
i have found my answer.

as the playback freeze and stuttering etc appeared to me to be an interrupt issue of some sort i i have played hard with this.

by removing the following input packages

xserver-xorg-input-elographics
&
xserver-xorg-input-wacom

which also removes the meta-package

xserver-xorg-input-all

most of my sound issues are gone.

as i do not have those input devices this does not bother me

and the sound is superb

i hope this helps others.

---

### Post by s3a on 2008-07-07
I've been having choppy sound when I listened to music through totem or Rhythmbox due to high CPU usage but I have a 3 Ghz Pentium 4 CPU with 1 GB RAM running in Ubuntu 64-bit. IS this what you're refering to? I'm asking because I want to know if following your instructions will help me and don't want to do something for nothing.

Thanks!

---

### Post by FishRCynic on 2008-07-07
yes - even after following the instructions from this forum and others
i still had choppy sound to the point of "pausing" and timing out.
this has reduced it to almost non-existant - unless under heavy load
in my case i do not have either of the devices i removed,
so i do not need them loaded.  This may have something to do with
the multi-device driver for multiple kbds and mice but removing these
two solved my problem.  It even works again today :-)

---

### Post by mr.vanker on 2008-12-21
[FONT="Arial"]Alright, I did what the first user suggested... I uninstalled them with Synaptic Package Manager (or whatever it's called). That did help. But I still get some choppiness. Mostly only when I am on a webpage, and I scroll down (I use the arrow keys for scrolling) for a few seconds. I don't think that my CPU gets overloaded from just that!

Any help appreciated! :guitar:[/FONT]

---

### Post by m4lte on 2009-01-07
I removed the packaged as recommended in the first post. Still I occasionally get choppiness, up to the point where playback actually stops. The CPU is not particularly busy on those occasions.

Any ideas on how to solve the issue?

---

### Post by ian_hawdon on 2010-01-12
I can't do what the first user suggested, as I actually use the Wacom driver, and it took me ages to get the damn thing working! (my pad is actually an n-trig, but that's not the issue here)

Sound drops out at about 5 second intervals, but not all the way through the track, and not on every track... it's really annoying though!

---

### Post by kthxbai2u on 2010-03-15
yet another solution that doesn't work.... for me anyways...

---

