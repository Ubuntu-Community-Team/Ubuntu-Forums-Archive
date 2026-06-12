---
title: "speaker-test oddity"
date: 2009-05-27
forum: Multimedia Software
---

### Post by KamikazeNY on 2009-05-27
Just experienced a bit of an oddity with sound in Ubuntu and I was hoping someone could provide some insight on what just occured.

Was configuring a HTPC running latest build of XBMC. Sound was provided via iec958 on an old SBLive card I had laying around. Analog audio worked fine in Ubuntu however iec958 did not. When I enabled the spdif output (unmuted it) my receiver would detect a signal but be unable to read it. Playing music and movies through XBMC via iec958 worked fine. Once I stopped playing the movie, however, the receiver would go back into its error mode.

Ran speaker-test and suddenly my receiver locked onto the 2-channel PCM signal coming from the computer, and I heard the test tones. Ever since that, audio has worked fine all around, even after cycling power on both the receiver and computer.

Anyone know what it is about speaker-test that seems to have magically made everything work?

Thanks!

(this is on Jaunty i386 btw, with PulseAudio uninstalled)

---

