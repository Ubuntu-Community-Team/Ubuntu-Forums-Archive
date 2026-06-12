---
title: "wmv to avi? any ideas?"
date: 2008-03-23
forum: Multimedia &amp; Video
---

### Post by bigfoot1979 on 2008-03-23
Hi, 

I'm trying to convert some of my wmv files to avi ... any ideas how to do it?

tried this 

mencoder infile.wmv -ofps 23.976 -ovc lavc -oac copy -o outfile.avi

however, I get no sound.

Many thanks for any input

---

### Post by adityakavoor on 2008-03-23
Have you tried ffmpeg ?

```
sudo apt-get install ffmpeg
```

then :

```

ffmpeg -i <inputfile.wmv> <outputfile.avi>

```

Hope this helps :)

---

### Post by bigfoot1979 on 2008-03-23
thanks. I tried it but I got this out of the terminal

Seems stream 1 codec frame rate differs from container frame rate: 1000.00 (1000/1) -> 15.00 (15/1)
Input #0, asf, from 'Instructor.wmv':
  Duration: 00:01:19.5, start: 5.000000, bitrate: 70 kb/s
  Stream #0.0: Audio: 0x000a, 22050 Hz, mono, 20 kb/s
  Stream #0.1: Video: wmv3, yuv420p, 800x600, 15.00 fps(r)
Output #0, avi, to 'instructorCON.avi':
  Stream #0.0: Video: mpeg4, yuv420p, 800x600, q=2-31, 200 kb/s, 15.00 fps(c)
  Stream #0.1: Audio: mp2, 22050 Hz, mono, 64 kb/s
Stream mapping:
  Stream #0.1 -> #0.0
  Stream #0.0 -> #0.1
Unsupported codec (id=0) for input stream #0.0

Is there a problem with the audio codecs?

---

### Post by adityakavoor on 2008-03-23
```
 sudo apt-get install w32codecs
```

---

