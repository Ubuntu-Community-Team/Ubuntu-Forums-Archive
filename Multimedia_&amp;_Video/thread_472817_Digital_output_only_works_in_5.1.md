---
title: "Digital output only works in 5.1"
date: 2007-06-13
forum: Multimedia &amp; Video
---

### Post by amiba on 2007-06-13
I'm having a strange problem:
I have a SBLive connected to an external amplifier via SPDIF. 
Until recently, everything was working perfectly: I had sound output in stereo, and in surround when the videos had surround sound.
However, two days ago, it stopped working (I was trying to get VLC to play movies in surround, but "only"
messed with the prefs of vlc).
Right now, the situation is: 
-I have sound in the analogue output (Headphones)
-When I start a 5.1 movie in totem, the digital output works fine (the amp lights up with the indication of the number of channels)
-In all other occasions, the digital output is muted, and there is no indication whatever in the amp (the "default" stereo indicator goes off in the ubuntu startup process)
Besides all this, in the ubuntu sound configuration, three new devices have shown up:
- Multichannel playback
- Multichannel Capture/PT Playback
- ADC Capture/Standard PCM Playback
These weren't used to be there before this problem started, so I presume they are related.
I've tried to reinstall the alsa subsystem (purge/install), resetting everything, rebooting, but still no luck;
My problem is similar to this one 
[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/118861](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/118861)
Does anybody have a solution?
Thx

---

