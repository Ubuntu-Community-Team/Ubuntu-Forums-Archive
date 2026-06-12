---
title: "Sound Died and Cannot Figure Out Why"
date: 2009-02-07
forum: Multimedia Software
---

### Post by cosmicsteve on 2009-02-07
Hi everyone-

This is my first time posting here. It seems as though the sound playback on my Ubuntu 8.10 64 bit system has died. I have already looked around for an answer, and it looks as though everything seems to be working except for playback. It recognizes my soundcard (Sound Blaster Audigy LS), I have tried to purge/reinstall the ALSA drviers, and I can even get sound at the login screen. What I can't do, however, is hear any sounds after I log in. Does anyone out there have any suggestions for that? I would greatly apprecate any help.

Steven Ehlert

---

### Post by mc4man on 2009-02-07
Could be any number of things, I've had no problems with Audigy 2 cards (except on a box with a 5.1 sound system, there I totally removed pulse due to it's incredibly poor performance with upmixing 2 - 6 ch when using 3rd party apps

Try this - double left click on the little speaker icon in upper panel , choose 'switches' and uncheck the Audigy Analog/Digital output jack.
If there is no switches tab then click on preferences , scroll down and add it ( Audigy Analog/Digital output jack) and then go back to switches, and uncheck.

This thread has some screens and alt. way #9, # 14

[http://ubuntuforums.org/showthread.p...18#post6633218](http://ubuntuforums.org/showthread.p...18#post6633218)

---

### Post by cosmicsteve on 2009-02-08
Thanks for the help, although somehow it came back as I started screwing around with PulseAudio. I am not sure what I did but my sound appears to have come back.

---

