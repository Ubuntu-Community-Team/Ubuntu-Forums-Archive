---
title: "muteing speakers with headphones"
date: 2008-01-30
forum: Multimedia &amp; Video
---

### Post by usc911 on 2008-01-30
Hi guys,
I have an Advent 9112 and am having huge trouble getting the system speakers to mute while the headphones are plugged in.  I use my laptop while traveling so its a bit of a must to get htis fixed. I have seen this is a problem on vaio's as well, but none of the solutions there worked for me.

Any ideas?
Thanks

---

### Post by usc911 on 2008-01-31
any ideas guys? i have had a masisve search around but the only things i have found are:

- right click volume and enter volumne control, then mute the speakers (this just mutes everything

-to go in to the alsa settings through terminal. this also just muted both the headphones and speakers

really could do with getting this fixed

---

### Post by linuxferret on 2008-01-31
don't know if this will help or not - but the sound problems i had were only resolved using the GUI alsamixer (GNOME Alsa Mixer).  There are more settings to play around with there.  The 'surround' setting should be the volume control for your headphones.

I'm not saying the is a complete answer (there may be others here who can provide you with that) but worth a try as it solved the issue for me.

---

### Post by Antrix on 2008-01-31
Hi. I had exactly the same problem.

To fix it I had to.

1. Switch headphones on (either alsamixer or through gnome sound control panel)
2. Mute "Front". This will disable your builtin frontal speakers.
3. Adjust "Front" channel to about 80% volume - even though it is muted it still appears to control the headphone volume if headphone switch is on and headphones are plugged in.

Hope this helps you

---

### Post by usc911 on 2008-01-31
thanks for the response, when i mute front it mutes both the front and headphones. i have changed every possible ( i think) sequence of controls in the alsa mixer but still nothing, really frustrating me now, i have read a million ways to do it on other devices but cannot apply it to mine :@

---

### Post by usc911 on 2008-01-31
any further suggestions? i need help :D

---

### Post by sammydadams on 2008-01-31
i got something for you to at least try....this worked on my vaio so the modprobe thing might have to be changed, but try it anyway:

```
$ sudo apt-get install module-assistant
$ sudo m-a update
$ sudo m-a prepare
$ sudo m-a a-i alsa
```

i think this recompiles ALSA (correct my if i'm wrong cause i'm a relative noob)

i'm not sure if this is absolutely necessary for your setup, but i had to modify alsa-base as well, i hate to say, but you'll have to look up the coding on your own for that, i don't remember where i got this and it is computer specific, or at least company specific...check the alsa website maybe? ([a link to the soundcards matrix at alsa]("http://bugtrack.alsa-project.org/main/index.php/Matrix:Main"))  here's what i did though:

add line:
options snd-hda-***intel ***model=***vaio*** position_fix=0
to
/etc/modprobe.d/alsa-base

go into system>administration>software sources and enable Unsupported Updates (gutsy backports) under the updates tab

then go into synaptic and look up "backports"

install all the ones that are generic...i have:
linux-backports-modules
linux-backports-modules-2.6.22-14-generic
linux-backports-modules-generic


this is what worked for me so i figure it's at least worth a try...i really hope it helps you out cause i was struggling with this for awhile myself

---

