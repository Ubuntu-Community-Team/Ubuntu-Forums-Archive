---
title: "Netflix Dolby Pro Logic II upmix or emulation"
date: 2015-02-23
forum: Multimedia Software
---

### Post by nathan-burnside on 2015-02-23
Is there any way to get pulseaudio or alsa to emulate Dolby Pro Logic II upmixing? Netflix streams usually have stereo sound with DPL2 encoding, so that a DPL2 receiver can reproduce decent 5.1 surround sound. Even if the audio stream doesn't have DPL2 encoding (youtube or an mp3 for example) a decent receiver can emulate DPL2 and give acceptable surround sound.

Pulseaudio/alsa don't appear to have this capability. They CAN upmix a stereo stream to a 6 channel stereo stream -- but that's not really surround. You can also get it to apply a cutoff frequency for the subwoofer and a few other tricks. But, I haven't seen any support for Dolby Pro Logic II emulation and upmixing.

For example, if I watch a netflix movie, the sound passes to pulseaudio as a 2 channel stereo stream. Pulseaudio upmixes this to a 6 channel stereo stream (but not really surround). This outputs directly to 6 channels on my receiver (through alsa and my sound card and 6 RCA lines). What I hear when I watch a netflix movie is just six channel stereo sound. The center speaker doesn't get the dialog like it should. Unfortunately my receiver doesn't speak DPL2, so I was hoping that Linux would take care of it...apparently it doesn't.

---

### Post by tgalati4 on 2015-02-23
There are ways to get gstreamer (the audio playback framework) to pass through DLP2 signals through the SPDIF/optical port and have a Dolby Pro Logic II receiver decode the surround sound correctly.  [http://docs.gstreamer.com/display/GstSDK/Playback+tutorial+9%3A+Digital+audio+pass-through](http://docs.gstreamer.com/display/GstSDK/Playback+tutorial+9%3A+Digital+audio+pass-through)

There is not a way to decode DLP2 in software and play the true surround sound through the extra channels on your sound card.  That would require a Dolby license and powerful audio DSP.   My quick web search shows that some folks have tried to reverse-engineer such matrix decoding, but the results have been crappy.  The sound quality is worse than simple stereo into back channels.

Find a cheap receiver with a Dolby Logic Pro II sticker.  Of course the intersection of those two conditions might be the null set.

A Denon AVR1513 provides 110 watts/channel and Dolby decoding for $225 US.

---

### Post by nathan-burnside on 2015-02-23
Thanks for the informed response. I had assumed that DPL2 decoding, being fairly old, was easily implemented in linux.
 
I have seen decoder boxes that do what I want for about $50. I may get one of them, or just get a used receiver. Something pre-HDMI, but with DPL2 should be pretty cheap. Thanks.

---

### Post by tgalati4 on 2015-02-23
If it was easy, then it would be done already.  My impression is that it is a complicated encoding and compression that stores the extra channels as phase shifts in the stereo signal.  The matrix encoding implies that you need a vector processor (like an Altivec or similar) to effeciently decode on-the-fly so that the real-time-audio stays in sync with the video.  There are custom chips that do this, but trying to do the same in software becomes cumbersome and the latency too long to be useful.

---

