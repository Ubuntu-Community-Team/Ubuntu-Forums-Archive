---
title: "VLC not always working, but Totem does"
date: 2013-09-15
forum: Multimedia Software
---

### Post by George_Ronald_Mayfield on 2013-09-15
New computer from System 76
Installed VLC
Installed restricted extras

I've got a folder of shows. I watched several .avi files using VLC just fine, then I got a bunch that won't play.
Then, I tried watching in the default video program from Totem (It's just called "Videos"?), and they will play fine.

It seems there's no difference in codecs. They're all .avi containers with MPEG video and MP3 audio.

I assume something's wrong with VLC, so I uninstalled it and completely removed it, then re-installed it. Still not working for those videos.

---

### Post by Yellow Pasque on 2013-09-15
Run mediainfo on one that won't play and post output:
```
sudo apt-get install mediainfo
mediainfo <file>
```

---

### Post by George_Ronald_Mayfield on 2013-09-15
> **Temüjin said:**
> Run mediainfo on one that won't play and post output:
```
sudo apt-get install mediainfo
mediainfo <file>
```
General
Complete name                            : /home/wilddog/Desktop/ATHF.avi
Format                                   : AVI
Format/Info                              : Audio Video Interleave
File size                                : 87.5 MiB
Duration                                 : 11mn 47s
Overall bit rate mode                    : Variable
Overall bit rate                         : 1 037 Kbps
                                        : 


Video
ID                                       : 0
Format                                   : MPEG-4 Visual
Format profile                           : Advanced Simple@L5
Format settings, BVOP                    : 2
Format settings, QPel                    : No
Format settings, GMC                     : No warppoints
Format settings, Matrix                  : Default (H.263)
Muxing mode                              : Packed bitstream
Codec ID                                 : XVID
Codec ID/Hint                            : XviD
Duration                                 : 11mn 47s
Bit rate                                 : 894 Kbps
Width                                    : 512 pixels
Height                                   : 384 pixels
Display aspect ratio                     : 4:3
Frame rate                               : 23.976 fps
Color space                              : YUV
Chroma subsampling                       : 4:2:0
Bit depth                                : 8 bits
Scan type                                : Progressive
Compression mode                         : Lossy
Bits/(Pixel*Frame)                       : 0.190
Stream size                              : 75.4 MiB (86%)
Writing library                          : XviD 1.2.1 (UTC 2008-12-04)


Audio
ID                                       : 1
Format                                   : MPEG Audio
Format version                           : Version 1
Format profile                           : Layer 3
Mode                                     : Joint stereo
Mode extension                           : MS Stereo
Codec ID                                 : 55
Codec ID/Hint                            : MP3
Duration                                 : 11mn 47s
Bit rate mode                            : Variable
Bit rate                                 : 128 Kbps
Channel(s)                               : 2 channels
Sampling rate                            : 48.0 KHz
Compression mode                         : Lossy
Stream size                              : 11.0 MiB (13%)
Alignment                                : Aligned on interleaves
Interleave, duration                     : 24 ms (0.58 video frame)
Interleave, preload duration             : 141 ms
Writing library                          : LAME3.90.
Encoding settings                        : -m j -V 4 -q 2 -lowpass 17.6 --abr 128

---

### Post by George_Ronald_Mayfield on 2013-09-15
I guess I should expand on "won't play".
I click on the file, and default program is VLC, so VLC opens. The only thing VLC displays is the filename in the playlist as normal, and a black screen with the VLC logo on the player screen. It should play automatically, but if I click play, the filename in the playlist blinks. Nothing else happens.
If I throw another playable video under that one on the playlist, it skips over the bad video and starts playing the good one. 
I do not get an error in any case.

---

### Post by Yellow Pasque on 2013-09-15
```
Codec ID : XVID
```

Hmm, is libavcodec-extra-53 installed?

---

### Post by George_Ronald_Mayfield on 2013-09-15
> libavcodec-extra-53 is already the newest version.
 
I made sure, and it was

---

