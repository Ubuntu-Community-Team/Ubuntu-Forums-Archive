---
title: "Inlcuding subtitle when converting MTS to MKV"
date: 2013-05-26
forum: Multimedia Software
---

### Post by mci on 2013-05-26
Hello,

I want to convert my .MTS videos from my Sony HD Cam into a  .MKV. I am using ffmpeg and it works fine. But I have problems with the  subtitles (in this case the subtitles are date and time) because they  get lost once I convert the MTS into mkv.

  I use this command:
  ```
 ffmpeg -i 00235.MTS -scodec copy -acodec copy -vcodec copy -f matroska OUTPUT.mkv 
```  

This is the output:
  
```

ffmpeg version 0.8.6-4:0.8.6-0ubuntu0.12.04.1, Copyright (c) 2000-2013 the Libav developers
  built on Apr  2 2013 17:02:36 with gcc 4.6.3
*** THIS PROGRAM IS DEPRECATED ***
This program is only provided for compatibility and will be removed in a future release. Please use avconv instead.
Input #0, mpegts, from '00235.MTS':
  Duration: 00:00:22.07, start: 1.000011, bitrate: 26285 kb/s
  Program 1 
    Stream #0.0[0x1011]: Video: h264 (High), yuv420p, 1920x1080 [PAR 1:1 DAR 16:9], 50 fps, 50 tbr, 90k tbn, 100 tbc
    Stream #0.1[0x1100]: Audio: ac3, 48000 Hz, 5.1, s16, 448 kb/s
    Stream #0.2[0x1200]: Data: [144][0][0][0] / 0x0090
Output #0, matroska, to 'OUTPUT.mkv':
  Metadata:
    encoder         : Lavf53.21.1
    Stream #0.0: Video: H264 / 0x34363248, yuv420p, 1920x1080 [PAR 1:1 DAR 16:9], q=2-31, 1k tbn, 50 tbc
    Stream #0.1: Audio: ac3, 48000 Hz, 5.1, 448 kb/s
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
Press ctrl-c to stop encoding
frame= 1104 fps=1068 q=-1.0 Lsize=   67284kB time=22.08 bitrate=24963.2kbits/s    
video:66061kB audio:1208kB global headers:0kB muxing overhead 0.023045%

```

  It looks like ```
Stream #0.2[0x1200]
``` is the subtitle but in the end its not put into the MKV.

  I hope someone can help me.

---

### Post by andrew.46 on 2013-05-26
You should be able to do this with the *-map* option, see the gory details here:

[http://ffmpeg.org/trac/ffmpeg/wiki/How%20to%20use%20-map%20option](http://ffmpeg.org/trac/ffmpeg/wiki/How%20to%20use%20-map%20option)

---

### Post by mci on 2013-05-27
Thanks for the hint. I changed the setting from [COLOR=#696969]*-scodec copy*[/COLOR] to [COLOR=#696969]*-dcodec copy*[/COLOR] since it is a data stream not a subtitle stream.

It seems that matroska can't handle DATA streams. It doesn't matter if I try:

```
ffmpeg -i 00235.MTS -map 0:0 -map 0:1 -map 0:2 **-dcodec** copy -acodec copy -vcodec copy OUTPUT.mkv
```

or

```
ffmpeg -i 00235.MTS **-dcodec** copy -acodec copy -vcodec copy -f matroska OUTPUT.mkv

```
I always get this output:

```
ffmpeg version 0.8.6-4:0.8.6-0ubuntu0.12.04.1, Copyright (c) 2000-2013 the Libav developers
  built on Apr  2 2013 17:02:36 with gcc 4.6.3
*** THIS PROGRAM IS DEPRECATED ***
This program is only provided for compatibility and will be removed in a future release. Please use avconv instead.
Input #0, mpegts, from '00235.MTS':
  Duration: 00:00:22.07, start: 1.000011, bitrate: 26285 kb/s
  Program 1 
    Stream #0.0[0x1011]: Video: h264 (High), yuv420p, 1920x1080 [PAR 1:1 DAR 16:9], 50 fps, 50 tbr, 90k tbn, 100 tbc
    Stream #0.1[0x1100]: Audio: ac3, 48000 Hz, 5.1, s16, 448 kb/s
    Stream #0.2[0x1200]: Data: [144][0][0][0] / 0x0090
[COLOR=#ff0000][matroska @ 0x2185520] Only audio, video, and subtitles are supported for Matroska.[/COLOR]
Output #0, matroska, to 'OUTPUT.mkv':
  Metadata:
    encoder         : Lavf53.21.1
    Stream #0.0: Video: H264 / 0x34363248, yuv420p, 1920x1080 [PAR 1:1 DAR 16:9], q=2-31, 1k tbn, 50 tbc
    Stream #0.1: Audio: ac3, 48000 Hz, 5.1, 448 kb/s
    Stream #0.2: Data: [144][0][0][0] / 0x0090
Stream mapping:
  Stream #0.0 -> #0.0
  Stream #0.1 -> #0.1
  Stream #0.2 -> #0.2
Press ctrl-c to stop encoding
frame= 1104 fps=  0 q=-1.0 Lsize=   67284kB time=22.08 bitrate=24963.2kbits/s    
video:66061kB audio:1208kB global headers:0kB muxing overhead 0.023083%
```

- Is it possible to convert the data stream into a subtitle stream?

- Why does the Ubuntu Totem Media Player display the data stream (I can choose it to be shown by selecting the subtitle 'Subtitle #1') when I open a .MTS file and other Media Players don't display it?

---

### Post by mci on 2013-05-27
Okay, I have the solution from: [http://askubuntu.com/questions/300298/inlcuding-subtitle-when-converting-mts-to-mkv](http://askubuntu.com/questions/300298/inlcuding-subtitle-when-converting-mts-to-mkv)

I updated ffmpeg to the newest version using this guide: [https://ffmpeg.org/trac/ffmpeg/wiki/UbuntuCompilationGuide](https://ffmpeg.org/trac/ffmpeg/wiki/UbuntuCompilationGuide)

This command worked fine:
```

ffmpeg -i 00235.MTS -map 0 -c:v copy -c:s copy -c:a copy OUTPUT.mkv
```

as did my old command after updating ffmpeg to the newest version (git-2013-05-27-1c711b6):

```
ffmpeg -i 00235.MTS -scodec copy -acodec copy -vcodec copy -f matroska OUTPUT.mkv
```

Thanks frostschutz and andrew.46

---

### Post by andrew.46 on 2013-05-27
I wonder if you can simplify all the copying by simply using:

```
-codec copy
```

instead of specifying each stream individually. I have not tested this to see if it picks up more than 2 streams...

---

### Post by FakeOutdoorsman on 2013-05-28
> **andrew.46 said:**
> I wonder if you can simplify all the copying by simply using:

```
-codec copy
```

instead of specifying each stream individually. I have not tested this to see if it picks up more than 2 streams...

Using "-codec copy" alone will copy one stream of each type, but will ignore additional streams of the same type. For example, if the input has a video stream and two audio streams, then the audio stream with the fewest channels will not get copied. Including "-map 0" with "-codec copy" will ensure that everything from the input gets copied. See the [stream selection](http://ffmpeg.org/ffmpeg.html#Stream-selection) docs for more info.

---

### Post by andrew.46 on 2013-05-29
Thanks for that  FakeOutdoorsman, if I learn a new thing every day I will eventually become a genius :)

---

### Post by FakeOutdoorsman on 2013-05-29
My problem is that I forgot two things when I learn something new.

---

