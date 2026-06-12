---
title: "Excessive audio latency?"
date: 2006-06-15
forum: Multimedia &amp; Video
---

### Post by intvnut on 2006-06-15
I am the author of an Intellivision emulator, [jzIntv]("http://spatula-city.org/~im14u2c/intv/"), that uses [SDL]("http://www.libsdl.org/") as its sound and graphics library.  I was previously using Ubuntu 5.04 (Hoary), and experienced moderate but acceptable audio latency.  (I'd estimate it around 500ms, tops.)

I recently upgraded to 6.06 (Dapper), and now my audio latency has shot way up, to what seems like well over 1 second.  It could very easily be approaching 2 seconds.

Dunno if it's at all relevant, but I'm running on AMD64, and I'm using the audio from my K8N-DL's onboard Nforce4 chipset.

I have tried disabling ESD, and that did not seem to have any noticeable affect on audio latency.  As an emulator author, I'm very keen to see the sound effects in the video games line up with the video.  It's an up-hill battle, and I've always tolerated a little bit of misalignment--ultimately, games are least tolerant of video latency, so that must be the first order of business.  Audio is an almost distant second. 

But still, 1000 - 2000ms audio latency?  That's ridiculous.

I've tried both 44100 and 48000 kHz output sample rates.  They don't seem to help.  Internally, jzIntv uses up to 3 buffers of 512 samples.  That's around 35ms latency, tops.

Does anyone have any insight on how to configure Ubuntu to reduce the audio latency? 

Thanks,

--Joe

---

