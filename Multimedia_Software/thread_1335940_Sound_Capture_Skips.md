---
title: "Sound Capture Skips"
date: 2009-11-24
forum: Multimedia Software
---

### Post by seancarver on 2009-11-24
When I try to record the following spoken sentence (with sound recorder, Skype also having problems): "Testing ... Ho hum, la de da, life is good,"  I get: "Testing ... Ho hum, la de de de de de de de de de de...."  It can take up to 10-20 seconds of proper function before it starts to skip.  I can tell it is skipping because the duration of the recording (as displayed in Sound Recorder) jumps by several minutes for each second of real time.  When I play back at the precise moment that the duration started growing faster than real time, I get the skipping.

I have a Asus EEE PC 1101ha with Ubuntu Netbook Remix 9.10, kernel 2.6.31-14-generic.

One thing that is not out of the box:  I installed the ALSA drivers into the Kernel.  I can't remember exactly how I did this because I was following directions on the web which I can't find right now.  The ALSA drivers fixed the playback, RhythmBox etc didn't work before but does now.  To get any recording I had to set recording/boost levels to nonzero with alsamixer.  The internal microphone doesn't work at all.  I am using the "Front Mic" (plugged into to the side of the Netbook) to get this error.  It doesn't seem to matter how I have set the capture levels.

Before sending this post, I upgraded my Kernel to 2.6.31-15-generic.  This fixed some other problems I was having but audio (both sound capture and playback don't work).  I can't find instructions for putting the ASLA drivers back in the kernel.  Could someone please post them

Also I can't seem to find the capture skipping problem discussed anywhere.

Thanks for any help.

---

