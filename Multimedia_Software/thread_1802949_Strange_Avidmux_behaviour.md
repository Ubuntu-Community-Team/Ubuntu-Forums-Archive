---
title: "Strange Avidmux behaviour"
date: 2011-07-12
forum: Multimedia Software
---

### Post by coldraven on 2011-07-12
I just tried Avidmux gtk then removed it and installed Avidmux qt, they both did the same thing. I had applications on all four desktops then Avidmux (desktop 2) crashed and all apps including Avidmux ended up on desktop 1. Also the desktop switching panel changed into a Win98 style! Even more strange Avidmux actually did the transcoding that I had selected.
The file was a 1920 x 1080 AVI (15MB) with ITU H.264 video and DVI ADPCM 48kHz sound.
It gave a warning about frame rate, I selected the NO option.
>  H.264 detected   If the file is using B-frames as reference it can lead to a crash or stuttering.
Avidemux can use another mode which is safe but YOU WILL LOSE FRAME ACCURACY.
Do you want to use that mode?
Follwed by >   Index is not up to date
You should use Tool->Rebuild frame. Do it now ?
I don't remember what response I gave to that
What am I doing wrong? Is there another version of Avidmux?

---

### Post by BicyclerBoy on 2011-07-12
I have not used AviDemux much because it does not support LATM-AAC...

As AviDemux was still running on the desktop workspace, it didn't crash.(unless it supports auto-restart).
I would guess that the desktop effects manager crashed so the desktop then looks like std. classic gnome with no effects.
Maybe you run out of ram..

AFAIK.
H264 video uses I B(n) P frames, frame accurate cutting is not so simple.
Cutting at I frames is simple. (possibly not frame accurate).
Cutting at B & P frames requires re-encoding all B(n) & P frames back to previous I frame & new I frame to be placed at cut & re-encoding all Bs & P frames to the next I frame.
I not sure AviDemux can do this properly..

Indexing is required on variable bit rate & out-of order video encoding because..
Video using IBP frames encodes the frames in different order to the presentation because Bs & P requires the I and the Bs require I & P.
An index of I frames allows fast seeking..
Some botched containers (like avi) use packed B frames so predicting/calculating framerates/indexes is problematic.

---

### Post by coldraven on 2011-07-13
> **BicyclerBoy said:**
> I have not used AviDemux much because it does not support LATM-AAC...

As AviDemux was still running on the desktop workspace, it didn't crash.(unless it supports auto-restart).
I would guess that the desktop effects manager crashed so the desktop then looks like std. classic gnome with no effects.
Maybe you run out of ram..

AFAIK.
H264 video uses I B(n) P frames, frame accurate cutting is not so simple.
Cutting at I frames is simple. (possibly not frame accurate).
Cutting at B & P frames requires re-encoding all B(n) & P frames back to previous I frame & new I frame to be placed at cut & re-encoding all Bs & P frames to the next I frame.
I not sure AviDemux can do this properly..

Indexing is required on variable bit rate & out-of order video encoding because..
Video using IBP frames encodes the frames in different order to the presentation because Bs & P requires the I and the Bs require I & P.
An index of I frames allows fast seeking..
Some botched containers (like avi) use packed B frames so predicting/calculating framerates/indexes is problematic.


Thanks BicyclerBoy, I think you are correct about Compiz crashing. I have 4GB, you would think that was enough! I'm new at video transcoding so have to learn the hard way. I was trying to convert some AVI (high def I suppose) clips for upload to YouTube.

---

### Post by BicyclerBoy on 2011-07-15
I'm not sure if AviDemux uses shared ubuntu ffmpeg libs or is self contained..

Could try building AviDemux from source or.. try upgrading ffmpeg lavf by building it yourself.

Could transcode with Handbrake into a good container mkv or mpeg4.

---

