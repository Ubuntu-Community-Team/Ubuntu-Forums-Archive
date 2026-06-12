---
title: "What are the correct paramaters for avconv to reduce avi file size?"
date: 2014-05-26
forum: Multimedia Software
---

### Post by Bobby_James on 2014-05-26
I have an avi file which I created on my camera which is 130MB for 1 minute length.

The details are: 640x480, Motion JPEG, 30 fps.

I want to convert this into something rather smaller while, more or less, maintaining the quality.

The obvious program seems to be avconv but I've no idea what the parameters are.  All the ones that I've tried just give errors such as "Error while opening encoder for output stream #0:0 - maybe incorrect parameters such as bit_rate, rate, width or height"

Any ideas. Thanks.

---

### Post by papibe on 2014-05-26
Hi Bobby_James.

It would be valuable to check all details about your file. Could you install the program 'mediainfo'?
```
sudo apt-get update

sudo apt-get install mediainfo
```
and then post the output of this:
```
mediainfo /path/to/your/file.avi
```
(where /path/to/your/file.avi is the path to your actual movie file).

Regards.

---

### Post by Bobby_James on 2014-05-26
```

Format                                   : AVI
Format/Info                              : Audio Video Interleave
File size                                : 124 MiB
Duration                                 : 1mn 6s
Overall bit rate                         : 15.7 Mbps
Mastered date                            : Fri May 23 14:57:26 2014
Writing application                      : CanonMVI06

Video
ID                                       : 0
Format                                   : JPEG
Codec ID                                 : MJPG
Duration                                 : 1mn 6s
Bit rate                                 : 14.9 Mbps
Width                                    : 640 pixels
Height                                   : 480 pixels
Display aspect ratio                     : 4:3
Frame rate                               : 30.000 fps
Color space                              : YUV
Chroma subsampling                       : 4:2:2
Bit depth                                : 8 bits
Scan type                                : Progressive
Compression mode                         : Lossy
Bits/(Pixel*Frame)                       : 1.622
Stream size                              : 119 MiB (95%)

Audio
ID                                       : 1
Format                                   : PCM
Format settings, Endianness              : Little
Format settings, Sign                    : Signed
Codec ID                                 : 1
Duration                                 : 1mn 6s
Bit rate mode                            : Constant
Bit rate                                 : 705.6 Kbps
Channel(s)                               : 1 channel
Sampling rate                            : 44.1 KHz
Bit depth                                : 16 bits
Stream size                              : 5.60 MiB (5%)
Interleave, duration                     : 993 ms (29.79 video frames)
Interleave, preload duration             : 1000 ms

```

---

### Post by papibe on 2014-05-26
Thanks.

The most common container these days are either mkv or mp4 (using x264, and aac for audio or mp3).

Something like this should work for an mp4 (x264 and mp3):
```
avconv -i movie.avi -vcodec libx264 -acodec libmp3lame -ac 2  movie.mp4 
```
(tested on 12.04 32bits using avconv version 0.8.10-4:0.8.10-0ubuntu0.12.04.1)

Hope it helps. Let us know how that goes.
Regards.

---

### Post by Bobby_James on 2014-05-26
Thanks - super effective.

Reduced the file size by about 90%

---

