---
title: "Video Encoding help"
date: 2010-02-16
forum: Multimedia Software
---

### Post by mooman001 on 2010-02-16
Alright, I bought this Gigaware 42-422 Video player...

I been using Windows 7 and made the switch to Ubuntu due to I generally like it better. Well, the problem is.. Windows 7 would auto-convert the videos I uploaded onto this. Now I'm having the problem of figuring out what video codex I'm supposed to be using... I know the video is WMV but every time I tried re-encoding a AVI I get a message saying it's unsupported... I would love if someone can help me out here...

Here's a file format it can support

Video:
   Dimensions: 320 x 240
   Codec: Microsoft Windows Media 9
   Frame Rate: 24 frames per second

Audio:
   Codec: WMA Version 8
   Channels: Stereo
   Sample Rate: 22050 Hz

---

### Post by FakeOutdoorsman on 2010-02-16
Some devices are very picky about the videos they will accept.  Do you have any videos that acutally play on this device?  These videos can be inspected to see what they're made of and then you can try to replicate these settings.  Install FFmpeg, and then run this command:
```
ffmpeg -i name_of_the_video_that_plays_on_your_device.wmv
```
Even better would be to install [mediainfo](http://mediainfo.sourceforge.net/en/Download) and also see what it says about one of the working videos:
```
mediainfo name_of_the_video_that_plays_on_your_device.wmv
```
With this information I can try to give you a couple of encoding commands to try out.

---

### Post by mooman001 on 2010-02-16
Don't know if you need all of this but here you go...

```
Complete name                    : /home/stephen/Desktop/funny office.wmv
Format                           : Windows Media
File size                        : 4.16 MiB
Duration                         : 1mn 26s
Overall bit rate mode            : Constant
Overall bit rate                 : 404 Kbps
Maximum Overall bit rate         : 542 Kbps
Encoded date                     : UTC 2010-01-20 21:00:05.918

Video
ID                               : 1
Format                           : VC-1
Format profile                   : MP@LL
Codec ID                         : WMV3
Codec ID/Info                    : Windows Media Video 9
Codec ID/Hint                    : WMV3
Description of the codec         : Windows Media Video 9
Bit rate mode                    : Constant
Bit rate                         : 512 Kbps
Width                            : 320 pixels
Height                           : 240 pixels
Display aspect ratio             : 4:3
Frame rate mode                  : Variable
Nominal frame rate               : 23.976 fps
Resolution                       : 8 bits
Scan type                        : Progressive
Language                         : English (US)

Audio
ID                               : 2
Format                           : WMA
Format version                   : Version 2
Codec ID                         : 161
Codec ID/Info                    : Windows Media Audio
Description of the codec         : Windows Media Audio 9.2 -  22 kbps, 22 kHz, stereo 1-pass CBR
Duration                         : 1mn 26s
Bit rate mode                    : Constant
Bit rate                         : 22.0 Kbps
Channel(s)                       : 2 channels
Sampling rate                    : 22.05 KHz
Resolution                       : 16 bits
Stream size                      : 232 KiB (5%)
Language                         : English (US)

```

This is a video that works on it...

---

### Post by VertexPusher on 2010-02-16
I don't think there's a way to encode WMV3 in Linux.

Sell the Gigaware player and get one that supports MPEG formats (DivX, Xvid, DivX Plus, H.264, MP4).

---

### Post by mooman001 on 2010-02-16
That's not what I wanted to hear... Thanks for the reply though. I'll wait and see if the other guy responds...

---

