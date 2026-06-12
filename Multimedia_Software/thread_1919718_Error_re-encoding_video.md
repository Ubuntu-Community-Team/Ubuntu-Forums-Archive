---
title: "Error re-encoding video"
date: 2012-02-03
forum: Multimedia Software
---

### Post by trbone on 2012-02-03
I am trying to reduce the size of some of the videos that I have taken with my camera. I am using traGtor and I keep on getting a similar error message. 

The error message is

> Input #0, avi, from '/media/8CA0-95AB/MyPhotos/Archive/2012-01-29/DSCN0297.AVI':
Metadata:
encoder         :
maker           : NIKON
model           : COOLPIX S4150
creation_time   : 2012-01-29 03:48:40
Duration: 00:07:15.16, start: 0.000000, bitrate: 32085 kb/s
Stream #0.0: Video: mjpeg, yuvj422p, 1280x720, 30 tbr, 30 tbn, 30 tbc
Stream #0.1: Audio: pcm_s16le, 22050 Hz, 1 channels, s16, 352 kb/s
Incompatible sample format 's16' for codec 'ac3', auto-selecting format 'flt'
Incompatible pixel format 'yuvj422p' for codec 'mpeg4', auto-selecting format 'yuv420p'
[buffer @ 0x872540] w:1280 h:720 pixfmt:yuvj422p
[ffsink @ 0x884b40] auto-inserting filter 'auto-inserted scaler 0' between the filter 'src' and the filter 'out'
[scale @ 0x86e3c0] w:1280 h:720 fmt:yuvj422p -> w:1280 h:720 fmt:yuv420p flags:0x4
[mpeg4 @ 0x8679c0] timebase 33333/1000000 not supported by MPEG 4 standard, the maximum admitted value for the timebase denominator is 65535
Output #0, mp4, to '/media/8CA0-95AB/MyPhotos/Archive/2012-01-29/birthday rueda.mp4':
Stream #0.0: Video: mpeg4, yuv420p, 1280x720 [PAR 1:1 DAR 16:9], q=2-31, 2500 kb/s, 90k tbn, 30 tbc
Stream #0.1: Audio: ac3, 22050 Hz, 1 channels, flt, 128 kb/s
Stream mapping:
Stream #0.0 -> #0.0
Stream #0.1 -> #0.1
Error while opening encoder for output stream #0.0 - maybe incorrect parameters such as bit_rate, rate, width or height
According to traGtor the command line that was used was 

> ffmpeg -i '/media/8CA0-95AB/MyPhotos/Archive/2012-01-29/DSCN0297.AVI' -map 0.0 -map 0.1 -y -f mp4 -er 3 -acodec ac3 -ab 128k -ar 22050 -ac 1 -b 2500k -vcodec mpeg4 '/media/8CA0-95AB/MyPhotos/Archive/2012-01-29/birthday rueda.mp4'I'm not very technically advanced, so I would appreciate any help in resolving this problem. If you require any further information just let me know what command to type. 

Oh, and I'm running Ubuntu 11.1...

Thanks

T

---

### Post by nhtrader on 2012-06-13
> **trbone said:**
> 

I'm not very technically advanced, so I would appreciate any help in resolving this problem. If you require any further information just let me know what command to type. 

```

Stream #0.0: Video: mjpeg, yuvj422p, 1280x720, 30 tbr, 30 tbn, 30 tbc
Stream #0.1: Audio: pcm_s16le, 22050 Hz, 1 channels, s16, 352 kb/s
 
ffmpeg -i '/media/8CA0-95AB/MyPhotos/Archive/2012-01-29/DSCN0297.AVI' -map 0.0 -map 0.1 -y -f mp4 -er 3 -acodec ac3 -ab 128k -ar 22050 -ac 1 -b 2500k -vcodec mpeg4 '/media/8CA0-95AB/MyPhotos/Archive/2012-01-29/birthday rueda.mp4'

```


I see that you're using the ac3 audio codec, but the info shows that the audio stream uses pcm_s16le. I don't know if this will work, but try replacing -acodec ac3 with -acodec pcm_s16le

Plus, if you want to know if you have the pcm_s16le codec, use the command
ffmpeg -codecs

---

