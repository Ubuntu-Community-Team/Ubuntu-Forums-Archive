---
title: "Can't play this mp4 video, tried on several ubuntu systems (works on windows)"
date: 2013-12-23
forum: Multimedia Software
---

### Post by byenary on 2013-12-23
Hi,

Media info in vlc:

I'm unable to play mp4s from my sony HD camera, the quality is high 
Codec:H264-MPEG-4 AVC (part10° (avc1)
Resolution: 1920x1080
Frame rate : 59.940060
Decoded format:Planar 4:2:0 YUV full scale

Totem plays in slomotion
SMplayer shows only first frame, sound continues
vlcplayer shows a couple frames, sound continues

I have an example available here; [https://dl.dropboxusercontent.com/u/24523058/IMGA0530.MP4](https://dl.dropboxusercontent.com/u/24523058/IMGA0530.MP4)

I'm trying at the moment on rather modern machine, no fancy graphic card but 8 Gb RAM and I5, no problems playing those videos on the same machine when booting into W7

---

### Post by ajgreeny on 2013-12-23
I believe Sony uses a proprietary format for its videocams and HD camera videos.  See what the command line mediainfo says with ```
mediainfo -l /path/to/video.mp4
``` Mediainfo is in the repos.

Your sample plays fine here (a smiling baby with a green sleeved arm) but there is no sound; mediainfo does not find any audio either.
Your resolution is also much lower than you say in your original post, being reported by mediainfo as ```
Width                                    : 640 pixels
Height                                   : 360 pixels
Display aspect ratio                     : 16:9
Frame rate mode                          : Constant
Frame rate                               : 59.940 fps
Color space                              : YUV
```

---

### Post by sammiev on 2013-12-23
Sample plays fine here but no sound with VLC.

---

### Post by byenary on 2013-12-24
I used a bad example this one should be better high res : playing in totem no sound, playing in vlc, one frame but sound... no player playing as it should..
[https://dl.dropboxusercontent.com/u/24523058/IMGA0616.MP4](https://dl.dropboxusercontent.com/u/24523058/IMGA0616.MP4)
mediainfo :
elias@elias-Latitude-E6520:~$ mediainfo -l /home/elias/Dropbox/Public/IMGA0616.MP4 
General
Complete name                            : /home/elias/Dropbox/Public/IMGA0616.MP4
Format                                   : MPEG-4
Format profile                           : Base Media / Version 2
Codec ID                                 : mp42
File size                                : 26.9 MiB
Duration                                 : 12s 12ms
Overall bit rate mode                    : Variable
Overall bit rate                         : 18.8 Mbps
Encoded date                             : UTC 2013-04-04 10:37:27
Tagged date                              : UTC 2013-04-04 10:37:27
PANA                                     : HX-WA20

Video
ID                                       : 1
Format                                   : AVC
Format/Info                              : Advanced Video Codec
Format profile                           : Main@L4.1
Format settings, CABAC                   : No
Format settings, ReFrames                : 2 frames
Format settings, GOP                     : M=1, N=30
Codec ID                                 : avc1
Codec ID/Info                            : Advanced Video Coding
Duration                                 : 12s 12ms
Bit rate                                 : 18.3 Mbps
Width                                    : 1 920 pixels
Height                                   : 1 080 pixels
Display aspect ratio                     : 16:9
Frame rate mode                          : Constant
Frame rate                               : 59.940 fps
Original frame rate                      : 29.970 fps
Color space                              : YUV
Chroma subsampling                       : 4:2:0
Bit depth                                : 8 bits
Scan type                                : Interlaced
Scan order                               : Top Field First
Bits/(Pixel*Frame)                       : 0.147
Stream size                              : 26.1 MiB (97%)
Language                                 : English
Encoded date                             : UTC 2013-04-04 10:37:27
Tagged date                              : UTC 2013-04-04 10:37:27
Color primaries                          : BT.709
Transfer characteristics                 : BT.709
Matrix coefficients                      : BT.709

Audio
ID                                       : 2
Format                                   : AAC
Format/Info                              : Advanced Audio Codec
Format profile                           : LC
Codec ID                                 : 40
Duration                                 : 12s 12ms
Source duration                          : 12s 11ms
Bit rate mode                            : Variable
Bit rate                                 : 256 Kbps
Maximum bit rate                         : 384 Kbps
Channel count                            : 2 channels
Channel positions                        : Front: L R
Sampling rate                            : 48.0 KHz
Compression mode                         : Lossy
Stream size                              : 374 KiB (1%)
Source stream size                       : 374 KiB (1%)
Language                                 : English
Encoded date                             : UTC 2013-04-04 10:37:27
Tagged date                              : UTC 2013-04-04 10:37:27

---

### Post by monkeybrain20122 on 2013-12-24
Plays perfectly in vlc and Smplayer (with stock mplayer2 backend). Totem messes it up, no sound after the first few frames but video plays fine. Ubuntu 13.04, 32 bits. smplayer and mplayer2 both straight from repo, vlc 2.2 from daily build ppa.

On Ubuntu 13.10 64 bits plays perfectly on all players, including Totem. But on this install mplayer, mplayer2 and vlc (2.1.2) are all compiled from source against ffmpeg 2.1 (as oppose to avconv that Debian/Ubuntu offers, which seems to have problems with certain codecs and formats that real ffmpeg handles with no problem, but this shouldn't be a factor as the video plays in stock players in 13.04) Totem is from the repo.

Edited: Even bino works, it is a 3d video player but plays your video perfectly in 2d mode. So all players work basically(except for Totem in 32 bit raring which has no sound) Did you install Ubuntu-restricted-extras?

---

### Post by ajgreeny on 2013-12-24
Plays very well in its new form in all my players;  VLC, parole and gnome-mplayer, as well as mplayer in terminal, so I am uncertain why it doesn't on your machine.

---

