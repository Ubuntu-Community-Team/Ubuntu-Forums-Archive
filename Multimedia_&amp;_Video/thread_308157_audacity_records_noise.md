---
title: "audacity records noise"
date: 2006-11-27
forum: Multimedia &amp; Video
---

### Post by logos34 on 2006-11-27
I'm trying to record streaming audio in audacity but I'm getting awful distortion on top of the music -- system noise? I've experimented with every setting I can think of but no dice.  It's definitely in the record stage not playback.  It's not the players either -- same result whether xmms, totem, etc.  I unplugged my line-out to my stereo receiver but that's not it.  Audacity works otherwise--plays back files, exports as ogg, lame, wav.
In Preferences I/O is set for dev/dsp (no choice).  I tried changing gnome sound from Alsa to OSS to ICH, turned off ESD and system sounds, etc.  What am I missing?

---

### Post by dbbolton on 2006-11-27
my laptop records very poor quality UNLESS i run it from a battery or have a cheater plug (three-prong input, two-prong output) attatched to the AC cord. i have no idea why

---

### Post by logos34 on 2006-11-27
> **dbbolton said:**
> my laptop records very poor quality UNLESS i run it from a battery or have a cheater plug (three-prong input, two-prong output) attatched to the AC cord. i have no idea why

Grounding interference? Interesting but I think my problem lies elsewhere because a) I'm on a desktop (without even apc battery backup!) and b) audacity works perfectly on my windows partition (dual boot here).

---

### Post by tiaz on 2007-12-11
What soundcard do you have? I am having this issue also with an Intel 82801H soundcard.
I can find people months ago having no sound out issues with this card but none mentioning noisy ext-mic in. I guess it's still being worked on ... I hope it's fixed soon :(

---

### Post by warjowuch on 2008-05-01
I have got the same problem here, it makes the program unusable for recording. Very sad :-(:(

---

### Post by warjowuch on 2008-05-01
But, after a little googling, I found out that making a few configurations, it is solved for me:
- edit preferences ->
- Sampling rate to 48000
- Depth 24-bit
- Disable passthrough options on first 'tab'
- Record thing to Alsa-default (was OSS)

I don't know which of these helped, but it helped...
Good luck!

---

