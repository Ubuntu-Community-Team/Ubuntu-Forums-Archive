---
title: "Plugging-in headphones mutes speaker AND headphones"
date: 2011-02-25
forum: Multimedia Software
---

### Post by arthens on 2011-02-25
Hi guys :)

Searching in the forum (and in Google) I found a lot of people having the problem that when you plug-in your headphones it doesn't mute the speaker... well, I have the opposite problem!

**Problem 1**

When I plug-in my headphones it mutes both speakers and headphones. And un-muting one un-mutes the other one as well :confused: I can reproduce the same problem using alsa-mixer... muting "headphones" or "front" always mutes the whole system.

**Problem 2**

Also the volume control kind of doesn't work for the headphones... if I set the volume at 0/10 the headphones are mutes, if I set it to 1/10 they are normal, if I set it to 2/10 the headphones are REALLY loud, so loud that I can clearly hear everything even if the headphones are on my desk.
Using alsa-mixer I can fix it... but it's quite annoying that I have to use it every time!

It seems to me that the volume of the headphones is given by the channels Headphone * PCM, and the volume of the speakers by PCM * Front... the problem is that the volume control (of gnome or on the keyboard) changes Front and not PCM. 
Ideally it should change PCM, and the headphones (when plugged-in) should set Front to 0.

Any help? :)

---

### Post by arthens on 2011-02-26
Help anyone?

I'm using Ubuntu 10.10 (upgraded from 10.04)

---

