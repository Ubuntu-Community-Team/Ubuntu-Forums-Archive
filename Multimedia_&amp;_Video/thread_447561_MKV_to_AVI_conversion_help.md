---
title: "MKV to AVI conversion help"
date: 2007-05-18
forum: Multimedia &amp; Video
---

### Post by harishgayatri on 2007-05-18
I am using 7.04 with mencoder installed.
I am having two movie files in the mkv format,codecs are H.264,Vorbis audio.

I would like to convert them in the XviD format AVI.
while doing so mencoder is giving me some errors
```
Too many audio packets in the buffer: (4101 in 1800715 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.

Flushing video frames
Writing index...
Writing header...
ODML: vprp aspect is 16384:6553.
Setting audio delay to 0.048s.

Video stream: 1039.165 kbit/s  (129895 B/s)  size: 10591676 bytes  81.540 secs  2170 frames

Audio stream:  185.131 kbit/s  (23141 B/s)  size: 1896672 bytes  81.960 secs

```

Please help .
thans in advance...

---

### Post by eye208 on 2007-05-18
Ogg Vorbis audio streams are rarely used in AVI containers. If you want to make the AVI file compatible with standalone DivX/Xvid players, transcode the audio stream to MP3 (constant bitrate).

---

### Post by RawMustard on 2007-05-18
I don't know why your getting the errors you are, but how I would go about doing what you want is: I would extract both streams from the mkv file using mkvextract to movie.avi and movie.ogg.  then I'd use Avidemux to re-encode the avi to xvid format and then re-encode the ogg to mp3. Not sure how you'd do the ogg sound to mp3, not something I've ever done or would want to do, but a quick google search should give a few tips!

---

