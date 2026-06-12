---
title: "Mencoder can't see libdv"
date: 2010-02-12
forum: Multimedia Software
---

### Post by squaregoldfish on 2010-02-12
Hi all,

I've just been trying to convert a video to DV format, but mencoder doesn't know about libdv.

Using the command:

```
mencoder -oac pcm -ovc libdv -ofps 25 -noskip -o video.dv video.wmv
```I get the following output:

```
MEncoder UNKNOWN-4.4.1 (C) 2000-2009 MPlayer Team
success: format: 0  data: 0x0 - 0x964d51
ASF file format detected.
[asfheader] Audio stream found, -aid 1
[asfheader] Video stream found, -vid 2
VIDEO:  [WMV1]  320x240  24bpp  1000.000 fps    0.0 kbps ( 0.0 kbyte/s)
[V] filefmt:6  fourcc:0x31564D57  size:320x240  fps:1000.000  ftime:=0.0010
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 32000 Hz, 2 ch, s16le, 32.0 kbit/3.12% (ratio: 4000->128000)
Selected audio codec: [ffwmav2] afm: ffmpeg (DivX audio v2 (FFmpeg))
==========================================================================
Couldn't find video filter 'libdv'.
Failed to open the encoder.

```The list of codecs mencoder knows about is:

```
$mencoder -ovc help
MEncoder UNKNOWN-4.4.1 (C) 2000-2009 MPlayer Team

Available codecs:
   copy     - frame copy, without re-encoding. Doesn't work with filters.
   frameno  - special audio-only file for 3-pass encoding, see DOCS.
   raw      - uncompressed video. Use fourcc option to set format explicitly.
   nuv      - nuppel video
   lavc     - libavcodec codecs - best quality!
   xvid     - XviD encoding
   x264     - H.264 encoding

```

There's clearly no DV option there, even though the libdv package is installed on my machine.

How can I get mencoder to find the codec? Is there a specific place it looks for them?

Thanks,
Steve.

---

### Post by andrew.46 on 2010-02-12
Hi squaregoldfish,

> **squaregoldfish said:**
> How can I get mencoder to find the codec? Is there a specific place it looks for them?

What you need to see is:

```

andrew@skamandros~$ mencoder -ovc help
**[COLOR="Blue"]MEncoder SVN-r30529-4.3.3 (C) 2000-2010 MPlayer Team[/COLOR]**

Available codecs:
   copy     - frame copy, without re-encoding. Doesn't work with filters.
   frameno  - special audio-only file for 3-pass encoding, see DOCS.
   raw      - uncompressed video. Use fourcc option to set format explicitly.
   nuv      - nuppel video
   lavc     - libavcodec codecs - best quality!
   vfw      - VfW DLLs, read DOCS/HTML/en/encoding-guide.html.
   qtvideo  - QuickTime DLLs, currently only SVQ1/3 are supported.
  **[COLOR="Blue"] libdv    - DV encoding with libdv v0.9.5[/COLOR]**
   xvid     - XviD encoding
   x264     - H.264 encoding

```

and you can achieve this by compiling MPlayer / MEncoder against libdv. I will admit that I have not tested libdv encoding with MEncoder in this way and more specifically I have never tried encoding *to wmv *with MEncoder.

There are a few guides on these forums for compiling the svn MPlayer, these for the most part simply need a few tweaks to also build MEncoder and allow the support you are after.

All the best,

Andrew

---

### Post by squaregoldfish on 2010-02-12
Hmm. Surprising that the packaged mplayer isn't compiled for this. I'm sure it used to be - I dug this command out of a script I last used about a year ago, so it clearly worked then, and I could have sworn I've never compiled mplayer myself.

No matter. I'll see what I can do over the weekend.

Steve.

---

### Post by andrew.46 on 2010-02-12
Hi squaredgoldfish,

> **squaregoldfish said:**
> Hmm. Surprising that the packaged mplayer isn't compiled for this. I'm sure it used to be - I dug this command out of a script I last used about a year ago, so it clearly worked then, and I could have sworn I've never compiled mplayer myself.

Not sure about the repository MEncoder but I have just taken your cmmand for a whirl and it certainly works well enough, and of course you are converting to dv not wmv as my previous post suggested :). My completed transcode, tested with mediainfo, was:

```

andrew@skamandros:~/Desktop/share$ **[COLOR="Red"]mediainfo -f test.dv [/COLOR]**
General
Count                            : 259
Count of stream of this kind     : 1
Kind of stream                   : General
Kind of stream                   : General
Stream identifier                : 0
Count of video streams           : 1
Count of audio streams           : 1
[B][COLOR="Red"]Video_Format_List                : Digital Video
Video_Format_WithHint_List       : Digital Video (Sony)
Codecs Video                     : Sony DV
Audio_Format_List                : PCM
Audio_Format_WithHint_List       : PCM (Microsoft)
Audio codecs                     : PCM[/COLOR][/B]
Complete name                    : test.dv
File name                        : test.dv
File extension                   : dv
Format                           : AVI
Format                           : AVI
Format/Info                      : Audio Video Interleave
Format/Extensions usually used   : avi
Interleaved                      : Yes
Codec                            : AVI
Codec                            : AVI
Codec/Info                       : Audio Video Interleave
Codec/Extensions usually used    : avi
File size                        : 741873036
File size                        : 708 MiB
File size                        : 708 MiB
File size                        : 708 MiB
File size                        : 708 MiB
File size                        : 707.5 MiB
Duration                         : 234000
Duration                         : 3mn 54s
Duration                         : 3mn 54s 0ms
Duration                         : 3mn 54s
Duration                         : 00:03:54.000
Overall bit rate                 : 25363180
Overall bit rate                 : 25.4 Mbps
Stream size                      : 155436
Stream size                      : 152 KiB (0%)
Stream size                      : 152 KiB
Stream size                      : 152 KiB
Stream size                      : 152 KiB
Stream size                      : 151.8 KiB
Stream size                      : 152 KiB (0%)
Proportion of this stream        : 0.00021
Recorded date                    : 2010-02-13 10:34:13
File last modification date      : UTC 2010-02-12 23:37:48
File last modification date (loc : 2010-02-13 10:37:48
[B][COLOR="Red"]Writing application              : MEncoder SVN-r30529-4.3.3
Writing library                  : MPlayer
Writing library                  : MPlayer[/COLOR][/B]

Video
Count                            : 148
Count of stream of this kind     : 1
Kind of stream                   : Video
Kind of stream                   : Video
Stream identifier                : 0
ID                               : 0
ID                               : 0
[B][COLOR="Red"]Format                           : Digital Video
Codec ID                         : dvsd
Codec ID/Hint                    : Sony
Codec                            : dvsd
Codec                            : Sony DV
Codec/Family                     : DV
Codec/Info                       : Sony Digital Video (DV) 525 lines at 29.97 Hz or 625 lines at 25.00 Hz
Codec/CC                         : dvsd[/COLOR][/B]
Duration                         : 233480
Duration                         : 3mn 53s
Duration                         : 3mn 53s 480ms
Duration                         : 3mn 53s
Duration                         : 00:03:53.480
Bit rate                         : 24000000
Bit rate                         : 24.0 Mbps
Width                            : 720
Width                            : 720 pixels
Height                           : 480
Height                           : 480 pixels
Pixel aspect ratio               : 1.000
Original pixel aspect ratio      : 0.889
Display aspect ratio             : 1.500
Display aspect ratio             : 1.500
Original display aspect ratio    : 1.333
Original display aspect ratio    : 4:3
Frame rate mode                  : CFR
Frame rate mode                  : Constant
Frame rate                       : 25.000
Frame rate                       : 25.000 fps
Original frame rate              : 29.970
Original frame rate              : 29.970 fps
Frame count                      : 5837
Standard                         : NTSC
Resolution                       : 24
Resolution                       : 24 bits
Colorimetry                      : 4:1:1
Scan type                        : Interlaced
Scan type                        : Interlaced
Interlacement                    : Interlaced
Interlacement                    : Interlaced
Bits/(Pixel*Frame)               : 2.778
Stream size                      : 700440000
Stream size                      : 668 MiB (94%)
Stream size                      : 668 MiB
Stream size                      : 668 MiB
Stream size                      : 668 MiB
Stream size                      : 668.0 MiB
Stream size                      : 668 MiB (94%)
Proportion of this stream        : 0.94415
Encoding settings                : ae mode=manual / wb mode=hold / white balance=candle / fcm=manual focus

Audio
Count                            : 129
Count of stream of this kind     : 1
Kind of stream                   : Audio
Kind of stream                   : Audio
Stream identifier                : 0
Format                           : PCM
Format settings                  : Little / Unsigned
Format settings, Endianness      : Little
Format settings, Sign            : Unsigned
Codec ID                         : 1
Codec ID/Hint                    : Microsoft
Codec ID/Url                     : http://www.microsoft.com/windows/
[B][COLOR="Red"]Codec                            : PCM
Codec                            : PCM
Codec/Family                     : PCM
Codec/Info                       : Microsoft PCM[/COLOR][/B]
Codec/Url                        : http://www.microsoft.com/windows/
Codec/CC                         : 1
Codec settings                   : Little / Unsigned
Codec settings, Endianness       : Little
Codec settings, Sign             : Unsigned
Duration                         : 234000
Duration                         : 3mn 54s
Duration                         : 3mn 54s 0ms
Duration                         : 3mn 54s
Duration                         : 00:03:54.000
Bit rate mode                    : CBR
Bit rate mode                    : Constant
Bit rate                         : 1411200
Bit rate                         : 1 411.2 Kbps
Channel(s)                       : 2
Channel(s)                       : 2 channels
Sampling rate                    : 44100
Sampling rate                    : 44.1 KHz
SamplingCount                    : 10319400
Resolution                       : 16
Resolution                       : 16 bits
Stream size                      : 41277600
Stream size                      : 39.4 MiB (6%)
Stream size                      : 39 MiB
Stream size                      : 39 MiB
Stream size                      : 39.4 MiB
Stream size                      : 39.37 MiB
Stream size                      : 39.4 MiB (6%)
Proportion of this stream        : 0.05564
Interleave, duration             : 12.47
Interleave, duration             : 499
Interleave, duration             : 499 ms (12.47 video frames)
Interleave, preload duration     : 500
Interleave, preload duration     : 500 ms

```

Andrew

---

