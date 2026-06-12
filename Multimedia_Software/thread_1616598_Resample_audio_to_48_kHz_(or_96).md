---
title: "Resample audio to 48 kHz (or 96)"
date: 2010-11-08
forum: Multimedia Software
---

### Post by swaaye on 2010-11-08
I'm running an Audigy Platinum. As some of you probably know, the Creative cards run natively at 48 kHz and resample everything to that frequency. If you play 44.1 kHz the hardware conversion to 48 kHz isn't great. However, Audigy has wonderful signal quality so I usually just use a sample rate conversion filter in my music program (Winamp usually).

I did some web searching of course and found two different approaches to configuring the audio subsystem(s) to resample to 48 kHz. Unfortunately neither is working out.

1) PulseAudio /etc/pulse/daemon.conf tweaking
I first changed the default frequency to 48000 but this did not improve sound quality. It seems to be ignored? I then also changed the resampling algorithm to "src-sinc-best-quality" but this caused the audio system to crash as if the output format was incompatible....

2) ALSA tweaking via .asoundrc in home dir
This I could not figure out. I found a bunch of different examples on how to set up frequency and resampling algorithm but nothing seemed to have an effect. I tried setting both ALSA and PulseAudio output in Exaile but this didn't have an effect either.


I know there are other people out there who have dabbled in this sort of tweaking. I'm hoping I can find somebody who knows how to get it working. :)

---

### Post by cchhrriiss121212 on 2010-11-08
I can set my card rate just using alsamixer from a terminal window. but I'm not sure what kind of improvement you are looking for if your source is 44100Hz.

---

### Post by swaaye on 2010-11-08
The improvement is in bypassing the sound card's resampling hardware. Do some searching on Creative cards and 44.1 kHz -> 48 kHz. They internally resample everything to 48 kHz and going from 44.1 kHz to 48 kHz is one of the more difficult conversions. Their algorithm causes some minor aliasing.

It's not exactly a big deal but I've always used a Winamp plugin that gets around the issue.

---

### Post by cchhrriiss121212 on 2010-11-08
So no luck with alsamixer? I know that mplayer can resample, but I assume that you won't want to use that for playing music, you could however, use it to test the difference with any other system wide fix you might find.
In smplayer, go to preferences>advanced>options for mplayer, then follow the example shown for the audio filters box.

---

