---
title: "Convert AVCHD to mpg"
date: 2012-03-25
forum: Multimedia Software
---

### Post by Kaizoku001 on 2012-03-25
Hi there. I did a little search, but didn't understand much of what was said. 

Could somebody pleas help and explain how to convert AVCHD (mts) video files to mp4, or even avi.
These are videos of my kids so I would like to keep quality, while reducing space.
Thanks in advance

---

### Post by shantiq on 2012-03-25
hi kaizoku    typically m2ts   has very hi specs  Blu ray

so to reduce size of file maybe we can make the frame size a bit smaller [720p] and keep audio the same so as as to keep high quality   see the sample i used below and the reductions   [all in red]

reduce video bit rate from 16000k to 5000k which is still very good quality
and reduces the file size by two thirds  but you can change that to 8000k or whatever you want it to be

i chose mkv as extension but you can pick avi or mp4 or mpg if you wish.   I have reduced the 1080p to 720p.  If you want to retain 1080  simply replace  -s hd720 with -s hd1080  [of course this will increase size of file]
[CENTER][B]
=========
[/B][/CENTER]



**SO**   simply put your file(s) on desktop in a folder called conversion

open terminal   

enter   ```
cd Desktop/conversion
```

then   >  for f in *.m2ts ; do ffmpeg -i "$f"  -b 5000k  -s hd720 -ab 256k "${f%.m2ts}.mkv"; done


**and that is it**


check properties of new file as opposed to earlier    should be about a third in size but still really good def



Hope this is good for you [img]http://img96.imageshack.us/img96/2284/smilieubu921.png[/img] 




[CENTER][B]
=========
[/B][/CENTER]






> mediainfo sample_1.m2ts     



Video
ID                                       : 4113 (0x1011)
Menu ID                                  : 1 (0x1)
Format                                   : AVC
Format/Info                              : Advanced Video Codec
Format profile                           : Main@L4.0
Format settings, CABAC                   : Yes
Format settings, ReFrames                : 2 frames
Format settings, GOP                     : M=2, N=15
Codec ID                                 : 27
Duration                                 : 17s 951ms
Bit rate mode                            : Variable
[COLOR="DarkRed"]Bit rate                                 : 11.2 Mbps
Maximum bit rate                         : 16.0 Mbps[/COLOR]
[COLOR="DarkRed"]Width                                    : 1 440 pixels
Height                                   : 1 080 pixels[/COLOR]
Display aspect ratio                     : 16:9
Frame rate                               : 29.970 fps
Color space                              : YUV
Chroma subsampling                       : 4:2:0
Bit depth                                : 8 bits
Scan type                                : Interlaced
Scan order                               : Top Field First
Bits/(Pixel*Frame)                       : 0.240
Stream size                              : 24.0 MiB (92%)





> mediainfo sample_1.mkv

Video
ID                                       : 1
Format                                   : MPEG-4 Visual
Format profile                           : Simple@L1
Format settings, BVOP                    : No
Format settings, QPel                    : No
Format settings, GMC                     : No warppoints
Format settings, Matrix                  : Default (H.263)
Codec ID                                 : V_MPEG4/ISO/ASP
Codec ID/Info                            : Advanced Simple Profile
Duration                                 : 18s 35ms
[COLOR="DarkRed"]Bit rate                                 : 3 782 Kbps
Width                                    : 1 280 pixels
Height                                   : 720 pixels[/COLOR]
Display aspect ratio                     : 2.35:1
Original display aspect ratio            : 2.35:1
Frame rate                               : 59.940 fps
Color space                              : YUV
Chroma subsampling                       : 4:2:0
Bit depth                                : 8 bits
Scan type                                : Progressive
Compression mode                         : Lossy
Bits/(Pixel*Frame)                       : 0.068
Stream size                              : 8.13 MiB (95%)
Writing library                          : Lavc53.6.0
Language                                 : English
Default                                  : Yes
Forced                                   : No


---

### Post by pixiq on 2012-03-25
I do it according to the following link with ffmpeg, where the x264 codec compresses the file size. I'm running these commands in Ubuntu Studio 11.04. I know that there are differences between the versions, but at least if you have some flavour of 11.04, the standard version of ffmpeg does the job. You install it with the command
```
sudo apt-get install ffmpeg
```

See the following link
[[COLOR="SeaGreen"]_http://ubuntuforums.org/showthread.php?t=1920371_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1920371")

I intend to wait until 12.04 is out to upgrade to that version, and then modify my scripts to work in the new environment.

---

### Post by cotcot on 2012-03-25
I do not know in how far your are familiar with command line and ffmpeg instructions.
With ffmpeg command line you might need to tune the options depending on the specs of the input video (aspect ratio, 25 p or 50 i, ...)
Alternatives are GUI converters like Winff or Handbrake.
You could also use a video editor that can open .mts and render it to whatever format you want. Kdenlive, Openshot and Blender VSE can open and render or edit AVCHD. 
I do not recommend to edit directly with the .mts. I render them first with xvid to .avi and do the editing with the .avi files.

---

