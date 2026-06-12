---
title: "How to update ffmpeg"
date: 2016-08-22
forum: Multimedia Software
---

### Post by ahmed.elrmady on 2016-08-22
hey guys, 
i 'm having a few problems and i'd appreciate if someone helps O:)

1. currently im using ffmpeg version 2.8.6-1ubuntu2 and want to upgrade it to 3.1.2 

Note : i used this guide to install it in the first place [https://trac.ffmpeg.org/wiki/CompilationGuide/Ubuntu](https://trac.ffmpeg.org/wiki/CompilationGuide/Ubuntu) 

2. i downloaded some tutorials and documentations to use ffmpeg and finally i get it to record,but here is the problem 
         :???:
   
         there is alot of codes and variables and i get lost sometimes, so lets say i want to upload a video to youtube what code should i use to record my screen and my voice and to get this as a result :

Container: MP4
Audio codec: AAC-LC
     
[LIST]
[*]Channels: Stereo or Stereo + 5.1 
[*]Sample rate 96khz or 48khz 
[/LIST]
   
Video codec: H.264
     
[LIST]
[*]Progressive scan (no interlacing) 
[*]High Profile 
[*]2 consecutive B frames 
[*]Closed GOP. GOP of half the frame rate. 
[*]CABAC 
[*]Variable bitrate. No bitrate limit required, though we offer recommended bit rates below for reference 
[*]Chroma subsampling: 4:2:0 
[/LIST]
   
Bitrate 
[h=4]Recommended video bitrates for uploads[/h]      [TABLE="class: nice-table"]
                [TR]
           [TH]Type[/TH]
           [TH]Video Bitrate, Standard Frame Rate
          (24, 25, 30)[/TH]
           [TH]Video Bitrate, High Frame Rate
          (48, 50, 60)[/TH]
         [/TR]
         [TR]
           [TD]2160p (4k)[/TD]
           [TD]35-45 Mbps[/TD]
           [TD]53-68 Mbps[/TD]
         [/TR]
         [TR]
           [TD]1440p (2k)[/TD]
           [TD]16 Mbps[/TD]
           [TD]24 Mbps[/TD]
         [/TR]
         [TR]
           [TD]1080p[/TD]
           [TD]8 Mbps[/TD]
           [TD]12 Mbps[/TD]
         [/TR]
         [TR]
           [TD]720p[/TD]
           [TD]5 Mbps[/TD]
           [TD]7.5 Mbps[/TD]
         [/TR]
         [TR]
           [TD]480p[/TD]
           [TD]2.5 Mbps[/TD]
           [TD]4 Mbps[/TD]
         [/TR]
         [TR]
           [TD]360p[/TD]
           [TD]1 Mbps[/TD]
           [TD]1.5 Mbps[/TD]
         [/TR]
            [/TABLE]
      [h=4]Recommended audio bitrates for uploads[/h]                      [TABLE="class: nice-table"]
[TR]
           [TH]Type[/TH]
           [TH]Audio Bitrate[/TH]
         [/TR]
         [TR]
           [TD]Mono[/TD]
           [TD]128 kbps[/TD]
         [/TR]
         [TR]
           [TD]Stereo[/TD]
           [TD]384 kbps[/TD]
         [/TR]
         [TR]
           [TD]5.1[/TD]
           [TD]512 kbps[/TD]
[/TR]
[/TABLE]
                                           

     
Note: those are the Recommended upload encoding settings for youtube 
and thnx in advance O:)

---

### Post by mc4man on 2016-08-23
Why don't you go back to the guide you followed & read the bottom of the page, "Updating FFmpeg"

---

### Post by ahmed.elrmady on 2016-08-23
> **mc4man said:**
> Why don't you go back to the guide you followed & read the bottom of the page, "Updating FFmpeg"

i did but i only installed it like 8 days ago, so why i didn't get the latest update at the first time ?!!

---

### Post by mc4man on 2016-08-23
> **ahmed.elrmady said:**
> i did but i only installed it like 8 days ago, so why i didn't get the latest update at the first time ?!!
The git master updates many times per day, that guide is using a daily snapshot so you should be on 3.0.git
Check the Release file in your ffmpeg source folder.
ffmpeg version 2.8.6-1ubuntu2 is what is in the ubuntu repos, not what you supposedly built

---

### Post by ahmed.elrmady on 2016-08-23
ya u r right i checked the release file and it's 3.0.git like u said 
thnx :) 

and now i'm done with update part ,do u have any ideas about the code i should use !!

---

### Post by FakeOutdoorsman on 2016-08-24
> do u have any ideas about the code i should use !!
See documentation about x11grab and pulse:
[https://ffmpeg.org/ffmpeg-devices.html#x11grab](https://ffmpeg.org/ffmpeg-devices.html#x11grab)
[https://ffmpeg.org/ffmpeg-devices.html#pulse](https://ffmpeg.org/ffmpeg-devices.html#pulse)

Then read the FFmpeg Wiki:
[https://trac.ffmpeg.org/wiki/Encode/YouTube](https://trac.ffmpeg.org/wiki/Encode/YouTube)

Also this (especially the pavucontrol section):
[https://ubuntuforums.org/showthread.php?t=1392026&p=8746719&viewfull=1#post8746719](https://ubuntuforums.org/showthread.php?t=1392026&p=8746719&viewfull=1#post8746719)

Your final command may look like:
```
ffmpeg -f x11grab -framerate 50 -video_size 1280x720 -i :0.0+100,250 -f pulse -i default -c:v libx264 -crf 18 -c:a libfdk_aac -vbr 5 output.mkv
```

---

