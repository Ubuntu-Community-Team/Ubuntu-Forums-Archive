---
title: "[SOLVED] wmv to avi - neither mencoder nor ffmpeg did work"
date: 2008-03-11
forum: Multimedia &amp; Video
---

### Post by thomas7.10 on 2008-03-11
Hi

I try to convert a wmv file to a avi file.


On mencoder i used that command:

```
mencoder infile.wmv -ofps 23.976 -ovc lavc -oac copy -o outfile.avi
```

And the error i got was:

```

ODML: Aspect information not (yet?) available or unspecified, not writing vprp header.

Video stream:  489.794 kbit/s  (61224 B/s)  size: 62033749 bytes  1013.222 secs  25304 frames

Audio stream:  128.040 kbit/s  (16004 B/s)  size: 16190958 bytes  1011.619 secs
```

Then i tried it with ffmpeg.

I used that command (it was a combination of a bit of the manpage and a bigger part of guessing):

```
ffmpeg -i infile.wmv outfile.avi
```

the error i got here was:

```

Seems stream 1 codec frame rate differs from container frame rate: 1000.00 (1000/1) -> 25.00 (25/1)
Input #0, asf, from 'infile.wmv':
  Duration: 02:14:27.0, start: 3.000000, bitrate: 49 kb/s
  Stream #0.0: Audio: 0x0162, 44100 Hz, stereo, 128 kb/s
  Stream #0.1: Video: wmv3, yuv420p, 360x288, 25.00 fps(r)
Output #0, avi, to 'outfile.avi':
  Stream #0.0: Video: mpeg4, yuv420p, 360x288, q=2-31, 200 kb/s, 25.00 fps(c)
  Stream #0.1: Audio: mp2, 44100 Hz, stereo, 64 kb/s
Stream mapping:
  Stream #0.1 -> #0.0
  Stream #0.0 -> #0.1

```

Could someone please help me with that?

Thomas

---

### Post by thomas7.10 on 2008-03-12
Now i tried it again with mencoder. I used that command:

```
mencoder infile.wmv -o outfile.avi -ovc lavc -oac mp3lame
```

The error I got here was:

```
MEncoder 2:1.0~rc1-0ubuntu13.1 (C) 2000-2006 MPlayer Team
CPU: Intel(R) Core(TM)2 CPU          6300  @ 1.86GHz (Family: 6, Model: 15, Stepping: 6)
CPUflags: Type: 6 MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
Compiled with runtime CPU detection.
success: format: 0  data: 0x0 - 0x3000000
ASF file format detected.
VIDEO:  [WMV3]  360x288  24bpp  25.000 fps    0.0 kbps ( 0.0 kbyte/s)
[V] filefmt:6  fourcc:0x33564D57  size:360x288  fps:25.00  ftime:=0.0400
==========================================================================
Opening audio decoder: [dmo] Win32/DMO decoders
Win32 LoadLibrary failed to load: wma9dmod.dll, /usr/lib/win32/wma9dmod.dll, /usr/local/lib/win32/wma9dmod.dll
IMediaObject ERROR: 0x86c5be6  could not open DMO DLL (0x0 : 0)
ERROR: Could not open required DirectShow codec wma9dmod.dll.
ADecoder preinit failed :(
ADecoder init failed :(
Opening audio decoder: [dmo] Win32/DMO decoders
Win32 LoadLibrary failed to load: wmadmod.dll, /usr/lib/win32/wmadmod.dll, /usr/local/lib/win32/wmadmod.dll
IMediaObject ERROR: 0x86c5be6  could not open DMO DLL (0x0 : 0)
ERROR: Could not open required DirectShow codec wmadmod.dll.
ADecoder preinit failed :(
ADecoder init failed :(
Cannot find codec for audio format 0x162.
Read DOCS/HTML/en/codecs.html!
==========================================================================
Opening video filter: [expand osd=1]
Expand: -1 x -1, -1 ; -1, osd: 1, aspect: 0.000000, round: 1
==========================================================================
Opening video decoder: [dmo] DMO video codecs
Win32 LoadLibrary failed to load: wmv9dmod.dll, /usr/lib/win32/wmv9dmod.dll, /usr/local/lib/win32/wmv9dmod.dll
IMediaObject ERROR: 0x86c5be6  could not open DMO DLL (0x0 : 0)
Failed to create DMO filter
ERROR: Could not open required DirectShow codec wmv9dmod.dll.
You need to upgrade/install the binary codecs package.
Go to http://www.mplayerhq.hu/dload.html
VDecoder init failed :(
Opening video decoder: [dmo] DMO video codecs
Win32 LoadLibrary failed to load: wmvdmod.dll, /usr/lib/win32/wmvdmod.dll, /usr/local/lib/win32/wmvdmod.dll
IMediaObject ERROR: 0x86c5be6  could not open DMO DLL (0x0 : 0)
Failed to create DMO filter
ERROR: Could not open required DirectShow codec wmvdmod.dll.
You need to upgrade/install the binary codecs package.
Go to http://www.mplayerhq.hu/dload.html
VDecoder init failed :(
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffwmv3] vfm: ffmpeg (FFmpeg M$ WMV3/WMV9)
==========================================================================
VDec: vo config request - 360 x 288 (preferred colorspace: Planar YV12)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is undefined - no prescaling applied.
videocodec: libavcodec (360x288 fourcc=34504d46 [FMP4])
Writing header...
ODML: Aspect information not (yet?) available or unspecified, not writing vprp header.
Writing header...
ODML: Aspect information not (yet?) available or unspecified, not writing vprp header.
Pos: 524.8s  13119f ( 6%) 228.23fps Trem:  14min 455mb  A-V:0.000 [462:0]
Too many audio packets in the buffer: (2822 in 8389806 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.
Pos: 524.8s  13120f ( 6%) 228.24fps Trem:  14min 455mb  A-V:0.000 [462:0]
Too many audio packets in the buffer: (2822 in 8389806 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.

Flushing video frames
Writing index...
Writing header...
ODML: Aspect information not (yet?) available or unspecified, not writing vprp header.

Video stream:  462.166 kbit/s  (57770 B/s)  size: 30318080 bytes  524.800 secs  13120 frames

```

---

### Post by thomas7.10 on 2008-03-12
I downloaded the missing dll  files and now it says again:

```
Flushing video frames
Writing index...
Writing header...
ODML: Aspect information not (yet?) available or unspecified, not writing vprp header.

Video stream:  488.931 kbit/s  (61116 B/s)  size: 61837571 bytes  1011.800 secs  25304 frames

Audio stream:  191.885 kbit/s  (23985 B/s)  size: 24236114 bytes  1010.442 secs

```

---

### Post by andrew.46 on 2008-03-13
Hi,

 Can you post the file somewhere?

     Andrew

---

### Post by thomas7.10 on 2008-03-15
Yes that was the problem the file was bad from the beginning.

Thanks anyway ;)

---

