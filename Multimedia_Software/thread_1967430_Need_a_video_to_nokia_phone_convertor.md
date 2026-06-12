---
title: "Need a video to nokia phone convertor"
date: 2012-04-28
forum: Multimedia Software
---

### Post by soumoks on 2012-04-28
Hey guys am new to ubuntu,installed 12.04 just yesterday and i absolutely love it,i was wondering if there was a video to nokia phone convertor  such as [http://www.dvdvideosoft.com/free-dvd-video-software.htm](http://www.dvdvideosoft.com/free-dvd-video-software.htm) or any convertor which allows me to set my own presets such as screen resolution e.t.c,thanks in advance..
btw i am using nokia 5233.

---

### Post by ron999 on 2012-04-28
> **soumoks said:**
> ... or any convertor which allows me to set my own presets such as screen resolution e.t.c
Hi
Think about using **WinFF** ---> [http://winff.org/html_new/]("http://winff.org/html_new/")
It's a gui for FFmpeg, so you can make your own presets ---> [http://code.google.com/p/winff/wiki/HowToMakePresets]("http://code.google.com/p/winff/wiki/HowToMakePresets")
Install it from software centre or use PPA for latest version ---> [http://code.google.com/p/winff/wiki/UbuntuInstallation]("http://code.google.com/p/winff/wiki/UbuntuInstallation")

---

### Post by soumoks on 2012-04-29
> **ron999 said:**
> Hi
Think about using **WinFF** ---> [http://winff.org/html_new/](http://winff.org/html_new/)
It's a gui for FFmpeg, so you can make your own presets ---> [htt.com/p/winff/wiki/HowToMakePresets]("http://code.google.com/p/winff/wiki/HowToMakePresets")
Install it from software centre or use PPA for latest version ---> [http://code.google.com/p/winff/wiki/UbuntuInstallation](http://code.google.com/p/winff/wiki/UbuntuInstallation)i am very much thankful for ur help,but it opens up terminal and this is what happens      Seems stream 0 codec frame rate differs from container frame rate: 23.98 (65535/2733) -> 23.98 (2997003/125000)
Input #0, avi, from '/media/46006A9B006A922B/how i met ur mother/season 7/How.I.Met.Your.Mother.S07E04.HDTV.XviD-LOL.[VTV].avi':
  Metadata:
    encoder         : transcode-1.0.6
  Duration: 00:21:09.00, start: 0.000000, bitrate: 1156 kb/s
    Stream #0.0: Video: mpeg4 (Advanced Simple Profile), yuv420p, 624x352 [PAR 1:1 DAR 39:22], 23.98 tbr, 23.98 tbn, 23.98 tbc
    Stream #0.1: Audio: mp3, 48000 Hz, stereo, s16, 128 kb/s
Unable to find a suitable output format for 'ffmpeg'
Press Enter to Continue


what do i abt it?thanks again..:)

---

### Post by soumoks on 2012-04-29
> **soumoks said:**
> i am very much thankful for ur help,but it opens up terminal and this is what happens      Seems stream 0 codec frame rate differs from container frame rate: 23.98 (65535/2733) -> 23.98 (2997003/125000)
Input #0, avi, from '/media/46006A9B006A922B/how i met ur mother/season 7/How.I.Met.Your.Mother.S07E04.HDTV.XviD-LOL.[VTV].avi':
  Metadata:
    encoder         : transcode-1.0.6
  Duration: 00:21:09.00, start: 0.000000, bitrate: 1156 kb/s
    Stream #0.0: Video: mpeg4 (Advanced Simple Profile), yuv420p, 624x352 [PAR 1:1 DAR 39:22], 23.98 tbr, 23.98 tbn, 23.98 tbc
    Stream #0.1: Audio: mp3, 48000 Hz, stereo, s16, 128 kb/s
Unable to find a suitable output format for 'ffmpeg'
Press Enter to Continue


what do i abt it?thanks again..:)
by the way i used this command line parameter in winff   ffmpeg -i input.avi -f mp4 -vcodec mpeg4 -b 2200k -r 30 -s 640x360 -acodec libfaac -ar 32000 -ab 128k -ac 2 -threads 8 output.mp4,i found this in some thread in this forum only..

---

### Post by ron999 on 2012-04-29
> **soumoks said:**
> 
what do i abt it?
Hi
If you want to make a preset for the Nokia 5233...
_**Read this again**_ ---> [http://code.google.com/p/winff/wiki/HowToMakePresets]("http://code.google.com/p/winff/wiki/HowToMakePresets")

And try these settings...


Preset Name
```
Nokia5233
```

Preset Label
```
Nokia 5233
```

Preset Command Line Parameters
```
-vf "scale=640:trunc(ow/a/2)*2" -c:v mpeg4 -b:v 1200k -c:a aac -strict experimental -b:a 192k -ar 44100 -ac 2
```

Output File Extension
```
mp4
```

Category
```
Nokia
```

PS
Information is from here ---> [http://www.facebook.com/note.php?note_id=138333152898066]("http://www.facebook.com/note.php?note_id=138333152898066")

---

### Post by soumoks on 2012-05-02
> **ron999 said:**
> Hi
If you want to make a preset for the Nokia 5233...
_**Read this again**_ ---> [http://code.google.com/p/winff/wiki/HowToMakePresets](http://code.google.com/p/winff/wiki/HowToMakePresets)

And try these settings...


Preset Name
```
Nokia5233
```Preset Label
```
Nokia 5233
```Preset Command Line Parameters
```
-vf "scale=640:trunc(ow/a/2)*2" -c:v mpeg4 -b:v 1200k -c:a aac -strict experimental -b:a 192k -ar 44100 -ac 2
```Output File Extension
```
mp4
```Category
```
Nokia
```PS
Information is from here ---> [http://www.facebook.com/note.php?note_id=138333152898066](http://www.facebook.com/note.php?note_id=138333152898066)hey bro,i tried the above config and i got the foll in my terminal ffmpeg version 0.8.1-4:0.8.1-0ubuntu1, Copyright (c) 2000-2011 the Libav developers
  built on Mar 22 2012 05:29:10 with gcc 4.6.3
This program is not developed anymore and is only provided for compatibility. Use avconv instead (see Changelog for the list of incompatible changes).
[matroska,webm @ 0x8a33240] Estimating duration from bitrate, this may be inaccurate
Input #0, matroska,webm, from '/media/46006A9B006A922B/how i met ur mother/season 4/Episode 04 - Intervention.mkv':
  Duration: 00:21:08.95, start: 0.000000, bitrate: N/A
    Stream #0.0: Video: h264 (High), yuv420p, 624x352, PAR 1:1 DAR 39:22, 23.98 fps, 23.98 tbr, 1k tbn, 47.95 tbc (default)
    Stream #0.1(dut): Audio: aac, 48000 Hz, stereo, s16 (default)
Unable to find a suitable output format for 'vf'
Press Enter to Continue


what to do?

---

### Post by The Rnegade on 2012-05-02
> **soumoks said:**
> Hey guys am new to ubuntu,installed 12.04 just yesterday and i absolutely love it,i was wondering if there was a video to nokia phone convertor  such as [http://www.dvdvideosoft.com/free-dvd-video-software.htm](http://www.dvdvideosoft.com/free-dvd-video-software.htm) or any convertor which allows me to set my own presets such as screen resolution e.t.c,thanks in advance..
btw i am using nokia 5233.

transmaggedon and ogg rip

---

