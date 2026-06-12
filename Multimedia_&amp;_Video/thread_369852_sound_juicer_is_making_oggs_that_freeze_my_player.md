---
title: "sound juicer is making oggs that freeze my player"
date: 2007-02-25
forum: Multimedia &amp; Video
---

### Post by LogicalDash on 2007-02-25
I have a TrekStor Vibez. It's a musicbox that plays .oggs.

It will play .oggs that were created by Sound Juicer, but then it'll freeze at the very end of the track. This does not happen if I instead make them in Windows with AudioGrabber. (I tried using grip in Ubuntu, but encountered some problems that I'll deal with later.)

I haven't the slightest clue what's going on here. Can someone enlighten me, or at least tell me what to look at?

---

### Post by LogicalDash on 2007-02-25
I got grip working correctly... turned out I had just set the output directory wrong. X-p

So, yes, ogg files created by grip work just fine on the Vibez. This suggests that my problem is with gstreamer, since that's what Sound Juicer uses.

The "gstreamer pipeline" for my Sound Juicer's CD Quality Lossy profile is:

 audio/x-raw-float,rate=44100,channels=2 ! vorbisenc name=enc quality=0.5 ! oggmux

---

