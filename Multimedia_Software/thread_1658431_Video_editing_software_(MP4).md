---
title: "Video editing software (MP4)??"
date: 2011-01-02
forum: Multimedia Software
---

### Post by puntigamer on 2011-01-02
Hallo,
I'm seraching a video editor, that can play and edit/convert MP4 videos. I've already tried many of them, but they play it laggy and I bacome a terrible video.
Any ideas? Perhaps I missed to download some codecs?

(ATI RADEON HD 4500, Ubuntu 32-bit)

Thanks

---

### Post by BicyclerBoy on 2011-01-02
Can you playback any video correctly ?
DVD or mpeg-ts H264 AVC ?

If playback is the main problem then it is likely related to the video driver of the AMD/ATI GPU. Linux video & AMD/ATI do not make a good combination
And playback could be codec related as well.

I assume that your mp4 video is MPEG-4 AVC H264.
Real time linear editing of H264 material would require seriously powerful PC &/or use of the GPU. This is not a trivial software problem.

You could get real time playback 1080p with GPU acceleration or core2duo CPU maxed out.
Encoding is another matter entirely.
Tools like ffmpeg & x264 are needed.

MP4 can contain mpeg-2 or 1 video ...

Nero Badaboom (non-free) is purported to do GPU H264 real time. Linux version ?

All conversion/transcoding is slow & likely to be lossy.

I believe the best common practice is to convert to a lossless (very big files) format for all editing & post process to final format.

H264 AVC is a complex multi-frame compression method & as such is not suited to direct linear editing.

So I would try to convert with ffmpeg to mpeg-2 or similar & use PiTiVi or Cinnelerra etc to edit..Use ffmpeg-x264 to re-encode to anything ..

The Nero s/w only worked with nvidia GPU ..this may or may not be the situation now.

---

### Post by puntigamer on 2011-01-03
Thanks, I will download the encoder, and keep trying:)
I use Pitivi editor and Transmageddon encoder, but the converted AVI/OGG files will be laggy too.
I can play everything, what is not MP4! (HD videos, Avi, DivX)
And I have a Core 2 Duo (2,1 GHZ).
Ah, why they can't just record in OGG? :)

---

### Post by no2498 on 2011-01-03
some disagree with me but if you install smplayer it lodes some more 264 codes

type it in a terminal it tells you how to install it

---

### Post by BicyclerBoy on 2011-01-03
The theora/ogg combination will have a similar computational requirements to MPEG-4/AVC(H264 AAC).

Compressed video needs horsepower.

You should be able to playback some h264 material on your CPU.
I have no problem playing 1080i HD on 50% core2duo (CPU decode).
That problem could be the ATI radeon driver.

AFAIK There are 2 transcoding projects in Linux: ffmpeg & gstreamer.
Everything (including lots of windoze progs) depends on these.

GUI programs like HandBrake or AviDemux or WinFF could be options.

---

