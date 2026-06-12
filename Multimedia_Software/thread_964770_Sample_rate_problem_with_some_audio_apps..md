---
title: "Sample rate problem with some audio apps."
date: 2008-10-31
forum: Multimedia Software
---

### Post by lemmyc on 2008-10-31
Hi,
I have an Emu 1212M, which I have working in Ubuntu 8.10.
(Using ALSA and pulseaudio.)
Originally the sample rate kept defaulting to 48KHz - I would change it to 44.1KHz but on reboot it would go back to 48KHz. I've managed to fix that by updating the drivers and doing 

alsactl store

All good. Except in Banshee, the audio plays back slow. If I reset the sound card sample rate to 48KHz it's ok again. But then it's too fast in other applications. I've tried uninstalling and reinstalling Banshee, same problem.

Question: Is there a sample rate setting stored in a config file somewhere that Banshee is reading? 

Thanks.

---

### Post by lemmyc on 2008-10-31
bump

---

### Post by markbuntu on 2008-10-31
You might want to check the default-sample-rate in your /etc/pulse/daemon.conf file. Some Emu cards, and I am not sure if yours is one of them, do not support 44.1k sample rates, only 48k.

---

### Post by lemmyc on 2008-11-01
Thanks, I just tried it - there was a default sample rate == 44K which I uncommented, but no change after a reboot. :(

Strange thing is, with the soundcard set to 44K (which is a supported option for the card), everything else plays back at the correct rate - e.g. YouTube videos. I suppose they are being played through Pulse too? 

Only Banshee wants to have the sound set to 48K. Maybe this is a Banshee specific issue? I looked in the Banshee database and coulnd't see any relevant config options. (I think I had the same problem with Rhythmbox - I tried to check just now but was getting an unknown playback error. Hm.)

---

### Post by lemmyc on 2008-11-01
Thanks, I just tried it - there was "default sample rate = 44K" which I uncommented, but no change after a reboot. :(

Strange thing is, with the soundcard set to 44K (which is a supported option for the card), everything else plays back at the correct rate - e.g. YouTube videos. I suppose they are being played through Pulse too? 

Only Banshee wants to have the sound set to 48K. Maybe this is a Banshee specific issue? I looked in the Banshee database and coulnd't see any relevant config options. (I think I had the same problem with Rhythmbox - I tried to check just now but was getting an unknown playback error. Hm.)

---

