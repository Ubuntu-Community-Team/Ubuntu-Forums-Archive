---
title: "Stuttering Flash -- Local Flash Player?"
date: 2006-11-21
forum: Multimedia &amp; Video
---

### Post by secdroid on 2006-11-21
I'm using the beta Adobe Flash 9 plugin with Firefox 1.5 on Dapper X86.

There's a site with videos that I am interested in.  Sometimes I can play the vids, but sometimes I get stuttering and then play stops, while the content is still being downloaded.  Play never starts again.  (I think that there is net congestion, but I'm not sure.)

OK, I downloaded the .flv files from the site, thinking that I'd convert them to some other format and play them locally.  No go -- unsupported codec.  I think they must be Flash 8.

I know that there are Flash .flv file players for Windows, but I haven't found one for Linux.  I looked on Sourceforge and found two html/.js/.swf players for .flv (intended for web developers), but they exceed my ability and one appears to have compatibility issues.

Is there any way I can play or convert these Flash vids?

TIA, Puzzled_Player

---

### Post by Jason_25 on 2006-11-21
This is the ffmpeg command I use to convert youtube video into mpg.

```

ffmpeg -i 'Kiss - Tom Snyder 1.flv' -ac 2 -ar 44100 -ab 128 -b 3000  -s 320x240 test.mpg

```

---

### Post by secdroid on 2006-11-21
> This is the ffmpeg command I use
Here's what I get with ffmpeg
> [flv @ 0x82c8a80]Unsupported video codec (4)

The flv2avi.sh (uses mencoder from mplayer) and flvconvert.sh (uses ffmpeg) both fail with unsuported codec errors.

The transcode command fails with:
> [transcode] auto-probing source ess06.flv (failed)
[transcode] V: import format    | unknown  (V=(null)|A=(null))
[transcode] warning : no option -x found, option -i ignored, reading from "/dev/zero"
[transcode] V: import frame     | 720x576  1.25:1
[transcode] V: bits/pixel       | 0.174
[transcode] V: decoding fps,frc | 25.000,0
[transcode] V: Y'CbCr           | YV12/I420
[transcode] A: import format    | 0x2000  AC3          [48000,16,2]
[transcode] A: export           | disabled
[transcode] V: encoding fps,frc | 25.000,3
[transcode] A: bytes per frame  | 7680 (7680.000000)
[transcode] A: adjustment       | 0@1000
[transcode] V: IA32/AMD64 accel | 3dnowext (3dnowext 3dnow mmxext mmx asm C)

FWIW, all players can play the audio from this .flv, but all (vlc, mplayer, totem, real, etc.) fail with video.

I'm stumped.

---

### Post by pierric on 2006-12-15
Same issue here, I'm not sure there is a way to play a flash8/9 FLV file other than through the flash9 beta, and that means it can only be done with online files through the flash players.

If someone knows a way to play newer FLV files with mplayer... let me know!

Cheers.

---

### Post by shewbox on 2006-12-25
Wanted to say I am having the same problem.  Playing an .flv file in mplayer, vlc will play sound, but no video.  I tried to convert it to ogg theora, but get this error:

```
[flv @ 0xb7f98c30]Unsupported video codec (4)
[flv @ 0xb7f98c30]Could not find codec parameters (Video: 0x0004)
Input #0, flv, from 'video.flv':
  Duration: 00:01:29.6, bitrate: N/A
  Stream #0.0: Audio: mp3, 22050 Hz, stereo
  Stream #0.1: Video: 0x0004, 30.00 fps(r)
      0:01:29.62 audio: 43kbps video: 0kbps
```

And the resulting file is audio only.

---

### Post by digbysellers on 2007-12-26
> **pierric said:**
> Same issue here, I'm not sure there is a way to play a flash8/9 FLV file other than through the flash9 beta, and that means it can only be done with online files through the flash players.

If someone knows a way to play newer FLV files with mplayer... let me know!

Cheers.

After downloading the same file multiple times, assuming I had an incomplete file, I just booted into XP and my most recently downloaded .flv's played perfectly in flv player. 
No new media players, no new codecs needed. 
Won't even play in Ubuntu.
Only .flv's from a couple of years back play in 6.06 for me. 

So damned frustrating...
The sheer amount of time one must waste on these things. I hate computers.

---

