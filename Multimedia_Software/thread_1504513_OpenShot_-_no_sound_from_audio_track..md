---
title: "OpenShot - no sound from audio track."
date: 2010-06-08
forum: Multimedia Software
---

### Post by dchurch24 on 2010-06-08
Hi all,

I have recorded some video, and now wanted to add some sound.

I added a sound track, but when it's playing, I can't hear anything.

I'm usually running Jack - for Ardour/Hydrogen etc... - I can't find anywhere in OpenShot to change the Audio to Jack, so assume it's not supported.

I have killed Jack in the hope that Alsa will work with OpenShot, but still I have no sound.

Does anyone know how I can get this working?

---

### Post by cchhrriiss121212 on 2010-06-09
Hello again, try removing pulse from your system.

---

### Post by dchurch24 on 2010-06-09
> **cchhrriiss121212 said:**
> Hello again, try removing pulse from your system.

Thank you, I'll try that when I get home.

Jack will still work though, right?

---

### Post by cchhrriiss121212 on 2010-06-09
Yes, jack runs on top of ALSA in the same way pulse does. [Here]("http://yokozar.org/blog/content/linuxaudio.png") is a diagram showing the somewhat confusing state of audio on linux. 

A simple version for you would be this:
Applications -> Pulse/Jack -> ALSA -> Sound card

So when you remove pulse, the chain will go straight to ALSA.

---

