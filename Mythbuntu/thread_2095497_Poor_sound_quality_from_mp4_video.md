---
title: "Poor sound quality from mp4 video"
date: 2012-12-17
forum: Mythbuntu
---

### Post by NautiusMaximus on 2012-12-17
I'm trying to play a video via the videos feature of the MythTV front end. (It's [this one]("http://www.decayfilm.com/"), if you're interested).

The playback, in particular the sound, is very jittery and makes the film unwatchable. This seems to be specific to the MythTV front end video player: if I watch it in VLC media player on the same machine, it's fine.

According to the properties of the video file, the video codec is H.264 / AVC, with a frame rate of 24 fps and a bitrate of 12860 kbps. The audio codec is MPEG-4 AAC with a sample rate of 48000 Hz and a bitrate of 157 kbps.

I've checked the mythfrontend.log file, and it reports numerous "prebuffering pauses". 

Any idea what the problem is? Can this be fixed by tweaking some settings or using ffmpeg to recode the file (preferably without losing quality)? Or am I just going to have to watch the movie in VLC media player?

Many thanks
NM

---

### Post by NautiusMaximus on 2012-12-17
Sorry, just realised I forgot to mention which software versions I'm using.

Mythbuntu 10.04, pretty much "out of the box" with nothing fancy done to it after installation. MythTV version 0.23.1.

---

### Post by nickrout on 2012-12-17
There are any number of video files to download from that site - which one did you get? (Looks interesting but the good quality files are a big download - is it a good movie?)

---

### Post by andrew.46 on 2012-12-17
Can't really help with Mythtv but thanks for the heads-up with the free film, I am downloading the 1080 HQ version via torrent :)

---

### Post by NautiusMaximus on 2012-12-17
> **nickrout said:**
> There are any number of video files to download from that site - which one did you get? (Looks interesting but the good quality files are a big download - is it a good movie?)

Ah yes, sorry, should have specified. It was the 1080p version from the "recommended downloads".

Don't know whether it's a good movie yet: haven't watched it, pending resolving this issue.

---

### Post by fdrake on 2012-12-17
can't help either but whatching the trailer I had this urge to ask myself: why scientists at Cern should have guns???

---

### Post by andrew.46 on 2013-01-02
> **fdrake said:**
> can't help either but whatching the trailer I had this urge to ask myself: why scientists at Cern should have guns???

Having watched the movie I can tell you that there was actually only *one* gun and it was originally owned by a security guard before the zombies.... well you can guess the rest :)

@NautiusMaximus: It is a very high quality movie:

```

andrew@skamandros~/downloads/Decay_2012_1080p_HQ$ mediainfo Decay_2012_1080p_HQ.mp4 
General
Complete name                            : Decay_2012_1080p_HQ.mp4
Format                                   : MPEG-4
Format profile                           : Base Media / Version 2
Codec ID                                 : mp42
File size                                : 18.4 GiB
Duration                                 : 1h 16mn
Overall bit rate mode                    : Variable
Overall bit rate                         : 34.6 Mbps
Encoded date                             : UTC 2012-12-08 07:44:59
Tagged date                              : UTC 2012-12-08 08:38:56
©TIM                                     : 00:00:00:00
©TSC                                     : 24000
©TSZ                                     : 1001

Video
ID                                       : 1
Format                                   : AVC
Format/Info                              : Advanced Video Codec
**[COLOR="Red"]Format profile                           : Main@L5.1[/COLOR]**
Format settings, CABAC                   : Yes
Format settings, ReFrames                : 3 frames
Format settings, GOP                     : M=4, N=33
Codec ID                                 : avc1
Codec ID/Info                            : Advanced Video Coding
Duration                                 : 1h 16mn
**[COLOR="Red"]Bit rate                                 : 34.4 Mbps[/COLOR]**
Width                                    : 1 920 pixels
Height                                   : 960 pixels
Display aspect ratio                     : 2.000
Frame rate mode                          : Constant
Frame rate                               : 23.976 fps
Standard                                 : NTSC
Color space                              : YUV
Chroma subsampling                       : 4:2:0
Bit depth                                : 8 bits
Scan type                                : Progressive
Bits/(Pixel*Frame)                       : 0.778
Stream size                              : 18.3 GiB (99%)
Language                                 : English
Encoded date                             : UTC 2012-12-08 07:44:59
Tagged date                              : UTC 2012-12-08 07:44:59

Audio
ID                                       : 2
Format                                   : AAC
Format/Info                              : Advanced Audio Codec
Format profile                           : LC
Codec ID                                 : 40
Duration                                 : 1h 16mn
Source duration                          : 1h 16mn
Bit rate mode                            : Variable
Bit rate                                 : 157 Kbps
Maximum bit rate                         : 264 Kbps
Channel(s)                               : 2 channels
Channel positions                        : Front: L R
Sampling rate                            : 48.0 KHz
Compression mode                         : Lossy
Stream size                              : 85.7 MiB (0%)
Source stream size                       : 85.7 MiB (0%)
Language                                 : English
Encoded date                             : UTC 2012-12-08 07:44:59
Tagged date                              : UTC 2012-12-08 07:44:59

```

That's mbps no kbps, so you would need some serious hardware +/- video acceleration...

---

### Post by nickrout on 2013-01-02
Max for bluray iirc is 45Mbps so not too bad. 5.1 level encoding is a more likely problem.

---

### Post by andrew.46 on 2013-01-02
> **nickrout said:**
> Max for bluray iirc is 45Mbps so not too bad. 5.1 level encoding is a more likely problem.

I did not know that, mind you my knowledge of how MythTV runs is pretty close to zero :). My television will not play h264 + aac in mp4 so I routinely convert to mpeg4 video mp3 sound in avi and this might perhaps help the OP:

```

ffmpeg -y -i "Decay_2012_1080p_HQ.mp4" -threads auto \
-c:v mpeg4 -q:v 5 -vtag XVID -f avi -mbd rd -flags +mv4+aic -trellis 2 -cmp 2 -subcmp 2 -g 300 \
-c:a libmp3lame -ac 2 -q:a 3 -ar 44100 \
"Decay_2012_1080p_HQ.avi"

```

and with this the file size drops from 19gig to 1.6gig, quality is fine on tv... But perhaps a reencode with x264 might be a better option?

---

### Post by nickrout on 2013-01-02
> **andrew.46 said:**
> I did not know that, mind you my knowledge of how MythTV runs is pretty close to zero :). My television will not play h264 + aac in mp4 so I routinely convert to mpeg4 video mp3 sound in avi and this might perhaps help the OP:

```

ffmpeg -y -i "Decay_2012_1080p_HQ.mp4" -threads auto \
-c:v mpeg4 -q:v 5 -vtag XVID -f avi -mbd rd -flags +mv4+aic -trellis 2 -cmp 2 -subcmp 2 -g 300 \
-c:a libmp3lame -ac 2 -q:a 3 -ar 44100 \
"Decay_2012_1080p_HQ.avi"

```

and with this the file size drops from 19gig to 1.6gig, quality is fine on tv... But perhaps a reencode with x264 might be a better option?yuk, why wreck a perfectly good hi def file like that? Especially when it is available in lower quality anyway.



We weren't talking about what codecs your TV supports, but what mythfrontend supports.

---

### Post by andrew.46 on 2013-01-03
> **nickrout said:**
> We weren't talking about what codecs your TV supports, but what mythfrontend supports.

Indeed, my apologies for rambling away from the original topic...

---

