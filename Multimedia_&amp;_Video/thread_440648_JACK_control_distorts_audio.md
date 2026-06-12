---
title: "JACK control distorts audio"
date: 2007-05-11
forum: Multimedia &amp; Video
---

### Post by Bungo Pony on 2007-05-11
So I installed Ubuntu Studio and was excited to try it out. I loaded some audio files in adour, started up JACK, and the sound is scratchy as hell. Now, this only happens when I'm running JACK. If I play a sound file in Amarok, it plays fine.

Any ideas on why JACK hates my PC?

---

### Post by sites on 2007-05-11
It might have something to do with running JACK in a user login and not as root. I'm just learning how to work with JACK myself.

---

### Post by stratotak on 2007-05-11
you shouldnt have to run jack under root,,thats the whole reason for the low latency kernel..

---

### Post by MetalMusicAddict on 2007-05-11
> **Bungo Pony said:**
> So I installed Ubuntu Studio and was excited to try it out. I loaded some audio files in adour, started up JACK, and the sound is scratchy as hell. Now, this only happens when I'm running JACK. If I play a sound file in Amarok, it plays fine.

Any ideas on why JACK hates my PC?

It very well could be your hardware.

Also make sure you have done this in a terminal: **sudo su -c 'echo @audio - rtprio 99 >> /etc/security/limits.conf'** Then logout/in.

---

### Post by Bungo Pony on 2007-05-11
I tried using JACK before when I was running edgy, and I seem to recall having the same problem. This is one of the main reasons why I'm still using Windows for all of my audio editing / mixing. Adour looks wonderful, but I can't use it if it sounds like crap.

---

### Post by Bungo Pony on 2007-05-11
> Also make sure you have done this in a terminal: sudo su -c 'echo @audio - rtprio 99 >> /etc/security/limits.conf' Then logout/in.

No change :(

---

### Post by Bungo Pony on 2007-05-11
So I'm using mhWaveEdit now (nice editor!). Here's what happens using the following drivers to play a .wav file:

ALSA - Plays fine
OSS - Plays fine
JACK - Sounds like crap (distorted)

When I load up Meterbridge, the VU meters are WAY over 100% (as if the audio is too loud). Perhaps this is a JACK audio input problem? How would I fix that?

---

### Post by Bungo Pony on 2007-05-13
bump

I still don't have it working :(

---

### Post by Chang An on 2007-05-24
Same problem over here

---

### Post by Chang An on 2007-05-25
Any Ideas?

---

### Post by Suthern on 2007-06-06
Same issue over here. (The LOUDNESS). You can get ride of the scratching by playing around with the JACK server settings and increasing/decreasing various values. (boy, how much more vague could that be?)

Just thought I'd chime in too on the loudness part.

---

### Post by lookitseman on 2008-03-04
bump.....same issue.

My system initially had no audio, so I had to patch it (to 1.0.15) by compiling alsa from the source using [this]("https://help.ubuntu.com/community/HdaIntelSoundHowto") guide.  In a previous gutsy install I didn't have this problem, but I don't know if I had used the same guide to patch the audio.

That may be completely unrelated, but as I mentioned this didn't happen last time I installed Gutsy, and I don't know what else could be different this time around.

---

### Post by lookitseman on 2008-03-04
Actually there was something else I noticed that is worth noting.

I set up Ardour to run in time with my system clock.  After about 30 seconds, Ardour was about a second behind my system clock.

Hope that helps.

---

### Post by lookitseman on 2008-03-18
Got it!

I wasn't using the realtime kernel...once I found out what it is and what it's for, the issue was solved!  I don't know how you get the realtime kernel installed, but it came in with the ubuntustudio-audio package which installed a handful of applications, Jack included.

Good Luck!

---

### Post by lookitseman on 2008-03-18
> **stratotak said:**
> you shouldnt have to run jack under root,,thats the whole reason for the low latency kernel..

aaand I really wish I knew the 'rt' kernel option in GRUB stood for realtime...I would have had this problem licked weeks ago.

[https://wiki.ubuntu.com/RealTime](https://wiki.ubuntu.com/RealTime)
-- Instructions to get the realtime kernel if you don't want to bother with the entire ubuntu studio audio package.

---

### Post by naurus on 2008-07-18
All you have to do to get the real time kernel is:
> sudo apt-get install linux-rt 

Hope that helps guys.

---

### Post by naurus on 2008-07-18
Alright, so installing and using the real time kernel didn't do it for me.
I have JACK running in real time mode (i think). Is there any way to test this?

---

