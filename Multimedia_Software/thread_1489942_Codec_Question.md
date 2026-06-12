---
title: "Codec Question"
date: 2010-05-21
forum: Multimedia Software
---

### Post by mikeashelby on 2010-05-21
I have a video - taken on my mobile phone. In totem, I get sound and video: lovely. However, in Openshot I don't get sounds, and in WinFF it tells me "Unsupported codec (id=73728)" for the audio stream.

Why, when both are using FFMpeg do the installed codecs work differently in different programs?

Cheers,

Mike

---

### Post by mc4man on 2010-05-21
Well although it would've  been better to mention what version of ubuntu you're using totem would be getting amr decoding thru a gstreamer plugin - your other apps are using libavcodec which doesn't support amr in the repo version.

If on karmic or lucid then add medibuntu to your software sources,  and then update your ffmpeg libs the the 'extra' versions (search ffmpeg in synaptic and scroll down

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by mikeashelby on 2010-05-25
That's wicked! Thanks.

Sorry for my bad on Ubuntu version: I'm on 10.04, and was running Totem 2.30.1 and Openshot 1.1.3 (which couldn't hear the audio!).

Anyway, that's cleared it right up!

Cheers.

---

