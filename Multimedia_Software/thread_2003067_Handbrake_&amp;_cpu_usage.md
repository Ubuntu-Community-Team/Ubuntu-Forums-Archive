---
title: "Handbrake &amp; cpu usage"
date: 2012-06-13
forum: Multimedia Software
---

### Post by cottfcfan on 2012-06-13
I've been using Handbrake to rip my DVDs, as I find it the most user friendly.
The problem is, when ripping a DVD in H264 format, my cpu usage is between 97-100%.
Obviously temps rise considerably.
Is there anyway to reduce this, & how long can my desktop go at 100% cpu usage before damage occurs?

---

### Post by bryanl on 2012-06-13
It's a good way to test your system's CPU cooling! If all is well, it should cause no problems. Most CPU's will throttle down if they get too hot as a backup. Your system should be designed to handle full throttle CPU usage safely.

Of course, you do have a maintenance procedure that cleans out all the dust bunnies in the computer every now and then? You do make sure that the ventilation into the case is not blocked?

The transcoding that Handbrake does from DVD (mp2) to mp4 is a very compute intensive process. On some of my slower computers, the transcoding frame rate is slower than the display frame rate of the video. I just let them run all night (and sometimes I even queue up a day or two's worth to go through)

It is related to why playback of 1080p video can be an issue on some computers as well.

Some of the modern video graphics subsystems are providing dedicated hardware to help handle the encoding and decoding of modern video codecs and that can be one way to reduce the load on the main cpu.

The CPU load also tests the power supply. I have found a few cases where a full tilt CPU load made the machine flakey after a while because the power supply was weak.

---

### Post by cottfcfan on 2012-06-14
Thanks for your reply.
So I take it that as long as I keep an eye on my temps, & make sure they stay within the recommended limits, then there is no problem?

---

