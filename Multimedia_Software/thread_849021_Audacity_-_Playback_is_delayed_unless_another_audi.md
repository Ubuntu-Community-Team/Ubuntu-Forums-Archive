---
title: "Audacity - Playback is delayed unless another audio player is running"
date: 2008-07-04
forum: Multimedia Software
---

### Post by GammaRay256 on 2008-07-04
If I open Audacity with no other programs running and I try to play an audio file in Audacity, there is a delay of about 250-500ms before the audio will start playing; it does not matter where I start in the file.  Both devices "OSS: /dev/dsp" and "ALSA: default" have the same delay except that ALSA makes a 'clicking' noise during the initial delay until the sound starts.  Basically, it makes Audacity very annoying to use.

Now, I have found a workaround: If I open another music player (such as Audacious/XMMS or Totem) and pause whatever that player is playing, Audacity magically begins to work (no more delays or clicking, sounds play instantly).  Sometimes the list of devices in Audacity's preferences changes from about 13 devices to about 3 or 4 devices once the external player is running.  It does not matter whether I start the player before I start Audacity or while it is running.  When the player starts Audacity instantly starts working perfectly; and when the player is closed, Audacity instantly goes back to the original problem.

This workaround works fine; it is kind of annoying to have to open and audio player, but it can be done.

No other programs have this problem, only Audacity.

I am wondering if anyone knows what might be causing this, if there is anyway to fix it, and if anyone else has had this problem either with the same or different hardware.

My laptop is a Dell M1210, and I am currently running Ubuntu 8.04.

I've had the problem with Ubuntu 7.10, and now 8.04.  PulseAudio in 8.04 seems to make no difference in this situation.

---

