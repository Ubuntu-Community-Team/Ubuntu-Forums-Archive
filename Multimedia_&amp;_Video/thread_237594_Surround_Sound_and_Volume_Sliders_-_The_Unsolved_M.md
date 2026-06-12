---
title: "Surround Sound and Volume Sliders - The Unsolved Mystery"
date: 2006-08-16
forum: Multimedia &amp; Video
---

### Post by cbrack on 2006-08-16
Hi all,

I'm relatively new to these forums, mainly because I just switched back from windows to Kubuntu.  I'm glad to see that linux has come a long way from where it was a few years ago.

Anyways, I have my setup with a Soundblaster Live 5.1 surround sound card and my surround sound speaker system.  Everything works properly sound-wise, however when trying to control volume, I run into a funky error that I have not been able to solve.  I've been searching in my spare time for a week now, and I haven't found any solution that works.

The issue is that when trying to control my volume levels, the three sliders that work do not control the same speakers.  When PCM and Wave Surround are fully up with Master down, I hear just a faint sound, not completely mute.  When I kick up Wave Surround with Master muted and PCM fully up, I only get sound from the rear 2 speakers.  With only PCM up and the other 2 down, I get no sound.  With Master & PCM at full, and Wave Surround down, I get sound only from the front speakers.

Basically, I need to find a way to control all the speakers with 1 slider, so that I can use my media keyboard correctly, without only controlling either the front or rear.

If I was confusing, or if anyone needs additional info, I'd be happy to provide it.

Thanks in advance,


Chris

---

### Post by cbrack on 2006-08-18
bump :)

---

### Post by cbrack on 2006-08-19
I'm still searching for the answer... If anyone has any places to start looking, let me know.  Been searching google and these forums like mad.

If I find anything out I'll be sure to post.

---

### Post by svenaron on 2006-09-12
Not sure if this will work for you but I did this:

Start the volume-control app.
```
/usr/bin/gnome-volume-control
```
In the tab "switches" I ticked the box "SB Live Analog/Digital Output Jack" and voilá, Master volume stands up for its name.

Hope it helps!

/Sven

---

