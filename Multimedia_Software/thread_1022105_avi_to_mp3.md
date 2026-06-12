---
title: "avi to mp3"
date: 2008-12-26
forum: Multimedia Software
---

### Post by martin saint martin on 2008-12-26
is there a program that i could use to extract the audio from an avi file and have it become a mp3 file?

---

### Post by xc3RnbFO8P on 2008-12-26
You can use Avidemux in Add/Remove (all available application)
Open the file with Avidemux,
on the left Audio, choose codec,
on the top bar choose Audio> save .

---

### Post by Hello_World on 2008-12-27
You can also use the below linked solution. It works, btw, for many other audio/video files to convert to mp3. Using a right click on the file, it's so easy, you won't believe it. But it works great!

[http://www.atokar.net/index.php/topic,239.msg472/topicseen.html#msg472](http://www.atokar.net/index.php/topic,239.msg472/topicseen.html#msg472)

P.S.: There is also a German version of the How-To on the very same site ;)

---

### Post by sekinto on 2008-12-27
VLC or Avidemux would work.

---

### Post by martin saint martin on 2008-12-27
Avidemux does the trick, but now i'm wondering how to set up different tracks, instead of one long track.  i'm thinking Audacity can help me do this.

---

### Post by FakeOutdoorsman on 2008-12-28
ffmpeg can do this (assuming Ubuntu 8.10).  First install ffmpeg and the unstripped libraries:
```
sudo apt-get install ffmpeg libavcodec-unstripped-51 libavformat-unstripped-52
```
To use ffmpeg:
```
ffmpeg -i input.avi output.mp3
```
If you like a GUI, then try [WinFF](http://code.google.com/p/winff/wiki/UbuntuInstallation).

---

### Post by MartyBuntu on 2008-12-28
> **FakeOutdoorsman said:**
> 
If you like a GUI, then try [WinFF](http://code.google.com/p/winff/wiki/UbuntuInstallation).
I agree. Then use Audacity to split up the big .mp3 file.

A shame mp3splt-gtk isn't in the repositories.

---

