---
title: "Mythtv and HD support for Hauppauge PVR-1200"
date: 2008-11-28
forum: Mythbuntu
---

### Post by ebike on 2008-11-28
Hi All,

I have just installed this card and have the drivers installed ok, including the firmware, but although the streams tuned in ok, I am having trouble playing the streams in Mythtv. I managed to play a stream for a few seconds, but then I get a segfault in mythfrontend. The error is below. It seems there is an issue with h.264 decoding.

For graphics I am using an ASUS PQ5-EM motherboard with integrated g45 graphics. I am using a 2.6.17-7 kernel.

Can anyone suggest how to debug this? ... or is the h.264 support still flakey for g45? Also, there is an issue with sound. It appears there is no support for AAC+ yet, is this true?

Thanks

> 
I am getting the following error on Mythfrontend:

2008-11-29 11:50:54.759 [h264 @ 0x7f55f9e5ae90]number of reference frames exceeds max (probably corrupt input), discarding one
2008-11-29 11:50:54.759 [h264 @ 0x7f55f9e5ae90]number of reference frames exceeds max (probably corrupt input), discarding one
2008-11-29 11:50:54.759 [h264 @ 0x7f55f9e5ae90]number of reference frames exceeds max (probably corrupt input), discarding one
2008-11-29 11:50:54.777 [h264 @ 0x7f55f9e5ae90]mmco: unref short failure
2008-11-29 11:50:54.805 [h264 @ 0x7f55f9e5ae90]mmco: unref short failure
2008-11-29 11:50:54.877 [h264 @ 0x7f55f9e5ae90]mmco: unref short failure
2008-11-29 11:50:57.281 Video timing method: USleep with busy wait
2008-11-29 11:50:57.364 WriteAudio: buffer underrun
2008-11-29 11:50:57.381 NVP: prebuffering pause
Segmentation fault



---

### Post by ebike on 2008-11-28
After much forum trawling I have found the answer for the crashing anyway. After I turned off the loopfilter option in the playback profile I was using (CPU+), then everything was stable and I could watch every channel at all HD resolutions.

By the way I have a Dual-core E7300 CPU and I am decoding 720p at 20% CPU usage and 30% for 1080i ... brilliant ...:popcorn:

However, there still remains the issue of sound. For the channels that broadcast MP3, they are fine, but I have no sound for the channels that use AAC+, I guess I will have to wait for support for that .....

That will teach me for being on the bleeding edge ....:)

---

### Post by ebike on 2008-12-01
Anyone know when support for AAC+ will be added to the codecs mythtv uses?

---

