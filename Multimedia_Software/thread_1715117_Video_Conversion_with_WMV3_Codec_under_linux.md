---
title: "Video Conversion with WMV3 Codec under linux?"
date: 2011-03-26
forum: Multimedia Software
---

### Post by nzso on 2011-03-26
I have a Sony Walkman NWZ-E354 and am having problems finding a suitable method on converting videos to a playable format for this device. I was able to convert videos of any type under windows to WMV for playback on it but after switching over to Linux I have had little luck finding a converter that will allow me to convert videos using the WMV3 Codec. 

I have tested WinFF, Transmageddon, Avidemux, VLC, Pitivi (Can't get Pitivi to launch) and done some searching through goggle and have been left with the impression that it is just not possible through Linux. I have even tried running a few Windows converters through Wine with no luck.

Is it possible to convert videos under Linux using the WMV3 codec for the video stream? Any tips or suggestions would be greatly appreciated.

---

### Post by nzso on 2011-03-27
Bump...

---

### Post by SeijiSensei on 2011-03-27
The only video codec I see listed on Sony's page for that device is "Format : WMV (DRM)".  If it really only accepts videos with DRM controls, it's likely to be pretty useless in Linux.  I'm a bit surprised it doesn't list the MP4 container, which is one of Sony's favorites.  

Having looked around a bit more, I'd say you've chosen an especially proprietary device that won't play well with Linux.

---

### Post by howefield on 2011-03-27
I'm not 100% sure but believe Handbrake will do it.

---

### Post by SeijiSensei on 2011-03-27
> **howefield said:**
> I'm not 100% sure but believe Handbrake will do it.

I have Handbrake from the [PPA John Stebbins maintains]("https://launchpad.net/~stebbins/+archive/handbrake-snapshots") that provides daily updates.  I only see the MP4 and MKV containers as options.

---

### Post by nzso on 2011-03-27
I should of hung on to my PSP for portable video. I really hate the idea of setting up a dual boot just so I can convert compatible videos.

---

### Post by FakeOutdoorsman on 2011-03-27
Perhaps one of the other WMV versions will work for you:
```

$ ffmpeg -codecs 2>&1 | egrep "wmv|wma"
 D..... = Decoding supported
 .E.... = Encoding supported
 ..V... = Video codec
 ..A... = Audio codec

 D A    wmapro          Windows Media Audio 9 Professional
 DEA    wmav1           Windows Media Audio 1
 DEA    wmav2           Windows Media Audio 2
 D A    wmavoice        Windows Media Audio Voice
 DEVSD  wmv1            Windows Media Video 7
 DEVSD  wmv2            Windows Media Video 8
 D V D  wmv3            Windows Media Video 9
 D V D  wmv3_vdpau      Windows Media Video 9 VDPAU
```
Example command using FFmpeg:
```
ffmpeg -i input -vcodec wmv2 -acodec wmav2 -qscale 3 -ab 128k -s 320x240 output.wmv
```

---

