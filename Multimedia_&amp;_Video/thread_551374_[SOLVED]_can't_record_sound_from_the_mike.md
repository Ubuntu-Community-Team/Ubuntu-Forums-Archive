---
title: "[SOLVED] can't record sound from the mike"
date: 2007-09-15
forum: Multimedia &amp; Video
---

### Post by berliita on 2007-09-15
Hi y'all,

My mike works fine: i can hear myself in the speakers loud and clear while speaking into the mike. Nevertheless, none of the sound recording software i've used: Audacity, KRec and Soundrecorder manages to capture input from my mike. More accurately, they appear to capture fine, but they don't play it back. :confused:

---

### Post by berliita on 2007-09-28
I've been able to record from the microphone for a few days now. All i needed to do was fiddle around with the various channels on the Volume Control panel.

---

### Post by apparle on 2007-09-28
i also have the same problem. I am hearing mic sound from speaker but unable to record??
I use OSS instead of ALSA (ALSA doesn't work for me)
Help me out will you??

---

### Post by apparle on 2007-09-28
i also have the same problem. I am hearing mic sound from speaker but unable to record??
I use OSS instead of ALSA (ALSA doesn't work for me)
Help me out will you??

---

### Post by berliita on 2007-09-28
Here's my Volume Control configuration. I use Audacity to record sound from the microphone. My mic is part of my headset.

On the "Switches" tab, the following items are marked, and only them:
* Microphone Capture
* Mic Boost (+20dB)
* External Amplifier

On the "Recording" tab both "Capture" sliders are enabled and are set at the highest position.

On the "Options" tab:
* Mic Select: Mic1
* IEC958 Playback Source: AC-Link
* Mono Output Select: Mix

On the "Playback" tab all sliders are at their highest positions, but some are muted. Here's the complete list:
* Master: muted
* Master Mono: muted
* Headphones: enabled
* PCM: enabled
* Line-in: muted
* CD: enabled
* Microphone: muted
* Phone: muted
* IEC958 Playback AC97-SPSA: muted
* Aux: muted

Hope this helps.

---

### Post by apparle on 2007-10-04
I will give it a try

---

