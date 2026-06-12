---
title: "DV Audio + Codecs"
date: 2008-03-30
forum: Multimedia &amp; Video
---

### Post by tribunal on 2008-03-30
Hi All!
I have a nice video-camera Sony SR5E
I have found a nice script to convert .ts files to .avi files
It works :)
The only problem I have is here:
at the last stage ffmpeg is working
and what I see:

[I]Opening audio decoder: [libdv] Raw DV Audio Decoder
Unknown/missing audio format -> no sound
ADecoder init failed :(
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
Cannot find codec 'dvaudio' in libavcodec...
ADecoder init failed :(
ADecoder init failed :(
Cannot find codec for audio format 0x56444152.
[/I]

All codecs are installed (may be not all?)
What can I do?

---

### Post by ajmorris on 2008-03-30
hi there,
have you installed the w32codecs package from the medibuntu repositories? (check the end user license agreement to check that they are legal in your area)

AJ

---

### Post by tribunal on 2008-03-30
Yes, w32codecs are installed
As I see, all medibuntu files are installed...
After googling a little, I see:
0x56444152 is id of "Raw DV" in libavcodec
So, ffmpeg should know what is it.
May be I should install anything more?

---

