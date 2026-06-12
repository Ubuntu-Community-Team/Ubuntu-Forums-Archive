---
title: "How to capture/record online video as mp4"
date: 2019-06-21
forum: Multimedia Software
---

### Post by satimis on 2019-06-21
Hi all,

Ubuntu 16.04 desktop

Please advise which is the easy way to capture/record online video as .mp4 file?  The video is running on a webpage (not Youtube nor Facebook)

Thanks in advance

Regards
satimis

---

### Post by Claus7 on 2019-06-21
Hello,

I think that an easy way would be to use kazam. You can install it from the repos and then when opening it you could choose to screencast an area (the area of the video you want to capture). Select the area and press enter. Then click the capture option and let the program record your screen. When satisfied, finish the recording. The option by default would be to save the video in mp4 format.

Regards!

---

### Post by satimis on 2019-06-25
> **Claus7 said:**
> Hello,

I think that an easy way would be to use kazam. You can install it from the repos and then when opening it you could choose to screencast an area (the area of the video you want to capture). Select the area and press enter. Then click the capture option and let the program record your screen. When satisfied, finish the recording. The option by default would be to save the video in mp4 format.

Hi,

Thanks for your advice.

I have tried about 1 day without success.  The problem is no sound.

output file - kazam_a14rvqm0.movie

Preferences -> Screencast
Record with [RAW (AVI)] (the only selection)

Area ->
Sound from speakers (selected)

Regards
satimis

RemarK: The forum didn't advise me by email of your reply.  It has happened occasionally in the past.

---

### Post by Claus7 on 2019-06-25
Hello,

> **satimis said:**
> Hi,

....

Preferences -> Screencast
Record with [RAW (AVI)] (the only selection)

...

I have more than that option available: for example the default is H264 (mp4). Have you installed all available codecs for your system?

Regards!

---

### Post by TheFu on 2019-06-25
SimpleScreenRecorder
It might need a PPA, I don't recall.
It won't record DRM'd content.

---

### Post by satimis on 2019-06-25
> **Claus7 said:**
> 
I have more than that option available: for example the default is H264 (mp4). 
You are collect.  

Others are;
VP8(WEBM)
H264(MP4)
HUFFYUV(AVI)
Lossless JPEG(AVI)

I have tried both H264(MP4) and Lossless JPEG(AVI)

H264(MP4)
2 files created
.movie (an empty file)
.mux

Lossless JPEG(AVI)
an empty .movie file created

> 
Have you installed all available codecs for your system?

What codecs needed?

I can play the online video without problem also having sound.

Regards
satimis

---

### Post by satimis on 2019-06-25
$ xman```

Warning: locale not supported by Xlib, locale set to C
Warning: Cannot convert string "-*-helvetica-medium-r-*-*-*-120-*-*-*-*-*-*" to type FontStruct

```
That window started

> **TheFu said:**
> SimpleScreenRecorder
It might need a PPA, I don't recall.
It won't record DRM'd content.
Noted with thanks

Regards
satimis

---

### Post by TheFu on 2019-06-25
So ... I'm recording the LEN jr Diving competition right now in Kazan using SSR.  Working beautifully.
If it needs any extra stuff, I don't know about it. Always _just works_.  Think it includes the ffmpeg libraries needed.  

I haven't needed to "install" any extra codecs since leaving Windows.  vlc, mpv, mplayer all compile in the codecs.

---

### Post by satimis on 2019-06-25
Hi all,

Finally I solved the problem by installing Firefox add-ons, the Video Downloader.  It is much easier.

Anyway, lot of thanks for your advice.

Regards
satimis

---

