---
title: "GPU Video Encoding in Linux"
date: 2011-01-04
forum: Multimedia Software
---

### Post by airjrdn on 2011-01-04
I just watched [this short video]("http://apcmag.com/sandy-bridge-video-transcoding.htm") where MediaEspresso was used to encode a video on a new Intel GPU insanely quickly.  The video compares that to 3 other notebooks; one with a previous gen Intel GPU, one with an AMD/ATI GPU, and one with an nVidia GPU.

Is there an Ubuntu (or Linux in general) application comparable to that or Handbrake that will utilize the GPU (using Cuda for nVidia for example) offering performance comparable to what is shown on the video?

---

### Post by BicyclerBoy on 2011-01-04
AFAIK It is not going to happen any time soon in the foss world.

This is still the issue of input & output data bottlenecks.
We have full decode (& presentation) in vdpau but that is a lot of data to have to suck back into filesystem.

A fast CPU works well & works now..

Nero has some linux editing tools (non-free). Badaboom (windozes) does transcoding on nvidia GPU.

---

