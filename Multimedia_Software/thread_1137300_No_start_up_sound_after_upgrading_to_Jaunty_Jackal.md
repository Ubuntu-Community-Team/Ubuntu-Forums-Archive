---
title: "No start up sound after upgrading to Jaunty Jackalope"
date: 2009-04-25
forum: Multimedia Software
---

### Post by lnajt on 2009-04-25
After upgrading to Jaunty this morning, no applications on my computer play any sound, and the start up Jingle is mysteriously absent.

I would appreciate some help.

I ran a speaker test ($speaker-test) and I can hear some static.

UPDATE:

I'm not sure if this is related, but when I shut down I get the messae: *pidfile not found. is Jackd running?

---

### Post by lnajt on 2009-04-25
Partially Fixed:

I unchecked IEC958 Default PCM un under Volume Control > HDA Intel (ALsa Mixer) > Switches [you have to enable the switch in preferences].

It now works through the miniport on the side of my laptop, but not the dock that I normally plug my speakers into.

A minor issue, but if anyone knows how to fix it I would appreciate being told - the mini-port on the side of my computer is a little messed up.

---

### Post by markitoxs on 2009-04-25
Had the same Issue, using previous kernel works for me.

---

