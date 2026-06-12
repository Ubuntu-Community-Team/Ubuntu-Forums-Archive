---
title: "Unable to play WMV file"
date: 2010-02-23
forum: Multimedia Software
---

### Post by DoomDahDoomDoom on 2010-02-23
Hi,
I read through the thread started by wannabetechie hoping that it was a similar problem, but doesn't look like it.  I'm trying to view/edit some WMVs that were created using Forza 3 on the XBOX 360.

For a smallish sample (12 MB):

[http://www.forzamotorsport.net/UGCImageHandler.ashx?id=6908749&type=download](http://www.forzamotorsport.net/UGCImageHandler.ashx?id=6908749&type=download)

The file will be available for download for 24 hours.


I'm running the latest Ubuntu Studio on a new-ish computer.  4GB of RAM, Dual Core with an NVidia card.

When I tried to open the file above initially, Gstreamer ("Movie Player") complained that I needed to install a codec, which I "OK"ed.  But the movie still wouldn't play.  In fact the Movie player just closed (crashed?).

I tried installing VLC Media player.  Same story.  Try to load the WMV and POOF!, VLC closes (crashes?)

I tried to right click on the file and view it's properties... POOF! my explorer window closes.

Obviously Ubuntu doesn't like this file.  I've tried rebooting a couple of times, just in case...

I'm hoping that with a sample file to work with some expert Linux user can tell me what I'm missing...

Thanks in advance!

---

### Post by DoomDahDoomDoom on 2010-02-23
Apparently I can't share the file via that link... possibly I could email it if somebody is feeling particularly helpful :)

Anyway, I should also note that it's a 720p (HD) quality video.

---

### Post by d3v1150m471c on 2010-02-23
Can you launch it with vlc? VLC plays most things but it won't help you edit them. For editing try avidemux and/or mencoder.

---

### Post by the yawner on 2010-02-23
Have you installed restricted extras yet? It includes among many other stuff support for wmv playback.

---

### Post by DoomDahDoomDoom on 2010-02-23
d3v - as I mentioned, VLC closes immediately when I try to play it.

yawner - yeah I think that's what was installed when I tried to play it initially.


I have tried to open it with Cinelerra and it doesn't recognize it - it treats it as a RAW audio file?


The movie plays in WinXP on Windows Media Player...

---

### Post by mc4man on 2010-02-23
Maybe upload your file to somewhere like here and post a link - 
[http://www.mediafire.com/](http://www.mediafire.com/)

I find it's pretty easy to use (have an account, never tried the no account way

---

### Post by Voorhees1979 on 2010-02-23
I had the exact same problem. You can't play them with any player on linux at all. You just get errors. BUT the newest VLC will play it fine and the newest avidemux will convert the file as well. These are the exact specs of the Forza 3 video codecs:

```
General
Count                            : 254
Count of stream of this kind     : 1
Kind of stream                   : General
Kind of stream                   : General
Stream identifier                : 0
Count of video streams           : 1
Count of audio streams           : 1
Video_Format_List                : VC-1
Video_Format_WithHint_List       : VC-1 (Microsoft)
Codecs Video                     : VC-1
Video_Language_List              : en-us
Audio_Format_List                : WMA2
Audio_Format_WithHint_List       : WMA2
Audio codecs                     : WMA2
Audio_Language_List              : en-us
Complete name                    : Forza3.wmv
File name                        : Forza3.wmv
File extension                   : wmv
Format                           : Windows Media
Format                           : Windows Media
Format/Extensions usually used   : asf wmv wma
Codec                            : Windows Media
Codec                            : Windows Media
Codec/Extensions usually used    : asf wmv wma
File size                        : 48427221
File size                        : 46.2 MiB
File size                        : 46 MiB
File size                        : 46 MiB
File size                        : 46.2 MiB
File size                        : 46.18 MiB
Duration                         : 25002
Duration                         : 25s 2ms
Duration                         : 25s 2ms
Duration                         : 25s 2ms
Duration                         : 00:00:25.002
Overall bit rate                 : 15495471
Overall bit rate                 : 15.5 Mbps
Maximum Overall bit rate         : 15885843
Maximum Overall bit rate         : 15.9 Mbps
HeaderSize                       : 2775
DataSize                         : 29993
Title                            : Ford Focus '09 on Full Circuit
Title/More                       : driven by O.Jones
Movie name                       : Ford Focus '09 on Full Circuit
Movie name/More                  : driven by O.Jones
Performer                        : Jimbo1979
Encoded date                     : UTC 2009-11-11 20:25:19.716
Comment                          : Forza Motorsport 3 Video
WM/Category                      : Forza;Forza Motorsport 3;Jimbo1979;Sedona Raceway Park;Full Circuit;O.Jones;Ford;Ford Focus '09
WM/PromotionURL                  : [http://forzamotorsport.net](http://forzamotorsport.net)
Forza/EnvironmentId              : 1
Forza/TrackId                    : 140
Forza/TrackConfig                : 0
Forza/FocusCarMakeId             : 14
Forza/FocusCarModelId            : 1,086
MediaFoundationVersion           : 1.112

Video
Count                            : 146
Count of stream of this kind     : 1
Kind of stream                   : Video
Kind of stream                   : Video
Stream identifier                : 0
ID                               : 2
ID                               : 2
Format                           : VC-1
Format profile                   : AP@L2
Codec ID                         : WVC1
Codec ID/Hint                    : Microsoft
Codec                            : VC-1
Codec                            : VC-1
Codec/Family                     : VC-1
Codec/Url                        : [http://www.microsoft.com/windows/windowsmedia/format/codecdownload.aspx](http://www.microsoft.com/windows/windowsmedia/format/codecdownload.aspx)
Codec/CC                         : WVC1
Codec profile                    : AP@L2
Duration                         : 25000
Duration                         : 25s 0ms
Duration                         : 25s 0ms
Duration                         : 25s 0ms
Duration                         : 00:00:25.000
Bit rate                         : 15728640
Bit rate                         : 15.7 Mbps
Width                            : 1280
Width                            : 1 280 pixels
Height                           : 720
Height                           : 720 pixels
Pixel aspect ratio               : 1.000
Display aspect ratio             : 1.778
Display aspect ratio             : 16/9
Frame rate                       : 30.000
Frame rate                       : 30.000 fps
Frame count                      : 750
Colorimetry                      : 4:2:0
Scan type                        : Progressive
Scan type                        : Progressive
Interlacement                    : PPF
Interlacement                    : Progressive
Bits/(Pixel*Frame)               : 0.569
Language                         : en-us
Language                         : en-us
AspectRatioX                     : 1
AspectRatioY                     : 1

Audio
Count                            : 121
Count of stream of this kind     : 1
Kind of stream                   : Audio
Kind of stream                   : Audio
Stream identifier                : 0
ID                               : 1
ID                               : 1
Format                           : WMA2
Codec ID                         : 161
Codec ID/Info                    : Windows Media Audio 2
Codec ID/Url                     : [http://www.microsoft.com/windows/windowsmedia/format/codecdownload.aspx](http://www.microsoft.com/windows/windowsmedia/format/codecdownload.aspx)
Codec                            : 161
Codec                            : WMA2
Codec/Info                       : Windows Media Audio 2
Codec/Url                        : [http://www.microsoft.com/windows/windowsmedia/format/codecdownload.aspx](http://www.microsoft.com/windows/windowsmedia/format/codecdownload.aspx)
Codec/CC                         : 161
Duration                         : 25002
Duration                         : 25s 2ms
Duration                         : 25s 2ms
Duration                         : 25s 2ms
Duration                         : 00:00:25.002
Bit rate                         : 128064
Bit rate                         : 128 Kbps
Channel(s)                       : 2
Channel(s)                       : 2 channels
Sampling rate                    : 48000
Sampling rate                    : 48.0 KHz
SamplingCount                    : 1200096
Resolution                       : 16
Resolution                       : 16 bits
Language                         : en-us
Language                         : en-us
```

[IMG]http://mepislovers.org/forums/image.php?u=9213&type=sigpic&dateline=1258561489[/IMG]

---

### Post by DoomDahDoomDoom on 2010-02-23
mc4man - I would, but at work here that site is "Access Denied"

voorhees79 - Do you mean VLC in Windows?  I installed VLC on Ubuntu and it just crashes the same as Movie Player.  Maybe when I get home I'll look up avidemux and see if I can convert these videos to a usable format?  Is that the best way?

---

### Post by DoomDahDoomDoom on 2010-02-27
Finally got around to trying the avidemux idea.

Unfortunately, it also crashes, but at least gives some info:

Crash

Segfault
 at line 0, file ??/usr/lib/libADM_core.so(ADM_backTrack+0x6d) [0x14192d]
/usr/lib/libADM_core.so(_Z20sig_segfault_handleri+0x46) [0x141db6]
[0xfa1400]
/usr/lib/libADM5avcodec.so.52 [0x9afa83]



And as suggested I've posted the file here as well:
[http://www.mediafire.com/?ch0dz0nyvyz](http://www.mediafire.com/?ch0dz0nyvyz)

---

### Post by mc4man on 2010-02-27
This is the only way I can play (the issue is something with the audio that ffmpeg (avcodec) doesn't like

```
mplayer -ac wmadmo /home/doug/Download/Forza2.wmv 
```

> doug@doug-desktop:~$ mplayer -ac wmadmo /home/doug/Download/Forza2.wmv 
MPlayer SVN-r30230-4.3.4 (C) 2000-2009 MPlayer Team
mplayer: could not connect to socket
mplayer: No such file or directory
Failed to open LIRC support. You will not be able to use your remote control.

Playing /home/doug/Download/Forza2.wmv.
ASF file format detected.
[asfheader] Audio stream found, -aid 1
[asfheader] Video stream found, -vid 2
VIDEO:  [WVC1]  1280x720  0bpp  1000.000 fps  15728.6 kbps (1920.0 kbyte/s)
Clip info:
 title: Audi RS 4 on Short Circuit
 author: DoomDahDoomD00M
 comments: Forza Motorsport 3 Video
==========================================================================
Trying to force video codec driver family ffmpeg...
Opening video decoder: [ffmpeg] FFmpeg's libavcodec codec family
Selected video codec: [ffvc1] vfm: ffmpeg (FFmpeg WVC1)
==========================================================================
==========================================================================
Forced audio codec: wmadmo
Opening audio decoder: [dmo] Win32/DMO decoders
AUDIO: 48000 Hz, 2 ch, s16le, 128.1 kbit/8.34% (ratio: 16008->192000)
Selected audio codec: [wmadmo] afm: dmo (Windows Media Audio DMO)
==========================================================================
AO: [alsa] 48000Hz 2ch s16le (2 bytes per sample)
Starting playback...
Movie-Aspect is 1.78:1 - prescaling to correct movie aspect.
VO: [xv] 1280x720 => 1280x720 Planar YV12 
A:   7.9 V:   7.9 A-V: -0.074 ct: -0.045 149/149 75%  3%  2.0% 5 0 

Exiting... (End of file)

---

### Post by andrew.46 on 2010-02-27
Based on mc4man's find that mplayer can play this file it is a relatively easy matter to *repair* the file. There will no doubt be a several different ways to do this but I first extracted the audio with MPlayer:

```

mplayer Forza2.wmv -ac wmadmo \
        -vc null -vo null \
        -ao pcm:fast:waveheader:file=audio.wav

```

and then remuxed the file, copying the video and then *adding in* and converting the audio:

```

ffmpeg -i Forza2.wmv -vcodec copy \
       -i audio.wav -acodec wmav2 -ab 128k \
       -map_meta_data 0:0 Forza2_repaired.wmv

```

This file plays perfectly with MPlayer using ffwmav2 and vlc had no trouble as well, the copying of the meta data is a bonus! I have placed [the repaired file here]("http://www.andrews-corner.org/samples/Forza2_repaired.wmv") if anyone is interested in looking at it.

All the best,

Andrew

---

