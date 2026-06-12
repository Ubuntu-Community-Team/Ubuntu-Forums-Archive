---
title: "Wily/15.10 Making JACK work with PulseAudio"
date: 2016-01-25
forum: Multimedia Software
---

### Post by JCopse on 2016-01-25
I have a simple need. I need to direct audio from a media player and audio from a USB microphone into one recording/capture source. I was able to get that working with a bunch of PulseAudio commands, but they seemed to randomly reset every now and then, - forcing me to re-apply a variety of settings mid-work. I have been told that JACK can do what I want to. However, when I tried installing JACK on a laptop (running Ubuntu 14), all of my audio stopped working. I'm worried about that happening again, because I don't understand why it happened.

Looking at [https://github.com/overtone/overtone/wiki/Installing-and-starting-jack](https://github.com/overtone/overtone/wiki/Installing-and-starting-jack) and [https://wiki.archlinux.org/index.php/PulseAudio/Examples#PulseAudio_through_JACK](https://wiki.archlinux.org/index.php/PulseAudio/Examples#PulseAudio_through_JACK) leaves me confused. The terminology goes right over my head. 

My basic questions are

1) Can I add JACK to my existing setup - not replacing ALSA or PulseAudio?

2) Can someone here help me to get JACK installed on Wily (whether I have to replace ALSA/PulseAudio or not)? A bit of layman-speak / step-by-step help or a Skype or Hangouts conversation would be appreciated. YouTube and Google haven't helped me.


Thanks for checking out this thread.


Edit: I found a video that gave me a simple guide and I've got JACK working now. However, a new problem has appeared. I can start JACK via qjackctl, but when I do I lose all sound. It returns when I stop JACK.

---

### Post by Bucky Ball on 2016-01-25
*Thread moved to **Multimedia Software**.*

---

### Post by yoshii on 2016-01-25
1) Can I add JACK to my existing setup - not replacing ALSA or PulseAudio?

Yes, JACK is a system that co-exists with ALSA and PulseAudio.  
All three of them co-exist with each other.  None of them fight each other.  
They won't replace each other.

---

### Post by JCopse on 2016-01-27
I have JACK installed in a way that lets me start/stop it to return to using just PulseAudio now. However, I get no sound when using JACK. In JACK, the lines between PulseAudio and System are red. I'm not sure what to do from here.

Edit: Nevermind. Turns out what I needed to do was use qjackctl to start JACK, then close all applications, then start applications, then use pavucontrol to switch from Built-In Analog Stereo to JACK Sink.

---

