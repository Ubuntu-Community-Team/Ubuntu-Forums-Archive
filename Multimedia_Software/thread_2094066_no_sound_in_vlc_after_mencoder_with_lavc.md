---
title: "no sound in vlc after mencoder with lavc"
date: 2012-12-12
forum: Multimedia Software
---

### Post by sslapp on 2012-12-12
I'm using **mencoder** to encode a video with **lavc** codecs:
```
mencoder test.mp4 -ovc copy -oac lavc -lavcopts acodec=ac3:abitrate=64 -o test.avi -audio-preload 0.174
```

The **test.avi** file plays in **vlc** with no sound.

The same video encoded with **avconv**:
```
avconv -i test.mp4 -c:v copy -c:a ac3 -b:a 64k test-ac3.avi
```

plays ok in **vlc** (with sound)

I've been trying to change the codec in **mencoder**:
```
acodec=libmp3lame, acodec=vorbis, ...
```

And all of them plays in **vlc** with no sound.

All the above video files plays ok (with sound) in **mplayer**, **totem** or **smplayer**.

I can't guess if it's a **mencoder** problem, a **vlc** problem or the combination of this two programs.

Here's the output from **Mediainfo** for the test.avi file (encoded with **mencoder**) and test-ac3.avi (encoded with **avconv**).
The audio stream values are the same!

General
Complete name                            : **test-ac3.avi**
Format                                   : AVI
Format/Info                              : Audio Video Interleave
File size                                : 1.57 MiB
Duration                                 : 19s 992ms
Overall bit rate                         : 657 Kbps
Writing application                      : Lavf53.21.0

Video
ID                                       : 0
Format                                   : AVC
Format/Info                              : Advanced Video Codec
Format profile                           : High@L3.0
Format settings, CABAC                   : Yes
Format settings, ReFrames                : 2 frames
Codec ID                                 : avc1
Duration                                 : 19s 981ms
Bit rate                                 : 392 Kbps
Width                                    : 640 pixels
Height                                   : 360 pixels
Display aspect ratio                     : 16:9
Frame rate mode                          : Variable
Frame rate                               : 1 000.000 fps
Color space                              : YUV
Chroma subsampling                       : 4:2:0
Bit depth                                : 8 bits
Scan type                                : Progressive
Bits/(Pixel*Frame)                       : 0.002
Stream size                              : 956 KiB (60%)

**Audio**
ID                                       : 1
Format                                   : AC-3
Format/Info                              : Audio Coding 3
Mode extension                           : CM (complete main)
Codec ID                                 : 2000
Duration                                 : 19s 992ms
Bit rate mode                            : Constant
Bit rate                                 : 64.0 Kbps
Channel(s)                               : 2 channels
Channel positions                        : Front: L R
Sampling rate                            : 44.1 KHz
Bit depth                                : 16 bits
Compression mode                         : Lossy
Stream size                              : 156 KiB (10%)
Alignment                                : Aligned on interleaves
Interleave, duration                     : 35 ms (34.81 video frames)
Interleave, preload duration             : 174 ms

General
Complete name                            : **test.avi**
Format                                   : AVI
Format/Info                              : Audio Video Interleave
File size                                : 1.11 MiB
Duration                                 : 20s 0ms
Overall bit rate                         : 468 Kbps
Writing application                      : MEncoder svn r34540 (Ubuntu), built with gcc-4.6
Writing library                          : MPlayer

Video
ID                                       : 0
Format                                   : AVC
Format/Info                              : Advanced Video Codec
Format profile                           : High@L3.0
Format settings, CABAC                   : Yes
Format settings, ReFrames                : 2 frames
Codec ID                                 : H264
Duration                                 : 20s 0ms
Bit rate                                 : 391 Kbps
Width                                    : 640 pixels
Height                                   : 360 pixels
Display aspect ratio                     : 16:9
Frame rate mode                          : Variable
Frame rate                               : 25.000 fps
Color space                              : YUV
Chroma subsampling                       : 4:2:0
Bit depth                                : 8 bits
Scan type                                : Progressive
Bits/(Pixel*Frame)                       : 0.068
Stream size                              : 956 KiB (84%)

**Audio**
ID                                       : 1
Format                                   : AC-3
Format/Info                              : Audio Coding 3
Mode extension                           : CM (complete main)
Codec ID                                 : 2000
Duration                                 : 19s 992ms
Bit rate mode                            : Constant
Bit rate                                 : 64.0 Kbps
Channel(s)                               : 2 channels
Channel positions                        : Front: L R
Sampling rate                            : 44.1 KHz
Bit depth                                : 16 bits
Compression mode                         : Lossy
Stream size                              : 156 KiB (14%)
Alignment                                : Aligned on interleaves
Interleave, duration                     : 35 ms (0.87 video frame)
Interleave, preload duration             : 174 ms

Any idea?

---

### Post by SeijiSensei on 2012-12-12
The mp3lame library is separate from lavc.  You can convert a video to MP3 audio within the AVI container like this:

```
mencoder test.mp4 -ovc copy -oac mp3lame -lameopts [whatever] -o test.avi -audio-preload 0.174
```

I recommend the [Gentoo guide for mencoder]("http://en.gentoo-wiki.com/wiki/Mencoder").  It has a lot of excellent examples.  The ones using mp3lame are [here](http://en.gentoo-wiki.com/wiki/Mencoder#mp3lame).

---

### Post by sslapp on 2012-12-12
Thank you for your reply.

I can get sound ok with avconv, as I said in my post, or with mencoder and lavc codecs playing it with mplayer or totem.

The question is: why lavc codecs within mencoder doesn't work with vlc?

---

### Post by andrew.46 on 2012-12-12
MEncoder has been rotting on the MPlayer tree for some time now, undeveloped with few bugs fixed. I notice that the MPlayer 2 fork has dropped it completely. If I were you I would not spend time troubleshooting it and move completely to FFmpeg.

---

### Post by mc4man on 2012-12-13
I wouldn't bother with mencoder either

You may see something in vlc messages
(- Open vlc & before starting vid go Tools > Messages
Raise the verbosity to  2, start the vid & browse thru the message output (or save it to a text file to read.

---

### Post by sslapp on 2012-12-13
@mc4man:
I've done your suggestion and here's the partial result:

```
main debug: filter(s) 'a52 '->'f32l' 44100 Hz->44100 Hz Dolby->Dolby
main debug: looking for audio filter module: 14 candidates
**main debug: using audio filter module "a52tofloat32"**
main debug: TIMER module_need() : 0.529 ms - Total 0.529 ms / 1 intvls (Avg 0.529 ms)
main debug: conversion pipeline completed
main debug: filter(s) 'f32l'->'f32l' 44100 Hz->44100 Hz Dolby->Dolby
main debug: conversion pipeline completed
main debug: filter(s) 'f32l'->'f32l' 48510 Hz->44100 Hz Dolby->Dolby
main debug: looking for audio filter module: 14 candidates
main debug: using audio filter module "samplerate"
main debug: TIMER module_need() : 0.146 ms - Total 0.146 ms / 1 intvls (Avg 0.146 ms)
main debug: conversion pipeline completed
**[COLOR="Red"]main warning: PTS is out of range (9328788), dropping buffer[/COLOR]**
pulse debug: listing sink alsa_output.pci-0000_00_1b.0.analog-stereo (44): Audio Interno Estéreo analógico
pulse debug: base volume: 65536
**[COLOR="Red"]avi warning: cannot get packet header, track disabled[/COLOR]**
```

The audio codec selected seems to be ok, but those lines in red appear in debug messages when video ends playing.

---

