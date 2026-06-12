---
title: "Logitech Music Anywhere no sound playback"
date: 2008-11-08
forum: Multimedia Software
---

### Post by arigram on 2008-11-08
Greetings fellow Ubuntu users.

I have trouble with the Logitech Music Anywhere bluetooth transmitter.
It used to work fine with previous releases but not with Ibex. It is probably some sound system mis-configuration as it recognizes the transmitter by name as soon as its plugged in.
Preferences/Sound, when selecting it in either of the two playback lists (Logitech Logitech Music Anywhere USB Tra USB Audio (ALSA) ) the Test returns with a warning:

> audiotestsrc wave=sine freq=512 ! audioconvert ! 
audiosample ! gconfaudiosink profile=music:
Could not open audio device for playback.

Same option with OSS comes up with the testing dialog but no actual sound.
How do I fix this?

Thank you beforehand.

---

### Post by arigram on 2009-02-13
... I thought the solution would be an easy (but obscure) text file edit... oh, well. Can I file it as a bug atleast?

---

### Post by cariboo on 2009-02-13
You can create a bug report at [Launchpad]("http:///bugs.launchpad.net/"), you'll have to creae an account if you don't have one already.

Jim

---

