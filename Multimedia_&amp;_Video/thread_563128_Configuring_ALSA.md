---
title: "Configuring ALSA"
date: 2007-09-29
forum: Multimedia &amp; Video
---

### Post by MattKemp on 2007-09-29
I've recently been playing with Mixxx a bit and I've been trying to use my headphones as well as my speakers to play the two different tracks. Playback for the speakers works fine - the problem I've got is that I can't seem to configure the extra channels for my headphones.

I've tried messing with all the channels in ALSA and OSS, and can't seem to find the right ones to use for the 'phones. Using:

```
speaker-test -D surround51 -c 6
```

Shows that I have sound - I get pink noise out of the left and right speakers, and the headphones. I currently have the headphones in the 'rear' audio socket and I get noice of of each respective side at the right time.

What I've recently been trying to do is use JACK to re-route the audio in Mixxx to the right channels  - however, the only writable client have is alsa_pcm, and this only has two channels - playback_1 and playback_2. My guess is I'm supposed to have a full complement of 5.1 settings i here, but I only seem to have left and right speaker ones.

Can anyone help me figure out how to configure ALSA to allow me to use my headphones too? My soundcard is an Audigy 2 ZS.

---

### Post by MattKemp on 2007-09-29
Just a note, I managed to fix this in JACK by setting the hardware interface to hw: 0,3 - for me this was multichannel playback. D'oh.

---

