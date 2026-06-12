---
title: "What MP3 decoder does iTunes have? How to get the same quality?"
date: 2009-12-29
forum: Multimedia Software
---

### Post by Repgahroll on 2009-12-29
Hello there!

I can get the same sound quality on Ubuntu that i get on Windows for FLAC/WAV files using Audacious and bypassing all signal processing.

However, MP3 files reproduction have poor quality, i'm learning english and i've downloaded some audio lessons to study, but the difference of quality is big and it's harder to hear the conversations using another player, I thought iTunes had gstreamer embedded, but it doesn't, maybe it has some closed-source miraculous decoder =(, i don't know.

My question is: Is there a way to get the same MP3 reproduction quality under GNU/Linux (Ubuntu)?

PS: Wine is good but iTunes doesn't work well and it has some kind of compatibility issue with the sound hardware (maybe the virtual hw) because the frequency response is limited and the sound isn't very good at all. (tested Winamp).

Thanks in advance.

---

### Post by Chronon on 2009-12-29
You could compare the decoder performance by decoding to a WAV with each decoder and then comparing the two decoded versions.  I would honestly be a bit surprised if this is a decoder issue.

---

### Post by Bölvaður on 2009-12-29
> **Repgahroll said:**
> 
However, MP3 files reproduction have poor quality,

Make sure you have high enough bit rate. If you encode it with too low bit rate it will give you poor quality. But higher bitrate means the file size increases.

Normally 192 kbps  &#8594;  320 kbps  is enough.

When you export in Audacity you have to pick mp3 and then if you want constant bitrate or if it should vary in different ways and what bitrate you would like. Many things to consider.

---

### Post by Chronon on 2009-12-30
I think the OP is talking about decoding previously encoded MP3s to PCM (and rendering with sound card).  I don't think the issue here is about encoding to mp3.

---

### Post by Repgahroll on 2009-12-30
> **Chronon said:**
> I think the OP is talking about decoding previously encoded MP3s to PCM (and rendering with sound card).  I don't think the issue here is about encoding to mp3.
Right.

----

The bitrate is 96kbps, but the sound is much clearer on iTunes, even comparing Winamp or WMP for example (on Windoze), so I think the difference is the iTunes decoder because i don't use equalizers/enhancers.

iTunes seems to decode "smoother" sound, maybe it "deblock" the digital sound or something...

Thanks.

---

### Post by cascade9 on 2009-12-30
If I recall correctly, iTunes is just using some standard decoder. Its not the decoder, its post-processing.

---

### Post by Repgahroll on 2009-12-30
Okay... Doesn't matter if its the decoder or post-processing... the question is:

How can i get the same quality on Ubuntu?

---

### Post by Repgahroll on 2009-12-31
Okay, i found two ways to get better MP3 sound quality:

-Using Audacious and not bypassing the signal processing
-Using Amarok+Xine (not as good as Audacious)

Songbird, Exaile, Rhythmbox, etc., all has the same bad sound quality.

However, comparing Audacious with signal processing, iTunes sound is significantly better.

Maybe the problem is the sound card support on Linux. Because FLAC files became bad if i activate signal processing on Audacious, and MP3 files became bad if i deactivate it. :(

---

### Post by VertexPusher on 2009-12-31
MP3 decoding is a standardized process, i.e. all decoders yield bit-identical results. Any difference in sound is a result of post-processing, so your goal is to minimize the amount of post-processing done after decoding.

If the sample rate (not bitrate) of an MP3 file does not match the sample rate of the sound card, the decoded stream needs to be converted. Sample rate conversion can degrade sound quality if a poor conversion method is used. Most sound cards run at 48kHz by default, but some can be reconfigured to run at 44.1kHz or even 96kHz. If that is not an option for you, you may replace the default sample rate converter. How this is done depends on whether you use PulseAudio or not.

---

### Post by cascade9 on 2010-01-01
> **Repgahroll said:**
> Maybe the problem is the sound card support on Linux. Because FLAC files became bad if i activate signal processing on Audacious, and MP3 files became bad if i deactivate it. :(

Nope, its a post-processing issue. What the whole process is doing its trying to 'fill' in discarded data. So, with MP3s, it tries to build up stuff thats been lost. Being lossless, flac doesnt have any missing data, so the post-processing actually muddies the signal. 

You could use one player for MP3, a different player for flac. 

Or you could just get rid of horrible 96K MP3 files, and move up to at least 192K (and better yet to go to VBR v2-v0, lower the number the better the sound).

---

