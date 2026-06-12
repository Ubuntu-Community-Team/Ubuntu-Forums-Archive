---
title: "Professional audio playback."
date: 2008-09-01
forum: Multimedia Software
---

### Post by Ginko on 2008-09-01
Hi!
I listen a lot of music recently and have some good quality .flac backup. Besides I have a Sennheiser HD 555 and an external DAC. So I was reading some articles and forum threads in the topic. The outcome is the rt kernel with jack.

I'm using the real time kernel, and this is the easiest way how to
install it:

```
sudo aptitude install linux-rt
```

I installed jack with the necessary items. I have a good latency with just a few xruns all day (latency: 5.8msec). I don't care about pulseaudio and I do NOT need software mixing. Jack can prove what I need (audio when listening to music or watching a movie).

I use these programs (they have direct access to jack):

- Amarok (I mean Xine because Amarok uses Xine as its engine)
- Smplayer

**I'm trying to solve the problem follows: suppose, I'm playing a file on the computer. Then the data have to flow into my external DAC without modifications, even if I listen 24/96 or 16/41 quality audio files. So I would like to avoid resampling and similar methods.** I would call it "passthrough".

My Jack settings:
- realtime
- 64 frames/period
- sample rate 44100
- periods / buffer
- 128 port max.
- 5000 msec timeout
- audio duplex

Jack resamples everything to 44100Hz with these settings.
The D/A converter has Toslink ports and USB connection so it can  be connected directly to the computer and it recognizes it as a sound card.
If I would use toslink then I have an integrated audio card (Realtek HD) with optical output.

So low latency and unmodified data are what I'm searching for.

---

### Post by markbuntu on 2008-09-01
You can set mplayer or vlc to use ac3 passthrough to get direct digital output from your built in sound card optical output. I do not know about amarock.

---

### Post by Ginko on 2008-09-01
> **markbuntu said:**
> You can set mplayer or vlc to use ac3 passthrough to get direct digital output from your built in sound card optical output. I do not know about amarock.

Do you know the specific option? I didn't find ac3 or similar output. And the most important would be Amarok but It isn't have passthrough option so Jack should do the job.

---

