---
title: "Problem with libmp3lame"
date: 2009-02-14
forum: Multimedia Software
---

### Post by knattlhuber on 2009-02-14
I'm trying to play a .wmv video but I don't get any audio. When I try to convert the video, WinFF complains about an unsupported audio codec. According to the terminal output, it's libmp3lame.
Oddly, libmp3lame is installed and there's a libmp3lame.s.0.0.0 file in /usr/lib. I created a sym link libmp3lame.so pointing to that file but still no audio.
Any suggestions on how to make Ubuntu find the codec? I'm on 64-bit Intrepid.

---

### Post by benerivo on 2009-02-14
What does WinFF say, exactly?

---

### Post by djbushido on 2009-02-14
Also, did you compile libmp3lame yourself?
I assume you used the repos, so instead, go to here:[http://lame.sourceforge.net/download.php](http://lame.sourceforge.net/download.php)
download the source tarball, move to that directory, and do this code:
```
./configure --enable-shared
make
sudo make install
```
try this first, then post back problems. Also, you might need to recompile ffmpeg to link against this as well. The repo ffmpeg might not support this codec. Actually, it probably doesn't.

Also, maybe look at a program like mencoder instead of ffmpeg. I use ffmpeg, but I built mine from source, and it's a fairly lengthy process.

---

### Post by knattlhuber on 2009-02-14
Here's the output:

```
Input #0, asf, from '~/Desktop/movie.wmv':
  Duration: 01:36:07.1, start: 5.000000, bitrate: 2089 kb/s
    Stream #0.0: Video: wmv3, yuv420p, 640x480 [PAR 0:1 DAR 0:1], 1879 kb/s, 29.97 tb(r)
    Stream #0.1: Audio: 0x0162, 48000 Hz, stereo, 181 kb/s
Output #0, avi, to '~/Desktop/movie.avi':
    Stream #0.0: Video: libxvid (hq), yuv420p, 704x384 [PAR 32:33 DAR 16:9], q=3-5, 1500 kb/s, 29.97 tb(c)
    Stream #0.1: Audio: libmp3lame, 48000 Hz, stereo, 128 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
Unsupported codec (id=0) for input stream #0.1

```

---

### Post by benerivo on 2009-02-14
I would say the problem is that the audio from the wmv file is unsupported. The fact that this file won't even play with audio suggets that this is the case, rather than it being a problem with lame encoding. How have you tried to play it back?

---

### Post by knattlhuber on 2009-02-14
> **djbushido said:**
> Also, did you compile libmp3lame yourself?
I assume you used the repos

Thanks for your suggestions. You assumed correctly, it's from the repos.

I'm just very surprised as this is the first time that this happened in two years of playing all kinds of video under Linux..

So this may not work because the ffmpeg version in the repos is stripped of the mp3 support compared to the version available on Sourceforge?

---

### Post by knattlhuber on 2009-02-14
> **benerivo said:**
> How have you tried to play it back?

I tried VLC, Movie Player, MPlayer and xine.

VLC says:
```
 main decoder error: no suitable decoder module for fourcc `wmap'.
VLC probably does not support this sound or video format.

```

---

### Post by andrew.46 on 2009-02-14
Hi knattlhuber,

I think you have the cart in front of the horse here:

> 
```

[COLOR="Red"]**Input**[/COLOR] #0, asf, from '~/Desktop/movie.wmv':
Duration: 01:36:07.1, start: 5.000000, bitrate: 2089 kb/s
Stream #0.0: Video: wmv3, yuv420p, 640x480 [PAR 0:1 DAR 0:1], 1879 kb/s, 29.97 tb(r)
**[COLOR="Red"]Stream #0.1: Audio: 0x0162[/COLOR]**, 48000 Hz, stereo, 181 kb/s
[...]
Unsupported codec (id=0) for **[COLOR="Red"]input stream #0.1[/COLOR]**

```

FFmpeg is complaining about the *input* stream: 0x0162 not the output stream. I believe this is Windows Media Audio DMO (0x0162) and I am not so sure that even the newest FFmpeg supports this. But I am prepared to be proven wrong :-).
Andrew

---

### Post by mc4man on 2009-02-14
This (the input audio file
> Stream #0.1: Audio: 0x0162, 48000 Hz, stereo, 181 kb/s

is a wma2 or 3 audio file
I don't have any so I don't know if current ffmpeg supports it.
I'd think mplayer/mencoder with w32codecs would, (unfortunately w64codecs are slightly better than worthless

not 100% sure on the audio, for instance here's a hd wmv

> Playing test.wmv.
ASF file format detected.
[asfheader] Video stream found, -vid 2
[asfheader] Audio stream found, -aid 1
VIDEO:  [WMV3]  1280x720  24bpp  1000.000 fps    0.0 kbps ( 0.0 kbyte/s)
Clip info:
 name: Saints Row 2
==========================================================================
Opening video decoder: [dmo] DMO video codecs
DMO dll supports VO Optimizations 0 1
DMO dll might use previous sample when requested
Decoder supports the following formats: YV12 YUY2 UYVY YVYU RGB8 RGB555 RGB565 RGB24 RGB32 
Decoder is capable of YUV output (flags 0x1b)
VDec: vo config request - 1280 x 720 (preferred colorspace: Packed YUY2)
VDec: using Planar YV12 as output csp (no 0)
Movie-Aspect is undefined - no prescaling applied.
VO: [xv] 1280x720 => 1280x720 Planar YV12 
Selected video codec: [wmv9dmo] vfm: dmo (Windows Media Video 9 DMO)
==========================================================================
==========================================================================
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 48000 Hz, 2 ch, s16le, 192.0 kbit/12.50% (ratio: 24000->192000)
Selected audio codec: [ffwmav2] afm: ffmpeg (DivX audio v2 (FFmpeg))


If you were to search out 0x0162 you'll find conflicting descriptions

---

### Post by knattlhuber on 2009-02-14
> **andrew.46 said:**
> Hi knattlhuber,

I think you have the cart in front of the horse here

FFmpeg is complaining about the *input* stream: 0x0162 not the output stream. I believe this is Windows Media Audio DMO (0x0162) and I am not so sure that even the newest FFmpeg supports this. But I am prepared to be proven wrong :-).
Andrew

](*,)

Thanks Andrew. I just checked out the ffmpeg website. DMO/WMAP is not supported (yet). I'll try to find a Windows or Mac box to convert it.

Thanks to everybody for their input!

---

### Post by andrew.46 on 2009-02-15
Hi again,

Found the details:

[http://wiki.multimedia.cx/index.php?title=Windows_Media_Audio_Pro](http://wiki.multimedia.cx/index.php?title=Windows_Media_Audio_Pro)

and just to prove that I cannot leave such issues alone I have downloaded a sample file from [the MPlayer samples site]("http://samples.mplayerhq.hu/A-codecs/WMA9/wmapro/") which FFmpeg identifies correctly:

```

Input #0, asf, from 'Beethovens nionde symfoni (Scherzo)-1.wma':
Duration: 00:01:14.34, start: 1.451000, bitrate: 293 kb/s
**[COLOR="Red"]Stream #0.0: Audio: 0x0162, 48000 Hz, stereo, s16, 287 kb/s[/COLOR]**

```

But FFplay barfs on. But good news is that MPlayer plays it with no problems:

```

andrew@skamandros~/Desktop$ mplayer Beethovens\ nionde\ symfoni\ \(Scherzo\)-1.wma 
MPlayer SVN-r28553-4.2.4 (C) 2000-2009 MPlayer Team

Playing Beethovens nionde symfoni (Scherzo)-1.wma.
ASF file format detected.
[asfheader] Audio stream found, -aid 1
Clip info:
 name: 
 author: 
 copyright: 
 comments: 
==========================================================================
Opening audio decoder: [dmo] Win32/DMO decoders
AUDIO: 48000 Hz, 2 ch, s16le, 287.5 kbit/18.71% (ratio: 35932->192000)
Selected audio codec: [wma9dmo] afm: dmo (Windows Media Audio 9 DMO)
==========================================================================
AO: [oss] 48000Hz 2ch s16le (2 bytes per sample)
Video: no video
A:  12.6 (12.6) of 77.0 (01:17.0)  1.3% 

```

So this would mean that you could use MPlayer to output as pcm and then encode as you wish with these files that have audio only. MEncoder should be able to handle video + audio files as mc4man has suggested.

**Edit:** BTW mc4man Transcode 1.1.0 has some neat tricks for this one:

```

$ transcode -H 0 -x null,mplayer -i Beethovens\ nionde\ symfoni\ \(Scherzo\)-1.wma \
-y null,tcaud --lame_preset insane -E 44100,16,2 -m $HOME/Desktop/test.mp3

```

That is beyond cool!!


Andrew

---

### Post by knattlhuber on 2009-02-15
Thanks again, Andrew.
Unfortunately, my MPlayer doesn't play the Beethoven sample file (let alone the other .wmv file's audio)...

```
knattlhuber@intrepid:~$ mplayer '~/Desktop/Beethovens nionde symfoni (Scherzo)-1.wma' 
MPlayer 1.0rc2-4.3.2 (C) 2000-2007 MPlayer Team
CPU: Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz (Family: 6, Model: 15, Stepping: 11)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
...
Playing /home/stefankuhle/Desktop/Beethovens nionde symfoni (Scherzo)-1.wma.
ASF file format detected.
[asfheader] Audio stream found, -aid 1
...
Forced audio codec: mad
Requested audio codec family [wma9dmo] (afm=dmo) not available.
Enable it at compilation.
Requested audio codec family [wmadmo] (afm=dmo) not available.
Enable it at compilation.
Cannot find codec for audio format 0x162.
Read DOCS/HTML/en/codecs.html!
Audio: no sound

```

---

### Post by andrew.46 on 2009-02-15
Hi,

> **knattlhuber said:**
> Unfortunately, my MPlayer doesn't play the Beethoven sample file (let alone the other .wmv file's audio)...
```
knattlhuber@intrepid:~$ mplayer '~/Desktop/Beethovens nionde symfoni (Scherzo)-1.wma' 
**[COLOR="Red"]MPlayer 1.0rc2-4.3.2 (C) 2000-2007 MPlayer Team[/COLOR]**
CPU: Intel(R) Core(TM)2 Quad CPU    Q6600  @ 2.40GHz (Family: 6, Model: 15, Stepping: 11)
CPUflags:  MMX: 1 MMX2: 1 3DNow: 0 3DNow2: 0 SSE: 1 SSE2: 1
...

```

Unfortunately you have an older version that has a reduced codec pack. There is a guide for [the full MPlayer here]("http://ubuntuforums.org/showthread.php?t=1024592") that should help. This is the guide I use myself to install MPlayer.

Andrew

---

### Post by mc4man on 2009-02-15
> my MPlayer doesn't play ....
that's the downside of a 64 bit system, there's no codecs available for formats such as this.
For comparison the w64codec package (or mplayer codec pak.) is about 250Kb in size, the 32codec one is around 31Mb

I've seen posts about installing the 32bit mplayer in a 64 bit install, don't know how feasible/easy it is though

Edit : andrew - can the 64 bit mplayer play these if you compile?


what's sorta interesting about the wma3 is it can vary in br, sr. 'resolution' and channels (multichannel
These 2 are definitely playable 1 I made from cd, the other the sample from mplayer

> Audio

Format                           : WMA3

Format profile                   : M0

Codec ID                         : 162

Codec ID/Info                    : Windows Media Audio 3

Description of the codec         : Windows Media Audio 10 Professional - 192 kbps, 44 kHz, 2 channel 16 bit 1-pass CBR

Duration                         : 3mn 52s

Bit rate mode                    : Constant

Bit rate                         : 192 Kbps

Channel(s)                       : 2 channels

Sampling rate                    : 44.1 KHz

Resolution                       : 16 bits



Audio

Format                           : WMA3

Format profile                   : M1

Codec ID                         : 162

Codec ID/Info                    : Windows Media Audio 3

Description of the codec         : Windows Media Audio 9.1 Professional - 384 kbps, 48 kHz, 2 channel 24 bit 2-pass VBR

Duration                         : 1mn 15s

Bit rate mode                    : Variable

Bit rate                         : 287 Kbps

Channel(s)                       : 2 channels

Sampling rate                    : 48.0 KHz

Resolution                       : 24 bits

---

### Post by andrew.46 on 2009-02-15
Hi,

Can I demonstrate one method of transcoding one of these problem files? Unfortunately it demonstrates the need for:

[LIST=1]
[*]A very recent copy of Transcode
[*]The latest svn MPlayer
[*]The latest git x264
[*]The latest svn FFmpeg and a good read of the Fakeoutdoorsman's guide
[/LIST]

which is a fair investment of time, effort and learning. The file that I have looked at is here:

```

$ wget http://samples.mplayerhq.hu/A-codecs/WMA9/wmapro/WMVHDsplash.wmv

```

And FFmpeg shows it as:

```

Stream #0.0: **[COLOR="Red"]Audio: 0x0162[/COLOR]**, 48000 Hz, 5.1, s16, 384 kb/s
Stream #0.1: Video: wmv3, yuv420p, 1280x720, 6500 kb/s, 23.98 tb(r)

```

which is exactly the audio codec that has been giving all the trouble. Note that for some reason audio and video tracks are reversed. Now as I have mentioned the svn MPlayer can play this audio so it can be extracted as PCM as follows:

```

$ transcode -H 0 -i WMVHDsplash.wmv -x null,mplayer -y null,wav -m sound.wav

```

And then with a bit of tricky remapping by FFmpeg the original video and the extracted sound are both muxed into an mp4 container using h264 for the video and aac for the sound:

```
$ ffmpeg -i WMVHDsplash.wmv -i sound.wav -map 0.1 -map 1.0 \
         -vcodec libx264 -vpre hq -crf 22 -threads 0 \
         -acodec libfaac -ab 128k -ar 44100 -ac 2 \
          converted.mp4
```

This leaves the final file as:

```

Stream #0.0(und): Video: h264, yuv420p, 1280x720, 23.98 tb(r)
Stream #0.1(und): Audio: aac, 44100 Hz, stereo, s16

```

And playable by most modern media players. Note that the Video and Audio streams have been neatly remapped? The original file is 15 megs while the transcoded file is 5 megs and I challenge anybody to tell me it looks and sounds all *that* different. 

So I guess knattlhuber the answer is that it certainly *can* be done. I am usually accused of making things too complicated but this would be *my* way of doing it. Can anybody else suggest an 'easier' way of accomplishing this task, perhaps utilising this file from MPlayer just to make it interesting :-).

All the best,

Andrew

---

### Post by djbushido on 2009-02-15
You can also use pacpl to convert wma to mp3 or whatnot. I believe it's pacpl.sourceforge.net, but a google search for pacpl should yield what you need.

---

### Post by knattlhuber on 2009-02-15
I tried compiling MPlayer but still no luck. So it's the 64-bit I guess.

My next Ubuntu installation's gonna be 32-bit again, that's for sure. Too much trouble with Flash, Java, codecs, and non-mainstream apps that don't support 64-bit...

---

### Post by mc4man on 2009-02-15
> My next Ubuntu installation's gonna be 32-bit again
I'm planning my next box, I'll think I'll make it a dual boot 32 and 64.

I tried Andrews method and as usual worked beautifully, though you need a 32 bit mplayer/win32codecs to do.

If you happened to have access to a windows install then it's quite easy to run your video thru windows media encoder and choose any audio output but lossless.

That would convert the audio to wma2 which vlc (64 or 32 ) can play. (vlc can't play wmap or wmal

There are more extensive methods, (demux, convert to wma2 or ac3 5.1, remux), but the above is almost point and click.

---

### Post by knattlhuber on 2009-02-15
Incidentally, I just came across this one:
[http://abock.org/moonshine/]("http://abock.org/moonshine/")

"Windows Media playback through Moonlight and Firefox for Linux
[...] Moonshine is a browser plugin that proxies the Moonlight plugin, claiming support for Windows Media content. When Firefox comes across content advertised as Windows Media, it loads the Moonshine plugin which in turn loads Moonlight.
Moonshine then loads its media player application, written in Silverlight, into the proxied Moonlight plugin, which is able to play back the Windows Media content.
The desktop player is Firefox with the standard web chrome replaced with controls to drive the media experience.
[...] Windows Media support is included in Moonlight, and is provided directly by Microsoft as part of their commitment to Silverlight compatibility on all platforms. Moonshine simply leverages this support by loading a Silverlight media player application into the browser for Moonlight to run."

Comes in 32- and 64-bit.

---

