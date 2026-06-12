---
title: "Video file size comparison."
date: 2013-02-20
forum: Multimedia Software
---

### Post by Geffers on 2013-02-20
Folks,

Enquiry for a friend, he has recorded two programs; one is over DOUBLE the file size but checking ffmpeg output not sure why so much bigger.

The bigger file is a little longer in duration but only 12 mins on a 84 minute movie, encoding diomensions are slightly bigger BUT video bit rate is actually LOWER.

Anyone cast an idea why the much bigger file size; output file attached..



Geffers

---

### Post by BicyclerBoy on 2013-02-20
Could check/compare the files with "mediainfo".
Post the terminal/text output from each..

Often ffmpeg/ffprobe needs to look further into files to get actual measure of bitrates..
Could try with:
ffprobe -analyzeduration 3000000  -i myvideo.mpg

The reported bitrate could be max peak & not average.
Your data is a little ambiguous w.r.t. video codec & settings.

---

### Post by Geffers on 2013-02-20
> **BicyclerBoy said:**
> Could check/compare the files with "mediainfo".
Post the terminal/text output from each..

Often ffmpeg/ffprobe needs to look further into files to get actual measure of bitrates..
Could try with:
ffprobe -analyzeduration 3000000  -i myvideo.mpg

The reported bitrate could be max peak & not average.
Your data is a little ambiguous w.r.t. video codec & settings.

Thanks, I'll try and get him to send me that info; thanks for the advice.

I'll post it when I receive it from him.

Geffers

---

