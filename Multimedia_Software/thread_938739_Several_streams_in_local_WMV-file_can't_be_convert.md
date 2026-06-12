---
title: "Several streams in local WMV-file can't be converted"
date: 2008-10-05
forum: Multimedia Software
---

### Post by OttifantSir on 2008-10-05
So far, the best conversion program I have found for Ubuntu is AVIDemux.

It has converted anything I have thrown at it, with the exception of this one file. It is a WMV-file with three video- and audiostreams in different sizes, bitrates and sampling rates.

The codecs are WMA2 and WMV3. I wish to extract the highest-resolution, bitrate and sampling rate streams from this file, but I need some help on how to do this. The result might be a WMV-file, as long as it contains only one stream so I can convert it with AVIDemux.

I guess I probably have to use commandline ffmpeg or mencoder, but don't know in which end to start. (man-pages are too confusing for me. Once tried eight different commandlines to get it to work because there were just too much information)

Anyone ever tried to do this before? If so, please help.

EDIT:

I did try to read the man-pages of ffmpeg, and this is the commandline I came up with:

```
ffmpeg -f mpeg2video -i Natasha.wmv -vcodec mpeg2video -ar 48000 -ab 128 -ac 2 -acodec mp3 natasha.mpg -map 0.2 -map 0.0

```

This, in turn returned this:
```
Seems stream 2 codec frame rate differs from container frame rate: 1000.00 (1000/1) -> 29.97 (30000/1001)

Seems stream 3 codec frame rate differs from container frame rate: 1000.00 (1000/1) -> 29.97 (30000/1001)

Seems stream 5 codec frame rate differs from container frame rate: 1000.00 (1000/1) -> 29.97 (30000/1001)
Input #0, asf, from 'Natasha.wmv':
  Duration: 00:20:01.5, start: 5.000000, bitrate: 1466 kb/s
  Stream #0.0: Audio: wmav2, 48000 Hz, stereo, 128 kb/s
  Stream #0.1: Audio: wmav2, 32000 Hz, stereo, 32 kb/s
  Stream #0.2: Video: wmv3, yuv420p, 320x240, 29.97 fps(r)
  Stream #0.3: Video: wmv3, yuv420p, 320x240, 29.97 fps(r)
  Stream #0.4: Audio: wmav2, 8000 Hz, stereo, 12 kb/s
  Stream #0.5: Video: wmv3, yuv420p, 160x120, 29.97 fps(r)
Output #0, mpeg, to 'natasha.mpg':
  Stream #0.0: Video: mpeg2video, yuv420p, 160x120, q=2-31, 200 kb/s, 29.97 fps(c)
  Stream #0.1: Audio: mp3, 48000 Hz, stereo, 0 kb/s
Stream mapping:
  Stream #0.2 -> #0.0
  Stream #0.0 -> #0.1

```

I believe I have narrowed down the problem: It chooses the lowest resolution stream because the frame rate is different than what it should be. However, forcing a framerate hasn't done anything to improve that.

---

### Post by OttifantSir on 2008-10-16
A week since I started this thread, and noone has yet to come up with something, so I feel I can BUMP this now...

---

### Post by OttifantSir on 2008-10-17
After having tried about 100 (not kidding) different commandlines, I found one that gave me vide in right resolution and audio that sounds ok:

```
ffmpeg -i Natasha.wmv -y -vcodec xvid -s 320x240 -b 512000 -acodec mp3 -ab 128 -ar 22050 -map 0.2 -map 0.0 natasha.avi
```

Still, I don't know whether or not this has extracted/mapped the video- and audio-stream with the highest resolution, sample and bit rate.

Can anyone please tell me what I have done?

---

