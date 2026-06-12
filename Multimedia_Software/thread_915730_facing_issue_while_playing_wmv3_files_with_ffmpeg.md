---
title: "facing issue while playing wmv3 files with ffmpeg"
date: 2008-09-10
forum: Multimedia Software
---

### Post by ajay.parashar on 2008-09-10
I am playing wmv3 files using ffmpeg .
I m using only file parser of ffmpeg not its decoding & rendring stuff.
ffmpeg parse my video file & put data in packets,
then i stream these packets to my hardware.
In case of mpeg2 it works fine,
but for wmv3 i need to insert some code frame by frame .
How can i come to know when one frame finishes & second starts.
i tried to use folowwing data structure to get frame_size
AVFormatContext->streams[0]->codec->frame_size

but it does not work , it give value 0 for frame_size as well as for nb_frames.

Please do the needful.

Regards
Ajay Parashar

---

