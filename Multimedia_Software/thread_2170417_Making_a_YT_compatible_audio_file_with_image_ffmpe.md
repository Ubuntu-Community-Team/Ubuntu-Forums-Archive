---
title: "Making a YT compatible audio file with image ffmpeg"
date: 2013-08-26
forum: Multimedia Software
---

### Post by shantiq on 2013-08-26
**if you do not want **to plough through entire thread the answer [**thanx **to FakeOutdoorman and Temüjin] is as follows

 > time ffmpeg -y -loop 1 -r 2 -i IMAGE.png -i SOUNDFILE.mp3 -c:a libfdk_aac -b:a 192k -c:v libx264 -g 7 -crf 0 -vf scale=-1:720 -preset veryfast -shortest VIDEO.mkv




Where you have installed ffmpeg [this way]("https://trac.ffmpeg.org/wiki/UbuntuCompilationGuide") and input image and sound can be any format


the original post

&#9660;
&#9660;
&#9660;

   



ok so i have tried this 

>  ffmpeg -i file.mp3  -i file.png -s hd720 -c:a copy file.mkv


with first a 24/96 flac and a png and YT rejected it then tried 16/48 flac and it also rejected it
then went 320k mp3 and png and still rejected

youtube says not an accepted video format


these are the files in question

> GeneralComplete name                            : Kingston.mp3
Format                                   : MPEG Audio
File size                                : 42.5 MiB
Duration                                 : 18mn 34s
Overall bit rate mode                    : Constant
Overall bit rate                         : 320 Kbps
Writing library                          : Lavf54.63.104
COMMENTS                                 : Processed by SoX


Audio
Format                                   : MPEG Audio
Format version                           : Version 1
Format profile                           : Layer 3
Mode                                     : Joint stereo
Mode extension                           : MS Stereo
Duration                                 : 18mn 35s
Bit rate mode                            : Constant
Bit rate                                 : 320 Kbps
Channel(s)                               : 2 channels
Sampling rate                            : 44.1 KHz
Compression mode                         : Lossy
Stream size                              : 42.5 MiB (100%)



mkv +++>


General
Unique ID                                : 219810790257369297053670777926744307634 (0xA55E04AFAD27D2A93786F398D71877B2)
Complete name                            : Kingston.mkv
Format                                   : Matroska
Format version                           : Version 2
File size                                : 42.9 MiB
Duration                                 : 18mn 34s
Overall bit rate                         : 322 Kbps
Writing application                      : Lavf54.63.104
Writing library                          : Lavf54.63.104
COMMENTS                                 : Processed by SoX


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
Duration                                 : 18mn 34s
Width                                    : 1 280 pixels
Height                                   : 720 pixels
Display aspect ratio                     : 1.201
Frame rate mode                          : Constant
Frame rate                               : 25.000 fps
Color space                              : YUV
Chroma subsampling                       : 4:2:0
Bit depth                                : 8 bits
Scan type                                : Progressive
Compression mode                         : Lossy
Writing library                          : Lavc54.92.100
Default                                  : Yes
Forced                                   : No


Audio
ID                                       : 2
Format                                   : MPEG Audio
Format version                           : Version 1
Format profile                           : Layer 3
Mode                                     : Joint stereo
Mode extension                           : MS Stereo
Codec ID                                 : A_MPEG/L3
Codec ID/Hint                            : MP3
Duration                                 : 18mn 34s
Bit rate mode                            : Constant
Bit rate                                 : 320 Kbps
Channel(s)                               : 2 channels
Sampling rate                            : 44.1 KHz
Compression mode                         : Lossy
Stream size                              : 42.5 MiB (99%)
Default                                  : Yes
Forced                                   : No





Also tried on 2 different accounts
What can the problem be here ?
Any of you learned chaps  see a possible reason?

---

### Post by Yellow Pasque on 2013-08-26
Looks like Matroska/.mkv is not supported: [https://support.google.com/youtube/troubleshooter/2888402?hl=en](https://support.google.com/youtube/troubleshooter/2888402?hl=en)

---

### Post by shantiq on 2013-08-26
[SIZE=2]well [/SIZE]Temüjin[COLOR=#000000][SIZE=2]  i have seen this too  and i must say i have uploaded countless mkv files[/SIZE]

avin read that i had also tried MOV and avi    and no good either   ;    i think it is the resulting file with

the [/COLOR]> [COLOR=#000000]*ffmpeg -i file.mp3 -i file.png -s hd720 -c:a copy file.mkv*[/COLOR][COLOR=#000000]   which is the problem


it does it quickly like 2 minutes [quick encode why i would favour it over kdenlive which takes 1.5 hour]on an 18 mn sound file    so it seems YT does not like that file       but it plays fine in vlc mplayer etc...


i wonder if there is something to add to the code line to make it YT-happy



If you do not want to read the entire thread the answer is   {thanx to FakeOutdoorman}


[/COLOR]> time ffmpeg -y -loop 1 -r 2 -i amarilla.png -i bulgaria.mp3 -c:a libfdk_aac -b:a 192k -c:v libx264 -g 7 -crf 0 -s hd720 -preset veryfast -shortest output24.mkv


[COLOR=#000000]

of course size is your choice   i picked hd720   also hd1080 available or any size of your choice   say  780x480 etc

[/COLOR]

---

### Post by Yellow Pasque on 2013-08-26
Some ideas - 
Have you done this?: [https://support.google.com/youtube/answer/71673?hl=en&ref_topic=2888648](https://support.google.com/youtube/answer/71673?hl=en&ref_topic=2888648)
Perhaps you should just let youtube mux the video by uploading the photo and creating a slideshow, then adding audio track.

---

### Post by shantiq on 2013-08-26
great tip [COLOR=#000000]Temüjin[/COLOR] but not what i need

this works for images but does not let you bring in your own audio     you have to use their audio it seems

---

### Post by FakeOutdoorsman on 2013-08-26
> **shantiq said:**
> Any of you learned chaps  see a possible reason?

The Youtube seems to accept just about anything I feed it theses days, and I can not duplicate your issue. Please include the complete console output for one of your commands that is failing in YouTube.

---

### Post by Yellow Pasque on 2013-08-26
I tried to duplicate your command with a .png and a 320k mp3. My ffmpeg (I'm on Debian sid) used h264 by default. I'm not sure if that means anything, though..

---

### Post by shantiq on 2013-08-27
ok FakeO and [COLOR=#000000][COLOR=#000000]Temüjin   let us test it again from scratch


i take a png

[/COLOR][/COLOR]> GeneralComplete name                            : amarilla.png
Format                                   : PNG
Format/Info                              : Portable Network Graphic
File size                                : 8.37 MiB


Image
Format                                   : PNG
Format/Info                              : Portable Network Graphic
Width                                    : 2 816 pixels
Height                                   : 2 244 pixels
Bit depth                                : 24 bits
Compression mode                         : Lossless
Stream size                              : 8.37 MiB (100%)


[COLOR=#000000][COLOR=#000000]


and an mp3


[/COLOR][/COLOR]> GeneralComplete name                            : bulgaria.mp3
Format                                   : MPEG Audio
File size                                : 11.0 MiB
Duration                                 : 4mn 48s
Overall bit rate mode                    : Constant
Overall bit rate                         : 320 Kbps
Writing library                          : LAME 64bits version 3.99.5 ([http://lame.sf.net](http://lame.sf.net))
Comment                                  : Processed by SoX


Audio
Format                                   : MPEG Audio
Format version                           : Version 1
Format profile                           : Layer 3
Mode                                     : Joint stereo
Duration                                 : 4mn 49s
Bit rate mode                            : Constant
Bit rate                                 : 320 Kbps
Channel(s)                               : 2 channels
Sampling rate                            : 44.1 KHz
Compression mode                         : Lossy
Stream size                              : 11.0 MiB (100%)


[COLOR=#000000][COLOR=#000000]


then do the muxing!   [an ancient dance ::]]]


[/COLOR][/COLOR]> [B]ffmpeg -i *bulgaria*.mp3  -i 'amarilla.png' -s hd720 -c:a copy Bulgaria.mkv
[/B]
ffmpeg version git-2013-03-11-1123080 Copyright (c) 2000-2013 the FFmpeg developers
  built on Mar 11 2013 18:18:28 with gcc 4.7 (Ubuntu/Linaro 4.7.2-22ubuntu3)
  configuration: --enable-gpl --enable-libass --enable-libfaac --enable-libfdk-aac --enable-libmp3lame --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libspeex --enable-librtmp --enable-libtheora --enable-libvorbis --enable-x11grab --enable-nonfree --enable-version3
  libavutil      52. 19.100 / 52. 19.100
  libavcodec     54. 92.100 / 54. 92.100
  libavformat    54. 63.104 / 54. 63.104
  libavdevice    54.  3.103 / 54.  3.103
  libavfilter     3. 44.101 /  3. 44.101
  libswscale      2.  2.100 /  2.  2.100
  libswresample   0. 17.102 /  0. 17.102
  libpostproc    52.  2.100 / 52.  2.100
[mp3 @ 0x2c9e8e0] max_analyze_duration 5000000 reached at 5015510 microseconds
[mp3 @ 0x2c9e8e0] Estimating duration from bitrate, this may be inaccurate
Input #0, mp3, from 'bulgaria.mp3':
  Metadata:
    encoder         : LAME 64bits version 3.99.5 ([http://lame.sf.net](http://lame.sf.net))
    TLEN            : 288810
  Duration: 00:04:48.87, start: 0.000000, bitrate: 320 kb/s
    Stream #0:0: Audio: mp3, 44100 Hz, stereo, s16p, 320 kb/s
[image2 @ 0x2ca0d00] Stream #0: not enough frames to estimate rate; consider increasing probesize
Input #1, image2, from 'amarilla.png':
  Duration: 00:00:00.04, start: 0.000000, bitrate: N/A
    Stream #1:0: Video: png, rgb24, 2816x2244 [SAR 18898:18898 DAR 64:51], 25 tbr, 25 tbn, 25 tbc
Output #0, matroska, to 'Bulgaria.mkv':
  Metadata:
    TLEN            : 288810
    encoder         : Lavf54.63.104
    Stream #0:0: Video: mpeg4 (FMP4 / 0x34504D46), yuv420p, 1280x720 [SAR 12:17 DAR 64:51], q=2-31, 200 kb/s, 1k tbn, 25 tbc
    Stream #0:1: Audio: mp3 (U[0][0][0] / 0x0055), 44100 Hz, stereo, 320 kb/s
Stream mapping:
  Stream #1:0 -> #0:0 (png -> mpeg4)
  Stream #0:0 -> #0:1 (copy)
Press [q] to stop, [?] for help
frame=    1 fps=0.0 q=6.2 size=       1kB time=00:00:00.04 bitrate= 132.8kbits/sframe=    1 fps=0.8 q=6.2 size=      65kB time=00:04:11.82 bitrate=   2.1kbits/sframe=    1 fps=0.7 q=6.2 Lsize=   11427kB time=00:04:48.86 bitrate= 324.1kbits/s    
video:67kB audio:11284kB subtitle:0 global headers:0kB muxing overhead 0.679931%


[COLOR=#000000][COLOR=#000000]


then play it in vlc and mplayer

[/COLOR][/COLOR]> mplayer Bulgaria.mkvMPlayer2 UNKNOWN (C) 2000-2012 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.


Playing Bulgaria.mkv.
[mkv] Track ID 1: video (V_MPEG4/ISO/ASP), -vid 0
[mkv] Track ID 2: audio (A_MPEG/L3), -aid 0, -alang und
[mkv] Will play video track 1.
Detected file format: Matroska
VIDEO:  [mp4v]  1280x720  24bpp  25.000 fps    0.0 kbps ( 0.0 kbyte/s)
Clip info:
 TLEN: 288810
 ENCODER: Lavf54.63.104
Load subtitles in .
==========================================================================
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffodivx] vfm: ffmpeg (FFmpeg MPEG-4)
==========================================================================
==========================================================================
Requested audio codec family [mpg123] (afm=mpg123) not available.
Enable it at compilation.
Opening audio decoder: [ffmpeg] FFmpeg/libavcodec audio decoders
AUDIO: 44100 Hz, 2 ch, floatle, 128.0 kbit/4.54% (ratio: 16000->352800)
Selected audio codec: [ffmp3float] afm: ffmpeg (FFmpeg MPEG layer-3 audio)
==========================================================================
AO: [pulse] 44100Hz 2ch floatle (4 bytes per sample)
Starting playback...
Movie-Aspect is 1.26:1 - prescaling to correct movie aspect.
VO: [vdpau] 1280x720 => 1280x1020 Planar YV12 
[vdpau] Got display refresh rate 60.000 Hz.
[vdpau] If that value looks wrong give the -vo vdpau:fps=X suboption manually.


Too many audio packets in the buffer: (4096 in 4279903 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.
A:   0.0 V:   0.0 A-V:  0.002 ct:  0.000   0/  0 ??% ??% ??,?% 0 0 


Too many audio packets in the buffer: (4096 in 4279902 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.
A:   0.0 V:   0.0 A-V:  0.002 ct:  0.000   0/  0 ??% ??% ??,?% 0 0 


Too many audio packets in the buffer: (4096 in 4279902 bytes).
Maybe you are playing a non-interleaved stream/file or the codec failed?
For AVI files, try to force non-interleaved mode with the -ni option.
A:   0.0 V:   0.0 A-V:  0.002 ct:  0.000   0/  0 ??% ??% ??,?% 0 0 





A:   0.1 V:   0.0 A-V:  0.002 ct:  0.000   0/  0 ??% ??% ??,?% 0 0[COLOR=#000000][COLOR=#000000]


and fine both times despite message in mplayer


now to YT

and i get:  [/COLOR][/COLOR][COLOR=#000000][COLOR=#000000]

[/COLOR][/COLOR][ATTACH=CONFIG]245755[/ATTACH]
[COLOR=#000000][COLOR=#000000]

so [/COLOR][/COLOR][COLOR=#000000]Temüjin rightly points out that YT does not list mkv altho i suspect it is [/COLOR].MPEG4 in the list below[COLOR=#000000]
[/COLOR][COLOR=#000000][COLOR=#000000]
[/COLOR][/COLOR]> Supported YouTube file formats

Not sure which format to save your video? Receiving an "invalid file format error message when you're uploading"? 


Make sure that you&#8217;re using one of the following formats:
.MOV
.MPEG4
.AVI
.WMV
.MPEGPS
.FLV
3GPP
WebM


If you're using a file format that's not listed above, use this troubleshooter to learn how to convert your file.


Select the file format you'd like to convert
.mp3, .wav, .jpg, .png 
mswmm (Movie maker project file), .msdvd (DVD Maker project file), .wlmp (Movie maker project file) 
.camproj (Camtasia project file) 
imovieproject, .dvdproj (iDVD project file), .rcproject (iMovie project file) 
.piv 

Other[COLOR=#000000][COLOR=#000000]



So i try with avi

[/COLOR][/COLOR]> ffmpeg -i *bulgaria*.mp3  -i 'amarilla.png' -s hd720 -c:a copy Bulgaria.avi

ffmpeg version git-2013-03-11-1123080 Copyright (c) 2000-2013 the FFmpeg developers
  built on Mar 11 2013 18:18:28 with gcc 4.7 (Ubuntu/Linaro 4.7.2-22ubuntu3)
  configuration: --enable-gpl --enable-libass --enable-libfaac --enable-libfdk-aac --enable-libmp3lame --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libspeex --enable-librtmp --enable-libtheora --enable-libvorbis --enable-x11grab --enable-nonfree --enable-version3
  libavutil      52. 19.100 / 52. 19.100
  libavcodec     54. 92.100 / 54. 92.100
  libavformat    54. 63.104 / 54. 63.104
  libavdevice    54.  3.103 / 54.  3.103
  libavfilter     3. 44.101 /  3. 44.101
  libswscale      2.  2.100 /  2.  2.100
  libswresample   0. 17.102 /  0. 17.102
  libpostproc    52.  2.100 / 52.  2.100
[mp3 @ 0x1f458e0] max_analyze_duration 5000000 reached at 5015510 microseconds
[mp3 @ 0x1f458e0] Estimating duration from bitrate, this may be inaccurate
Input #0, mp3, from 'bulgaria.mp3':
  Metadata:
    encoder         : LAME 64bits version 3.99.5 ([http://lame.sf.net](http://lame.sf.net))
    TLEN            : 288810
  Duration: 00:04:48.87, start: 0.000000, bitrate: 320 kb/s
    Stream #0:0: Audio: mp3, 44100 Hz, stereo, s16p, 320 kb/s
[image2 @ 0x1f47d00] Stream #0: not enough frames to estimate rate; consider increasing probesize
Input #1, image2, from 'amarilla.png':
  Duration: 00:00:00.04, start: 0.000000, bitrate: N/A
    Stream #1:0: Video: png, rgb24, 2816x2244 [SAR 18898:18898 DAR 64:51], 25 tbr, 25 tbn, 25 tbc
Output #0, avi, to 'Bulgaria.avi':
  Metadata:
    TLEN            : 288810
    ISFT            : Lavf54.63.104
    Stream #0:0: Video: mpeg4 (FMP4 / 0x34504D46), yuv420p, 1280x720 [SAR 12:17 DAR 64:51], q=2-31, 200 kb/s, 25 tbn, 25 tbc
    Stream #0:1: Audio: mp3 (U[0][0][0] / 0x0055), 44100 Hz, stereo, 320 kb/s
Stream mapping:
  Stream #1:0 -> #0:0 (png -> mpeg4)
  Stream #0:0 -> #0:1 (copy)
Press [q] to stop, [?] for help
frame=    1 fps=1.0 q=6.2 Lsize=   11629kB time=00:04:48.86 bitrate= 329.8kbits/s    
video:67kB audio:11284kB subtitle:0 global headers:0kB muxing overhead 2.455051%


[COLOR=#000000][COLOR=#000000]


and read with mediainfo

[/COLOR][/COLOR]> mediainfo Bulgaria.aviGeneral
Complete name                            : Bulgaria.avi
Format                                   : AVI
Format/Info                              : Audio Video Interleave
File size                                : 11.4 MiB
Duration                                 : 4mn 48s
Overall bit rate                         : 330 Kbps
Writing application                      : Lavf54.63.104


Video
ID                                       : 0
Format                                   : MPEG-4 Visual
Format profile                           : Simple@L1
Format settings, BVOP                    : No
Format settings, QPel                    : No
Format settings, GMC                     : No warppoints
Format settings, Matrix                  : Default (H.263)
Codec ID                                 : FMP4
Duration                                 : 40ms
Bit rate                                 : 13.6 Mbps
Width                                    : 1 280 pixels
Height                                   : 720 pixels
Display aspect ratio                     : 5:4
Frame rate                               : 25.000 fps
Color space                              : YUV
Chroma subsampling                       : 4:2:0
Bit depth                                : 8 bits
Scan type                                : Progressive
Compression mode                         : Lossy
Bits/(Pixel*Frame)                       : 0.592
Stream size                              : 66.6 KiB (1%)
Writing library                          : Lavc54.92.100


Audio
ID                                       : 1
Format                                   : MPEG Audio
Format version                           : Version 1
Format profile                           : Layer 3
Mode                                     : Joint stereo
Codec ID                                 : 55
Codec ID/Hint                            : MP3
Duration                                 : 4mn 48s
Bit rate mode                            : Constant
Bit rate                                 : 320 Kbps
Channel(s)                               : 2 channels
Sampling rate                            : 44.1 KHz
Compression mode                         : Lossy
Stream size                              : 11.0 MiB (97%)
Alignment                                : Aligned on interleaves

Interleave, duration                     : 0 ms (0.00 video frame)[COLOR=#000000][COLOR=#000000]



and back to YT   and sadly  Same Result!


so now to kdenlive where it will take much longer..   and not the 20 seconds it takes on ffmpeg 

[/COLOR][/COLOR]

[[IMG]http://img580.imageshack.us/img580/4785/e7k2.th.png[/IMG]]("http://img580.imageshack.us/img580/4785/e7k2.png")


and gives this


> mediainfo Bulgaria.m2tGeneral
ID                                       : 1 (0x1)
Complete name                            : Bulgaria.m2t
Format                                   : MPEG-TS
Commercial name                          : HDV 720p
File size                                : 96.4 MiB
Duration                                 : 4mn 48s
Overall bit rate mode                    : Variable
Overall bit rate                         : 2 801 Kbps


Video
ID                                       : 256 (0x100)
Menu ID                                  : 1 (0x1)
Format                                   : MPEG Video
Commercial name                          : HDV 720p
Format version                           : Version 2
Format profile                           : Main@High 1440
Format settings, BVOP                    : No
Format settings, Matrix                  : Default
Format settings, GOP                     : M=1, N=12
Codec ID                                 : 2
Duration                                 : 4mn 48s
Bit rate mode                            : Variable
Bit rate                                 : 2 275 Kbps
Width                                    : 1 280 pixels
Height                                   : 720 pixels
Display aspect ratio                     : 16:9
Frame rate                               : 25.000 fps
Color space                              : YUV
Chroma subsampling                       : 4:2:0
Bit depth                                : 8 bits
Scan type                                : Progressive
Compression mode                         : Lossy
Bits/(Pixel*Frame)                       : 0.099
Stream size                              : 78.3 MiB (81%)


Audio
ID                                       : 257 (0x101)
Menu ID                                  : 1 (0x1)
Format                                   : MPEG Audio
Format version                           : Version 1
Format profile                           : Layer 2
Codec ID                                 : 3
Duration                                 : 4mn 48s
Bit rate mode                            : Constant
Bit rate                                 : 384 Kbps
Channel(s)                               : 2 channels
Sampling rate                            : 48.0 KHz
Compression mode                         : Lossy
Stream size                              : 13.2 MiB (14%)


Menu
ID                                       : 4096 (0x1000)
Menu ID                                  : 1 (0x1)
Duration                                 : 4mn 48s
List                                     : 256 (0x100) (MPEG Video) / 257 (0x101) (MPEG Audio)
Service name                             : Service01
Service provider                         : Libav
Service type                             : digital television






which is much bigger and therefore takes longer to upload   but is [accepted]("http://www.youtube.com/watch?v=gcjGuRcDGZU")  ::]][COLOR=#000000][COLOR=#000000]

so this is where i have got to.    Any more thoughts?    by all means duplicate see what you get...    i really fancy the ffmpeg route as it is so much quicker and more elegant in my view









[/COLOR][/COLOR]

---

### Post by Yellow Pasque on 2013-08-27
For compatibility's sake, it's probably best to create a WebM file, using the original flac for best quality if possible
```
ffmpeg -i audiofile.flac -i picturefile.png -s hd720 -c:a libvorbis -aq 9 file.webm
```

---

### Post by shantiq on 2013-08-27
does not appear to fly here

> ffmpeg -i *224*.flac -i  amarilla.png -s hd720 -c:a  libvorbis -aq 9  file.webm
ffmpeg version git-2013-03-11-1123080 Copyright (c) 2000-2013 the FFmpeg developers
  built on Mar 11 2013 18:18:28 with gcc 4.7 (Ubuntu/Linaro 4.7.2-22ubuntu3)
  configuration: --enable-gpl --enable-libass --enable-libfaac --enable-libfdk-aac --enable-libmp3lame --enable-libopencore-amrnb --enable-libopencore-amrwb --enable-libspeex --enable-librtmp --enable-libtheora --enable-libvorbis --enable-x11grab --enable-nonfree --enable-version3
  libavutil      52. 19.100 / 52. 19.100
  libavcodec     54. 92.100 / 54. 92.100
  libavformat    54. 63.104 / 54. 63.104
  libavdevice    54.  3.103 / 54.  3.103
  libavfilter     3. 44.101 /  3. 44.101
  libswscale      2.  2.100 /  2.  2.100
  libswresample   0. 17.102 /  0. 17.102
  libpostproc    52.  2.100 / 52.  2.100
[flac @ 0x20a88e0] max_analyze_duration 5000000 reached at 5015510 microseconds
Input #0, flac, from '224.flac':
  Metadata:
    COMMENT         : Processed by SoX
  Duration: 00:04:48.81, bitrate: 671 kb/s
    Stream #0:0: Audio: flac, 44100 Hz, stereo, s16
[image2 @ 0x20d3060] Stream #0: not enough frames to estimate rate; consider increasing probesize
Input #1, image2, from 'amarilla.png':
  Duration: 00:00:00.04, start: 0.000000, bitrate: N/A
    Stream #1:0: Video: png, rgb24, 2816x2244 [SAR 18898:18898 DAR 64:51], 25 tbr, 25 tbn, 25 tbc
File 'file.webm' already exists. Overwrite ? [y/N] y
Output #0, webm, to 'file.webm':
  Metadata:
    COMMENT         : Processed by SoX
    Stream #0:0: Video: none, 1280x720, q=2-31, 128 kb/s, 90k tbn
    Stream #0:1: Audio: none, 0 channels
Stream mapping:
  Stream #1:0 -> #0:0 (png -> ?)
  Stream #0:0 -> #0:1 (flac -> libvorbis)
[COLOR=#ff0000]Encoder (codec none) not found for output stream #0:0[/COLOR]
 

---

### Post by Yellow Pasque on 2013-08-27
Your ffmpeg doesn't appear to be built with libvpx support :\
For that matter, it doesn't appear to support libx264 either.

---

### Post by shantiq on 2013-08-27
OH  that must the reason for my problems here?   i forgot   when i did install    back in March i was only thinking of audio

thanx  Temüjin;   looks like you have spotted the issue

will do a full reinstall on ffmpeg and report

thanx for your advice


===================


well  full reinstall


and still REJECTED by YT

> ffmpeg -i *224*.flac -i amarilla.png -s hd720 -c:a libvorbis -aq 9 file.webm
ffmpeg version git-2013-08-27-16c3ed5 Copyright (c) 2000-2013 the FFmpeg developers
  built on Aug 27 2013 18:43:59 with gcc 4.7 (Ubuntu/Linaro 4.7.3-1ubuntu1)
  configuration: --prefix=/home/shan/ffmpeg_build --extra-cflags=-I/home/shan/ffmpeg_build/include --extra-ldflags=-L/home/shan/ffmpeg_build/lib --bindir=/home/shan/bin --extra-libs=-ldl --enable-gpl --enable-libass --enable-libfdk-aac --enable-libmp3lame --enable-libopus --enable-libtheora --enable-libvorbis **--enable-libvpx --enable-libx264 **--enable-nonfree --enable-x11grab
  libavutil      52. 42.100 / 52. 42.100
  libavcodec     55. 29.100 / 55. 29.100
  libavformat    55. 14.102 / 55. 14.102
  libavdevice    55.  3.100 / 55.  3.100
  libavfilter     3. 82.102 /  3. 82.102
  libswscale      2.  5.100 /  2.  5.100
  libswresample   0. 17.103 /  0. 17.103
  libpostproc    52.  3.100 / 52.  3.100
Input #0, flac, from '224.flac':
  Metadata:
    COMMENT         : Processed by SoX
  Duration: 00:04:48.81, bitrate: 671 kb/s
    Stream #0:0: Audio: flac, 44100 Hz, stereo, s16
[image2 @ 0x204aa00] Stream #0: not enough frames to estimate rate; consider increasing probesize
Input #1, image2, from 'amarilla.png':
  Duration: 00:00:00.04, start: 0.000000, bitrate: N/A
    Stream #1:0: Video: png, rgb24, 2816x2244 [SAR 18898:18898 DAR 64:51], 25 tbr, 25 tbn, 25 tbc
[libvpx @ 0x204c620] v1.2.0
Output #0, webm, to 'file.webm':
  Metadata:
    COMMENT         : Processed by SoX
    encoder         : Lavf55.14.102
    Stream #0:0: Video: vp8 (libvpx), yuv420p, 1280x720 [SAR 12:17 DAR 64:51], q=-1--1, 200 kb/s, 1k tbn, 25 tbc
    Stream #0:1: Audio: vorbis (libvorbis), 44100 Hz, stereo, fltp
Stream mapping:
  Stream #1:0 -> #0:0 (png -> libvpx)
  Stream #0:0 -> #0:1 (flac -> libvorbis)
Press [q] to stop, [?] for help
frame=    1 fps=0.0 q=0.0 size=       4kB time=00:00:00.04 bitrate= 907.2kbits/sframe=    1 fps=0.7 q=0.0 size=      38kB time=00:00:08.00 bitrate=  38.8kbits/sframe=    1 fps=0.5 q=0.0 size=      38kB time=00:00:16.09 bitrate=  19.3kbits/sframe=    1 fps=0.4 q=0.0 size=      38kB time=00:00:23.79 bitrate=  13.1kbits/sframe=    1 fps=0.3 q=0.0 size=      38kB time=00:00:31.69 bitrate=   9.8kbits/sframe=    1 fps=0.3 q=0.0 size=      38kB time=00:00:39.48 bitrate=   7.9kbits/sframe=    1 fps=0.3 q=0.0 size=      38kB time=00:00:47.34 bitrate=   6.6kbits/sframe=    1 fps=0.2 q=0.0 size=      38kB time=00:00:54.54 bitrate=   5.7kbits/sframe=    1 fps=0.2 q=0.0 size=      38kB time=00:01:02.24 bitrate=   5.0kbits/sframe=    1 fps=0.2 q=0.0 size=      38kB time=00:01:10.25 bitrate=   4.4kbits/sframe=    1 fps=0.2 q=0.0 size=      38kB time=00:01:17.92 bitrate=   4.0kbits/sframe=    1 fps=0.2 q=0.0 size=      38kB time=00:01:25.33 bitrate=   3.6kbits/sframe=    1 fps=0.1 q=0.0 size=      38kB time=00:01:32.78 bitrate=   3.3kbits/sframe=    1 fps=0.1 q=0.0 size=      38kB time=00:01:40.51 bitrate=   3.1kbits/sframe=    1 fps=0.1 q=0.0 size=      38kB time=00:01:48.11 bitrate=   2.9kbits/sframe=    1 fps=0.1 q=0.0 size=      38kB time=00:01:55.84 bitrate=   2.7kbits/sframe=    1 fps=0.1 q=0.0 size=      38kB time=00:02:03.07 bitrate=   2.5kbits/sframe=    1 fps=0.1 q=0.0 size=      38kB time=00:02:09.39 bitrate=   2.4kbits/sframe=    1 fps=0.1 q=0.0 size=      38kB time=00:02:15.89 bitrate=   2.3kbits/sframe=    1 fps=0.1 q=0.0 size=      38kB time=00:02:23.55 bitrate=   2.2kbits/sframe=    1 fps=0.1 q=0.0 size=      38kB time=00:02:26.78 bitrate=   2.1kbits/sframe=    1 fps=0.1 q=0.0 size=      38kB time=00:02:32.23 bitrate=   2.0kbits/sframe=    1 fps=0.1 q=0.0 size=      38kB time=00:02:35.04 bitrate=   2.0kbits/sframe=    1 fps=0.1 q=0.0 size=      38kB time=00:02:39.68 bitrate=   1.9kbits/sframe=    1 fps=0.1 q=0.0 size=      38kB time=00:02:44.25 bitrate=   1.9kbits/sframe=    1 fps=0.1 q=0.0 size=      38kB time=00:02:50.97 bitrate=   1.8kbits/sframe=    1 fps=0.1 q=0.0 size=      38kB time=00:02:57.36 bitrate=   1.8kbits/sframe=    1 fps=0.1 q=0.0 size=      38kB time=00:03:04.48 bitrate=   1.7kbits/sframe=    1 fps=0.1 q=0.0 size=      38kB time=00:03:12.14 bitrate=   1.6kbits/sframe=    1 fps=0.1 q=0.0 size=      38kB time=00:03:19.32 bitrate=   1.6kbits/sframe=    1 fps=0.1 q=0.0 size=      38kB time=00:03:27.03 bitrate=   1.5kbits/sframe=    1 fps=0.1 q=0.0 size=      38kB time=00:03:33.72 bitrate=   1.5kbits/sframe=    1 fps=0.1 q=0.0 size=      38kB time=00:03:41.43 bitrate=   1.4kbits/sframe=    1 fps=0.1 q=0.0 size=      38kB time=00:03:49.01 bitrate=   1.4kbits/sframe=    1 fps=0.1 q=0.0 size=      38kB time=00:03:56.43 bitrate=   1.3kbits/sframe=    1 fps=0.1 q=0.0 size=      38kB time=00:04:03.92 bitrate=   1.3kbits/sframe=    1 fps=0.1 q=0.0 size=      38kB time=00:04:11.43 bitrate=   1.2kbits/sframe=    1 fps=0.1 q=0.0 size=      38kB time=00:04:18.16 bitrate=   1.2kbits/sframe=    1 fps=0.0 q=0.0 size=      38kB time=00:04:25.57 bitrate=   1.2kbits/sframe=    1 fps=0.0 q=0.0 size=      38kB time=00:04:33.11 bitrate=   1.1kbits/sframe=    1 fps=0.0 q=0.0 size=      38kB time=00:04:40.50 bitrate=   1.1kbits/sframe=    1 fps=0.0 q=0.0 size=      38kB time=00:04:48.40 bitrate=   1.1kbits/sframe=    1 fps=0.0 q=0.0 Lsize=   11887kB time=00:04:48.79 bitrate= 337.2kbits/s    
video:33kB audio:11686kB subtitle:0 global headers:4kB muxing overhead 1.400899%


why does it accept the Kdenlive version but not the ffmpeg?   what is in it that is missing in the ffmpeg mux?

Kdenlive mux

> mediainfo Bulgaria.m2tGeneral
 ID : 1 (0x1)
 Complete name : Bulgaria.m2t
 Format : MPEG-TS
 Commercial name : HDV 720p
 File size : 96.4 MiB
 Duration : 4mn 48s
 Overall bit rate mode : Variable
 Overall bit rate : 2 801 Kbps


 Video
 ID : 256 (0x100)
 Menu ID : 1 (0x1)
 Format : MPEG Video
 Commercial name : HDV 720p
 Format version : Version 2
 Format profile : Main@High 1440
 Format settings, BVOP : No
 Format settings, Matrix : Default
 Format settings, GOP : M=1, N=12
 Codec ID : 2
 Duration : 4mn 48s
 Bit rate mode : Variable
 Bit rate : 2 275 Kbps
 Width : 1 280 pixels
 Height : 720 pixels
 Display aspect ratio : 16:9
 Frame rate : 25.000 fps
 Color space : YUV
 Chroma subsampling : 4:2:0
 Bit depth : 8 bits
 Scan type : Progressive
 Compression mode : Lossy
 Bits/(Pixel*Frame) : 0.099
 Stream size : 78.3 MiB (81%)


 Audio
 ID : 257 (0x101)
 Menu ID : 1 (0x1)
 Format : MPEG Audio
 Format version : Version 1
 Format profile : Layer 2
 Codec ID : 3
 Duration : 4mn 48s
 Bit rate mode : Constant
 Bit rate : 384 Kbps
 Channel(s) : 2 channels
 Sampling rate : 48.0 KHz
 Compression mode : Lossy
 Stream size : 13.2 MiB (14%)


 Menu
 ID : 4096 (0x1000)
 Menu ID : 1 (0x1)
 Duration : 4mn 48s
 List : 256 (0x100) (MPEG Video) / 257 (0x101) (MPEG Audio)
 Service name : Service01
 Service provider : Libav
 Service type : digital television

---

### Post by FakeOutdoorsman on 2013-08-27
Try adding "-loop 1":

```
ffmpeg -loop 1 -i image.png -i music.mp3 -c:a copy -c:v libx264 -crf 0 -preset veryslow -shortest output.mkv
```
or maybe:
```
ffmpeg -loop 1 -r 2 -i image.png -i music.mp3 -c:a copy -c:v libx264 -crf 0 -preset veryslow -shortest output.mkv
```

I tried several combinations of various options to try to break YouTube and the only ones it didn't like were without "-loop 1":

```
ffmpeg -i normal.png -c:v libx264 -crf 0 -t 10 testsrc-crf0.mkv
ffmpeg -i normal.png -c copy -t 10 testsrc-copy.mkv
```

---

### Post by shantiq on 2013-08-28
ha thanx for that research FakeO

i understand now that what i was trying to upload in earlier attempts was in effect a sound file with ONE image only

so this explains why it took just a few seconds to obtain and why YT rejects them.  They are not video files only have the name of them

Of course now it takes the same time it takes Kdenlive but at least it is command line which i favour when choice is there

**PS   **had to add   >  -s   hd720    since my original image was 2300x2800   or somesuch and i only need 720p


Thanx to you and to Temüjin for help and time 
marked as solved   [YT is now happy!]

of course it now takes same time as Kdenlive:KS




>  [B]ffmpeg -loop 1 -i amarilla.png -i bulgaria.mp3 -c:a copy -c:v libx264 -crf 0 -preset veryslow -s hd720 -shortest output.mkv
[/B]

shan@shan:~/us music/king$ ffmpeg -loop 1 -i amarilla.png -i bulgaria.mp3 -c:a copy -c:v libx264 -crf 0 -preset veryslow -s hd720 -shortest output.mkv
ffmpeg version git-2013-08-27-16c3ed5 Copyright (c) 2000-2013 the FFmpeg developers
  built on Aug 27 2013 18:43:59 with gcc 4.7 (Ubuntu/Linaro 4.7.3-1ubuntu1)
  configuration: --prefix=/home/shan/ffmpeg_build --extra-cflags=-I/home/shan/ffmpeg_build/include --extra-ldflags=-L/home/shan/ffmpeg_build/lib --bindir=/home/shan/bin --extra-libs=-ldl --enable-gpl --enable-libass --enable-libfdk-aac --enable-libmp3lame --enable-libopus --enable-libtheora --enable-libvorbis --enable-libvpx --enable-libx264 --enable-nonfree --enable-x11grab
  libavutil      52. 42.100 / 52. 42.100
  libavcodec     55. 29.100 / 55. 29.100
  libavformat    55. 14.102 / 55. 14.102
  libavdevice    55.  3.100 / 55.  3.100
  libavfilter     3. 82.102 /  3. 82.102
  libswscale      2.  5.100 /  2.  5.100
  libswresample   0. 17.103 /  0. 17.103
  libpostproc    52.  3.100 / 52.  3.100
[image2 @ 0x308c500] Stream #0: not enough frames to estimate rate; consider increasing probesize
Input #0, image2, from 'amarilla.png':
  Duration: 00:00:00.04, start: 0.000000, bitrate: N/A
    Stream #0:0: Video: png, rgb24, 2816x2244 [SAR 18898:18898 DAR 64:51], 25 tbr, 25 tbn, 25 tbc
[mp3 @ 0x308e000] Estimating duration from bitrate, this may be inaccurate
Input #1, mp3, from 'bulgaria.mp3':
  Metadata:
    encoder         : LAME 64bits version 3.99.5 ([http://lame.sf.net](http://lame.sf.net))
    TLEN            : 288810
  Duration: 00:04:48.87, start: 0.000000, bitrate: 320 kb/s
    Stream #1:0: Audio: mp3, 44100 Hz, stereo, s16p, 320 kb/s
File 'output.mkv' already exists. Overwrite ? [y/N] y
No pixel format specified, yuv444p for H.264 encoding chosen.
Use -pix_fmt yuv420p for compatibility with outdated media players.
[libx264 @ 0x3090de0] using SAR=12/17
[libx264 @ 0x3090de0] using cpu capabilities: MMX2 SSE2Slow SlowCTZ
[libx264 @ 0x3090de0] profile High 4:4:4 Predictive, level 5.0, 4:4:4 8-bit
[libx264 @ 0x3090de0] 264 - core 138 r2 9e941d1 - H.264/MPEG-4 AVC codec - Copyleft 2003-2013 - [http://www.videolan.org/x264.html](http://www.videolan.org/x264.html) - options: cabac=1 ref=16 deblock=1:0:0 analyse=0x3:0x133 me=umh subme=9 psy=0 mixed_ref=1 me_range=24 chroma_me=1 trellis=0 8x8dct=1 cqm=0 deadzone=21,11 fast_pskip=0 chroma_qp_offset=0 threads=1 lookahead_threads=1 sliced_threads=0 nr=0 decimate=1 interlaced=0 bluray_compat=0 constrained_intra=0 bframes=0 weightp=2 keyint=250 keyint_min=25 scenecut=40 intra_refresh=0 rc=cqp mbtree=0 qp=0
Output #0, matroska, to 'output.mkv':
  Metadata:
    encoder         : Lavf55.14.102
    Stream #0:0: Video: h264 (libx264) (H264 / 0x34363248), yuv444p, 1280x720 [SAR 12:17 DAR 64:51], q=-1--1, 1k tbn, 25 tbc
    Stream #0:1: Audio: mp3 (U[0][0][0] / 0x0055), 44100 Hz, stereo, 320 kb/s
Stream mapping:
  Stream #0:0 -> #0:0 (png -> libx264)
  Stream #1:0 -> #0:1 (copy)
Press [q] to stop, [?] for help
frame=    2 fps=0.0 q=0.0 size=       1kB time=00:00:00.04 bitrate= 127.4kbits/sframe=    3 fps=1.4 q=0.0 size=       1kB time=00:00:00.08 bitrate=  63.7kbits/sframe=    3 fps=1.0 q=0.0 size=     940kB time=00:00:00.08 bitrate=96222.3kbits/frame=    4 fps=1.0 q=0.0 size=     943kB time=00:00:00.12 bitrate=64361.6kbits/frame=    5 fps=1.1 q=0.0 size=     945kB time=00:00:00.16 bitrate=48381.4kbits/frame=    6 fps=1.1 q=0.0 size=     945kB time=00:00:00.20 bitrate=38705.1kbits/frame=    6 fps=0.3 q=0.0 size=     946kB time=00:00:00.20 bitrate=38747.2kbits/frame=    7 fps=0.3 q=0.0 size=     948kB time=00:00:00.24 bitrate=32362.9kbits/frame=    8 fps=0.3 q=0.0 size=     949kB time=00:00:00.28 bitrate=27769.7kbits/frame=    9 fps=0.3 q=0.0 size=     951kB time=00:00:00.32 bitrate=24353.7kbits/frame=   10 fps=0.4 q=0.0 size=     952kB time=00:00:00.36 bitrate=21671.1kbits/frame=   11 fps=0.4 q=0.0 size=     955kB time=00:00:00.40 bitrate=19548.2kbits/frame=   12 fps=0.4 q=0.0 size=     956kB time=00:00:00.44 bitrate=17790.2kbits/frame=   13 fps=0.4 q=0.0 size=     958kB time=00:00:00.48 bitrate=16344.6kbits/frame=   14 fps=0.5 q=0.0 size=     959kB time=00:00:00.52 bitrate=15103.5kbits/frame=   15 fps=0.5 q=0.0 size=     961kB time=00:00:00.56 bitrate=14056.3kbits/frame=   15 fps=0.5 q=0.0 size=     961kB time=00:00:05.09 bitrate=1545.3kbits/sframe=   15 fps=0.5 q=0.0 size=     961kB time=00:00:05.09 bitrate=1545.3kbits/sframe=   15 fps=0.5 q=0.0 size=     961kB time=00:00:05.09 bitrate=1545.3kbits/sframe=   15 fps=0.5 q=0.0 size=     961kB time=00:00:07.34 bitrate=1072.4kbits/sframe=   15 fps=0.5 q=0.0 size=     961kB time=00:00:26.98 bitrate= 291.7kbits/sframe=   16 fps=0.5 q=0.0 size=     963kB time=00:00:40.09 bitrate= 196.7kbits/sframe=   16 fps=0.5 q=0.0 size=     963kB time=00:00:59.76 bitrate= 132.0kbits/sframe=   16 fps=0.5 q=0.0 size=     963kB time=00:01:19.41 bitrate=  99.3kbits/sframe=   16 fps=0.4 q=0.0 size=     963kB time=00:01:32.52 bitrate=  85.3kbits/sframe=   16 fps=0.4 q=0.0 size=     963kB time=00:01:45.63 bitrate=  74.7kbits/sframe=   16 fps=0.4 q=0.0 size=     963kB time=00:02:05.30 bitrate=  63.0kbits/sframe=   16 fps=0.4 q=0.0 size=     963kB time=00:02:24.95 bitrate=  54.4kbits/sframe=   16 fps=0.4 q=0.0 size=     963kB time=00:02:31.51 bitrate=  52.1kbits/sframe=   16 fps=0.4 q=0.0 size=     963kB time=00:02:44.62 bitrate=  47.9kbits/sframe=   16 fps=0.4 q=0.0 size=     963kB time=00:02:57.73 bitrate=  44.4kbits/sframe=   16 fps=0.4 q=0.0 size=     963kB time=00:03:10.82 bitrate=  41.3kbits/sframe=   16 fps=0.4 q=0.0 size=     963kB time=00:03:23.93 bitrate=  38.7kbits/sframe=   16 fps=0.4 q=0.0 size=     963kB time=00:03:43.60 bitrate=  35.3kbits/sframe=   16 fps=0.4 q=0.0 size=     963kB time=00:04:03.25 bitrate=  32.4kbits/sframe=   16 fps=0.4 q=0.0 size=     963kB time=00:04:16.36 bitrate=  30.8kbits/sframe=   16 fps=0.4 q=0.0 size=     963kB time=00:04:29.47 bitrate=  29.3kbits/sframe=   16 fps=0.4 q=0.0 size=     963kB time=00:04:42.59 bitrate=  27.9kbits/sframe=   16 fps=0.3 q=0.0 Lsize=   12301kB time=00:04:48.86 bitrate= 348.8kbits/s    
video:940kB audio:11284kB subtitle:0 global headers:0kB muxing overhead 0.631927%
[libx264 @ 0x3090de0] frame I:1     Avg QP: 0.00  size:961035
[libx264 @ 0x3090de0] frame P:15    Avg QP: 0.00  size:    47
[libx264 @ 0x3090de0] mb I  I16..4: 71.9% 13.2% 14.8%
[libx264 @ 0x3090de0] mb P  I16..4:  0.0%  0.0%  0.0%  P16..4:  0.0%  0.0%  0.0%  0.0%  0.0%    skip:100.0%
[libx264 @ 0x3090de0] 8x8 transform intra:13.2%
[libx264 @ 0x3090de0] coded y,u,v intra: 100.0% 99.7% 99.9% inter: 0.0% 0.0% 0.0%
[libx264 @ 0x3090de0] i16 v,h,dc,p: 23% 73%  4%  0%
[libx264 @ 0x3090de0] i8 v,h,dc,ddl,ddr,vr,hd,vl,hu: 33% 64%  1%  0%  1%  0%  0%  0%  0%
[libx264 @ 0x3090de0] i4 v,h,dc,ddl,ddr,vr,hd,vl,hu: 28% 59%  5%  1%  3%  1%  1%  1%  0%
[libx264 @ 0x3090de0] Weighted P-Frames: Y:0.0% UV:0.0%
[libx264 @ 0x3090de0] kb/s:12021.74






> mediainfo output.mkvGeneral
Unique ID                                : 197517132504802764748703615868033379494 (0x94986A7F1C4048CFC88F95FF10252CA6)
Complete name                            : output.mkv
Format                                   : Matroska
Format version                           : Version 2
File size                                : 12.0 MiB
Duration                                 : 4mn 48s
Overall bit rate                         : 349 Kbps
Writing application                      : Lavf55.14.102
Writing library                          : Lavf55.14.102


Video
ID                                       : 1
Format                                   : AVC
Format/Info                              : Advanced Video Codec
Format profile                           : High 4:4:4 Predictive@L5.0
Format settings, CABAC                   : Yes
Format settings, ReFrames                : 16 frames
Codec ID                                 : V_MPEG4/ISO/AVC
Duration                                 : 4mn 48s
Bit rate                                 : 21.9 Kbps
Width                                    : 1 280 pixels
Height                                   : 720 pixels
Display aspect ratio                     : 5:4
Original display aspect ratio            : 5:4
Frame rate mode                          : Constant
Frame rate                               : 25.000 fps
Color space                              : YUV
Chroma subsampling                       : 4:4:4
Bit depth                                : 8 bits
Scan type                                : Progressive
Bits/(Pixel*Frame)                       : 0.001
Stream size                              : 772 KiB (6%)
Writing library                          : x264 core 138 r2 9e941d1
Encoding settings                        : cabac=1 / ref=16 / deblock=1:0:0 / analyse=0x3:0x133 / me=umh / subme=9 / psy=0 / mixed_ref=1 / me_range=24 / chroma_me=1 / trellis=0 / 8x8dct=1 / cqm=0 / deadzone=21,11 / fast_pskip=0 / chroma_qp_offset=0 / threads=1 / lookahead_threads=1 / sliced_threads=0 / nr=0 / decimate=1 / interlaced=0 / bluray_compat=0 / constrained_intra=0 / bframes=0 / weightp=2 / keyint=250 / keyint_min=25 / scenecut=40 / intra_refresh=0 / rc=cqp / mbtree=0 / qp=0
Default                                  : Yes
Forced                                   : No


Audio
ID                                       : 2
Format                                   : MPEG Audio
Format version                           : Version 1
Format profile                           : Layer 3
Mode                                     : Joint stereo
Codec ID                                 : A_MPEG/L3
Codec ID/Hint                            : MP3
Duration                                 : 4mn 48s
Bit rate mode                            : Constant
Bit rate                                 : 320 Kbps
Channel(s)                               : 2 channels
Sampling rate                            : 44.1 KHz
Compression mode                         : Lossy
Stream size                              : 11.0 MiB (92%)
Default                                  : Yes
Forced                                   : No

---

### Post by FakeOutdoorsman on 2013-08-28
> **shantiq said:**
> had to add -s hd720  since my original image was 2300x2800   or somesuch and i only one 720p

Consider using "-vf scale=-1:720" instead of "-s hd720". In this example scale will automatically choose the correct width with your declared height to preserve aspect, otherwise -s can stretch or squish your output by make a "hard" resize to hd720 (1280x720).

---

### Post by shantiq on 2013-08-29
actually s hd was fine in my case but  problem is muxing takes possibly [?]longer than Kdenlive to process    ....   not sure why
and Kdenlive uses ffmpeg for its muxing   ...   mind you hard to tell about time since muxing never seems to take the same amount of time
i shall prepare the image so it is the size i want with Gimp first   then remove size switches on the command  ...     that should reduce the time?

---

### Post by FakeOutdoorsman on 2013-08-29
-r 2 input, -r 25 output
```
$ time ffmpeg -y -loop 1 -r 2 -i image.png -i music.mp3 -c:a copy -c:v libx264 -crf 0 -preset veryfast -shortest -r 25 output.mkv
real    0m11.037s
```

-r 2 input
```

$ time ffmpeg -y -loop 1 -r 2 -i image.png -i music.mp3 -c:a copy -c:v libx264 -crf 0 -preset veryfast -shortest output.mkv
real    0m11.070s
```

Default (-r 25 input)
```

$ time ffmpeg -y -loop 1 -i image.png -i music.mp3 -c:a copy -c:v libx264 -crf 0 -preset veryfast -shortest output.mkv
real    2m9.211s
```

---

### Post by shantiq on 2013-08-29
is there a timer for processes on ffmpeg?     i have never seen it.   what do you need to add?   or did you time it some other way?

my muxing took about 25 minutes on a 5 minute video

---

### Post by FakeOutdoorsman on 2013-08-29
I only added "time" to the commands, or you could use the "-benchmark" global option in ffmpeg if you only want utime/user/CPU time.

```
$ time sleep 5
real    0m5.022s
user    0m0.000s
sys     0m0.000s
```

```
$ time ffmpeg -y -f lavfi -i testsrc=d=60 -c:v libx264 output.mkv
...
real    0m1.987s
user    0m7.093s
sys     0m0.363s
```

```
$ ffmpeg -y -benchmark -f lavfi -i testsrc=d=60 -c:v libx264 output.mkv
...
bench: utime=7.037s
bench: maxrss=69480kB
```

> 
&#8216;-benchmark (global)&#8217;

    Show benchmarking information at the end of an encode. Shows CPU time used and maximum memory consumption. Maximum memory consumption is not supported on all systems, it will usually display as 0 if not supported. 

---

### Post by shantiq on 2013-08-30
thank you great tips!
never knew either were there...


ouch! on a 5 minute video

> 
real    106m16.869s
user    64m12.836s
sys    2m37.396s




this my command

> time ffmpeg -y   -loop 1 -i amarilla.png -i bulgaria.mp3 -c:a copy -c:v libx264 -crf 0 -s hd720 -preset veryslow -shortest output2.mkv

will now time Kdenlive on same     and it took   17 minutes

so that is still a huge discrepancy;  not sure what they are using
here first one is the ffmpeg mux    second kdenlive


> mediainfo output2.mkv output.m2t

FFMPEG

General
Unique ID                                : 99222194639135499069259069204543060127 (0x4AA57FE47F27D7431F4D47E633DC389F)
Complete name                            : output2.mkv
Format                                   : Matroska
Format version                           : Version 2
File size                                : 38.1 MiB
Duration                                 : 4mn 48s
Overall bit rate                         : 1 105 Kbps
Writing application                      : Lavf55.14.102
Writing library                          : Lavf55.14.102


Video
ID                                       : 1
Format                                   : AVC
Format/Info                              : Advanced Video Codec
Format profile                           : High 4:4:4 Predictive@L5.0
Format settings, CABAC                   : Yes
Format settings, ReFrames                : 16 frames
Codec ID                                 : V_MPEG4/ISO/AVC
Duration                                 : 4mn 48s
Bit rate                                 : 763 Kbps
Width                                    : 1 280 pixels
Height                                   : 720 pixels
Display aspect ratio                     : 5:4
Original display aspect ratio            : 5:4
Frame rate mode                          : Constant
Frame rate                               : 25.000 fps
Color space                              : YUV
Chroma subsampling                       : 4:4:4
Bit depth                                : 8 bits
Scan type                                : Progressive
Bits/(Pixel*Frame)                       : 0.033
Stream size                              : 26.3 MiB (69%)
Writing library                          : x264 core 138 r2 9e941d1
Encoding settings                        : cabac=1 / ref=16 / deblock=1:0:0 / analyse=0x3:0x133 / me=umh / subme=9 / psy=0 / mixed_ref=1 / me_range=24 / chroma_me=1 / trellis=0 / 8x8dct=1 / cqm=0 / deadzone=21,11 / fast_pskip=0 / chroma_qp_offset=0 / threads=1 / lookahead_threads=1 / sliced_threads=0 / nr=0 / decimate=1 / interlaced=0 / bluray_compat=0 / constrained_intra=0 / bframes=0 / weightp=2 / keyint=250 / keyint_min=25 / scenecut=40 / intra_refresh=0 / rc=cqp / mbtree=0 / qp=0
Default                                  : Yes
Forced                                   : No


Audio
ID                                       : 2
Format                                   : MPEG Audio
Format version                           : Version 1
Format profile                           : Layer 3
Mode                                     : Joint stereo
Codec ID                                 : A_MPEG/L3
Codec ID/Hint                            : MP3
Duration                                 : 4mn 48s
Bit rate mode                            : Constant
Bit rate                                 : 320 Kbps
Channel(s)                               : 2 channels
Sampling rate                            : 44.1 KHz
Compression mode                         : Lossy
Stream size                              : 11.0 MiB (29%)
Default                                  : Yes
Forced                                   : No



KDENLIVE

General
ID                                       : 1 (0x1)
Complete name                            : output.m2t
Format                                   : MPEG-TS
Commercial name                          : HDV 720p
File size                                : 98.2 MiB
Duration                                 : 4mn 53s
Overall bit rate mode                    : Variable
Overall bit rate                         : 2 800 Kbps


Video
ID                                       : 256 (0x100)
Menu ID                                  : 1 (0x1)
Format                                   : MPEG Video
Commercial name                          : HDV 720p
Format version                           : Version 2
Format profile                           : Main@High 1440
Format settings, BVOP                    : No
Format settings, Matrix                  : Default
Format settings, GOP                     : M=1, N=12
Codec ID                                 : 2
Duration                                 : 4mn 53s
Bit rate mode                            : Variable
Bit rate                                 : 2 273 Kbps
Width                                    : 1 280 pixels
Height                                   : 720 pixels
Display aspect ratio                     : 16:9
Frame rate                               : 25.000 fps
Color space                              : YUV
Chroma subsampling                       : 4:2:0
Bit depth                                : 8 bits
Scan type                                : Progressive
Compression mode                         : Lossy
Bits/(Pixel*Frame)                       : 0.099
Stream size                              : 79.6 MiB (81%)


Audio
ID                                       : 257 (0x101)
Menu ID                                  : 1 (0x1)
Format                                   : MPEG Audio
Format version                           : Version 1
Format profile                           : Layer 2
Codec ID                                 : 3
Duration                                 : 4mn 53s
Bit rate mode                            : Constant
Bit rate                                 : 384 Kbps
Channel(s)                               : 2 channels
Sampling rate                            : 48.0 KHz
Compression mode                         : Lossy
Stream size                              : 13.4 MiB (14%)


Menu
ID                                       : 4096 (0x1000)
Menu ID                                  : 1 (0x1)
Duration                                 : 4mn 53s
List                                     : 256 (0x100) (MPEG Video) / 257 (0x101) (MPEG Audio)
Service name                             : Service01
Service provider                         : Libav
Service type                             : digital television




---

### Post by FakeOutdoorsman on 2013-08-30
> **shantiq said:**
> 
this my command
```
time ffmpeg -y -loop 1 -i amarilla.png -i bulgaria.mp3 -c:a copy -c:v libx264 -crf 0 -s hd720 -preset veryslow -shortest output2.mkv
```
Try using "-r 2" as an input option and change veryslow to veryfast if the potential difference in file size (shouldn't be much for static image I believe) is less important than encoding speed:
```
ffmpeg -y -loop 1 -r 2 -i amarilla.png -i bulgaria.mp3 -c:a copy -c:v libx264 -crf 0 -s hd720 -preset veryfast -shortest output2.mkv
```
Fastest would be to [stream copy](http://ffmpeg.org/ffmpeg.html#Stream-copy) everything:
```
ffmpeg -y -loop 1 -i amarilla.png -i bulgaria.mp3 -c copy -shortest output2.mkv
```
Output file size may be large, but it's a tradeoff between encoding speed and file size (we try to keep quality as high as practically possible since YT will re-encode anyway). For static image, depending on the image, -crf 0 (lossless) and -crf 18 (roughly visually lossless) may not vary too significantly in file size or encoding time, so you can compare those too.

ffmpeg console outputs are usually more informative and accurate than mediainfo outputs.

---

### Post by Yellow Pasque on 2013-08-31
shantiq, what CPU do you have?
```
cat /proc/cpuinfo
```

I wonder if using ffmpeg's -threads option will help you. I couldn't get it to show any difference: [http://ubuntuforums.org/showthread.php?t=2168503](http://ubuntuforums.org/showthread.php?t=2168503)

---

### Post by shantiq on 2013-08-31
Yes T.   maybe my machine is not very powerful; i have had it 6 or 7 years now


> cat /proc/cpuinfoprocessor	: 0
vendor_id	: AuthenticAMD
cpu family	: 15
model		: 47
model name	: AMD Athlon(tm) 64 Processor 3400+
stepping	: 2
cpu MHz		: 2200.000
cache size	: 512 KB
fpu		: yes
fpu_exception	: yes
cpuid level	: 1
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt lm 3dnowext 3dnow rep_good nopl extd_apicid pni lahf_lm
bogomips	: 4377.29
TLB size	: 1024 4K pages
clflush size	: 64
cache_alignment	: 64
address sizes	: 40 bits physical, 48 bits virtual
power management: ts fid vid ttp tm stc




---

### Post by Yellow Pasque on 2013-08-31
Well, it's a single-core chip, so multithreading probably won't help. I wonder if '-g 0' would help?

---

### Post by shantiq on 2013-08-31
well Temüjin absolutely fantastic RESULT!   CHECK that time
funnily enough it did not work with -s hd720 as it warped the image but it worked with Fake's suggestion of -vf scale=-1:720



PS   i cannot see that -g switch in ffmpeg -h full       where is it?   what does it do?

ha ok found it

>   -g                 <int>        E..V.. set the group of picture (GOP) size (from INT_MIN to INT_MAX) (default 12)   but it might as well be in sanskrit.   What does it mean?


so that is really SOLVED here i think,   6 minutes and a perfect copy  [if only a bit fat at 450MB for a 5 minute video]

AND   it does not make my computer sound like a revved-up jet engine;   mostly quiet throughout


Thank you very much to both





> **time ffmpeg -y -loop 1 -r 2  -i amarilla.png -i bulgaria.mp3 -c:a copy -c:v libx264 -g  0  -crf 0 -vf scale=-1:720 -preset veryfast -shortest output2.mkv**


ffmpeg version git-2013-08-27-16c3ed5 Copyright (c) 2000-2013 the FFmpeg developers
  built on Aug 27 2013 18:43:59 with gcc 4.7 (Ubuntu/Linaro 4.7.3-1ubuntu1)
  configuration: --prefix=/home/shan/ffmpeg_build --extra-cflags=-I/home/shan/ffmpeg_build/include --extra-ldflags=-L/home/shan/ffmpeg_build/lib --bindir=/home/shan/bin --extra-libs=-ldl --enable-gpl --enable-libass --enable-libfdk-aac --enable-libmp3lame --enable-libopus --enable-libtheora --enable-libvorbis --enable-libvpx --enable-libx264 --enable-nonfree --enable-x11grab
  libavutil      52. 42.100 / 52. 42.100
  libavcodec     55. 29.100 / 55. 29.100
  libavformat    55. 14.102 / 55. 14.102
  libavdevice    55.  3.100 / 55.  3.100
  libavfilter     3. 82.102 /  3. 82.102
  libswscale      2.  5.100 /  2.  5.100
  libswresample   0. 17.103 /  0. 17.103
  libpostproc    52.  3.100 / 52.  3.100
[image2 @ 0x1c29700] Stream #0: not enough frames to estimate rate; consider increasing probesize
Input #0, image2, from 'amarilla.png':
  Duration: 00:00:00.04, start: 0.000000, bitrate: N/A
    Stream #0:0: Video: png, rgb24, 2816x2244 [SAR 18898:18898 DAR 64:51], 25 tbr, 25 tbn, 25 tbc
[mp3 @ 0x1c2b200] Estimating duration from bitrate, this may be inaccurate
Input #1, mp3, from 'bulgaria.mp3':
  Metadata:
    encoder         : LAME 64bits version 3.99.5 ([http://lame.sf.net](http://lame.sf.net))
    TLEN            : 288810
  Duration: 00:04:48.87, start: 0.000000, bitrate: 320 kb/s
    Stream #1:0: Audio: mp3, 44100 Hz, stereo, s16p, 320 kb/s
No pixel format specified, yuv444p for H.264 encoding chosen.
Use -pix_fmt yuv420p for compatibility with outdated media players.
[libx264 @ 0x1c2dfe0] using SAR=1920/1921
[libx264 @ 0x1c2dfe0] using cpu capabilities: MMX2 SSE2Slow SlowCTZ
[libx264 @ 0x1c2dfe0] profile High 4:4:4 Intra, level 3.1, 4:4:4 8-bit
[libx264 @ 0x1c2dfe0] 264 - core 138 r2 9e941d1 - H.264/MPEG-4 AVC codec - Copyleft 2003-2013 - [http://www.videolan.org/x264.html](http://www.videolan.org/x264.html) - options: cabac=1 ref=1 deblock=1:0:0 analyse=0x3:0x113 me=hex subme=2 psy=0 mixed_ref=0 me_range=16 chroma_me=1 trellis=0 8x8dct=1 cqm=0 deadzone=21,11 fast_pskip=0 chroma_qp_offset=0 threads=1 lookahead_threads=1 sliced_threads=0 nr=0 decimate=1 interlaced=0 bluray_compat=0 constrained_intra=0 bframes=0 weightp=0 keyint=1 keyint_min=1 scenecut=40 intra_refresh=0 rc=cqp mbtree=0 qp=0
Output #0, matroska, to 'output2.mkv':
  Metadata:
    encoder         : Lavf55.14.102
    Stream #0:0: Video: h264 (libx264) (H264 / 0x34363248), yuv444p, 904x720 [SAR 1920:1921 DAR 64:51], q=-1--1, 1k tbn, 2 tbc
    Stream #0:1: Audio: mp3 (U[0][0][0] / 0x0055), 44100 Hz, stereo, 320 kb/s
Stream mapping:
  Stream #0:0 -> #0:0 (png -> libx264)
  Stream #1:0 -> #0:1 (copy)
Press [q] to stop, [?] for help
frame=  580 fps=1.6 q=0.0 Lsize=  440008kB time=00:04:50.00 bitrate=12429.5kbits/s    
video:428622kB audio:11284kB subtitle:0 global headers:0kB muxing overhead 0.023305%
[libx264 @ 0x1c2dfe0] frame I:580   Avg QP: 0.00  size:756739
[libx264 @ 0x1c2dfe0] mb I  I16..4: 10.3% 31.0% 58.6%
[libx264 @ 0x1c2dfe0] 8x8 transform intra:31.0%
[libx264 @ 0x1c2dfe0] coded y,u,v intra: 99.1% 98.9% 99.1%
[libx264 @ 0x1c2dfe0] i16 v,h,dc,p: 33% 26% 31% 10%
[libx264 @ 0x1c2dfe0] i8 v,h,dc,ddl,ddr,vr,hd,vl,hu: 16% 22% 28%  4%  5%  7%  5%  7%  6%
[libx264 @ 0x1c2dfe0] i4 v,h,dc,ddl,ddr,vr,hd,vl,hu: 20% 15% 17%  7%  8% 10%  7%  8%  7%
[libx264 @ 0x1c2dfe0] kb/s:12107.82


real    **6m10.671s  !!!**
user    4m41.860s
sys    0m22.140s







ok playing further to reduce the obscene size of 450MB


tried -g 4   -g 8    and finally  -g 7     also moved from 320k mp3 to 192k aac which i understand is the highest YT ever goes for  [might shorten conversion time on YT?]


time is slightly shorter and size down to 92MB   video drops from 4000k to 2000k thereabouts   perfectly adequate


> **time ffmpeg -y -loop 1 -r 2 -i amarilla.png -i bulgaria.mp3 -c:a libfdk_aac -b:a 192k -c:v libx264 -g 7 -crf 0 -s hd720 -preset veryfast -shortest output24.mkv**


ffmpeg version git-2013-08-27-16c3ed5 Copyright (c) 2000-2013 the FFmpeg developers
  built on Aug 27 2013 18:43:59 with gcc 4.7 (Ubuntu/Linaro 4.7.3-1ubuntu1)
  configuration: --prefix=/home/shan/ffmpeg_build --extra-cflags=-I/home/shan/ffmpeg_build/include --extra-ldflags=-L/home/shan/ffmpeg_build/lib --bindir=/home/shan/bin --extra-libs=-ldl --enable-gpl --enable-libass --enable-libfdk-aac --enable-libmp3lame --enable-libopus --enable-libtheora --enable-libvorbis --enable-libvpx --enable-libx264 --enable-nonfree --enable-x11grab
  libavutil      52. 42.100 / 52. 42.100
  libavcodec     55. 29.100 / 55. 29.100
  libavformat    55. 14.102 / 55. 14.102
  libavdevice    55.  3.100 / 55.  3.100
  libavfilter     3. 82.102 /  3. 82.102
  libswscale      2.  5.100 /  2.  5.100
  libswresample   0. 17.103 /  0. 17.103
  libpostproc    52.  3.100 / 52.  3.100
[image2 @ 0x1e3d780] Stream #0: not enough frames to estimate rate; consider increasing probesize
Input #0, image2, from 'amarilla.png':
  Duration: 00:00:00.04, start: 0.000000, bitrate: N/A
    Stream #0:0: Video: png, rgb24, 2816x2244 [SAR 18898:18898 DAR 64:51], 25 tbr, 25 tbn, 25 tbc
[mp3 @ 0x1e3f1e0] Estimating duration from bitrate, this may be inaccurate
Input #1, mp3, from 'bulgaria.mp3':
  Metadata:
    encoder         : LAME 64bits version 3.99.5 ([http://lame.sf.net](http://lame.sf.net))
    TLEN            : 288810
  Duration: 00:04:48.87, start: 0.000000, bitrate: 320 kb/s
    Stream #1:0: Audio: mp3, 44100 Hz, stereo, s16p, 320 kb/s
No pixel format specified, yuv444p for H.264 encoding chosen.
Use -pix_fmt yuv420p for compatibility with outdated media players.
[libx264 @ 0x1e41ac0] using SAR=12/17
[libx264 @ 0x1e41ac0] using cpu capabilities: MMX2 SSE2Slow SlowCTZ
[libx264 @ 0x1e41ac0] profile High 4:4:4 Predictive, level 3.1, 4:4:4 8-bit
[libx264 @ 0x1e41ac0] 264 - core 138 r2 9e941d1 - H.264/MPEG-4 AVC codec - Copyleft 2003-2013 - [http://www.videolan.org/x264.html](http://www.videolan.org/x264.html) - options: cabac=1 ref=1 deblock=1:0:0 analyse=0x3:0x113 me=hex subme=2 psy=0 mixed_ref=0 me_range=16 chroma_me=1 trellis=0 8x8dct=1 cqm=0 deadzone=21,11 fast_pskip=0 chroma_qp_offset=0 threads=1 lookahead_threads=1 sliced_threads=0 nr=0 decimate=1 interlaced=0 bluray_compat=0 constrained_intra=0 bframes=0 weightp=1 keyint=7 keyint_min=1 scenecut=40 intra_refresh=0 rc=cqp mbtree=0 qp=0
Output #0, matroska, to 'output24.mkv':
  Metadata:
    encoder         : Lavf55.14.102
    Stream #0:0: Video: h264 (libx264) (H264 / 0x34363248), yuv444p, 1280x720 [SAR 12:17 DAR 64:51], q=-1--1, 1k tbn, 2 tbc
    Stream #0:1: Audio: aac (libfdk_aac) ([255][0][0][0] / 0x00FF), 44100 Hz, stereo, s16, 192 kb/s
Stream mapping:
  Stream #0:0 -> #0:0 (png -> libx264)
  Stream #1:0 -> #0:1 (mp3 -> libfdk_aac)
 Press [q] to stop, [?] for help

.....................

real    5m32.539s
user    4m24.580s
sys    0m12.064s
 




SO FINAL OFFER!



> time ffmpeg -y -loop 1 -r 2 -i IMAGE.png -i SOUNDFILE.mp3 -c:a libfdk_aac -b:a 192k -c:v libx264 -g 7 -crf 0 -vf scale=-1:720  -preset veryfast -shortest VIDEO.mkv

---

### Post by Yellow Pasque on 2013-08-31
'-g 0' turns off motion estimation (from ffmpeg manpage):
```
If your computer is not fast enough, you can speed up the compression at the expense of the compression ratio.
           You can use '-me zero' to speed up motion estimation, and '-g 0' to disable motion estimation completely (you
           have only I-frames, which means it is about as good as JPEG compression).
```

---

