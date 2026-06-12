---
title: "FFmpeg don't know ''libfaac'', Help?"
date: 2011-06-20
forum: Multimedia Software
---

### Post by xcommunistx on 2011-06-20
Since i installed ''libavformat-extra-5two (cant write the number)'' there is a Problem when i try to COnvert Videos using FFmpeg, i get this error:

```
 Seems stream 0 codec frame rate differs from container frame rate: 180000.00 (180000/1) -> 25.00 (25/1)
Input #0, mov,mp4,m4a,3gp,3g2,mj2, from 'KilezMore-Klimawandel.mp4':
  Metadata:
    major_brand     : mp42
    minor_version   : 0
    compatible_brands: mp42isomavc1
    encoder         : HandBrake 0.9.5 2011043000
  Duration: 00:05:20.00, start: 0.000000, bitrate: 647 kb/s
    Stream #0.0(und): Video: h264, yuv420p, 640x360, 484 kb/s, 25 fps, 25 tbr, 90k tbn, 180k tbc
    Stream #0.1(und): Audio: aac, 44100 Hz, stereo, s16, 158 kb/s
Unknown encoder 'libfaac'
 
```What does this mean? What do i have to do to get this fixed?

---

### Post by Yellow Pasque on 2011-06-20
It probably means you should install faac package.

---

### Post by xcommunistx on 2011-06-20
>  It probably means you should install faac package. 	  

I have already libfaac-dev and libfaac0 installed...

---

### Post by xcommunistx on 2011-06-20
I just re-installed FFmpeg and it worked...

---

### Post by FakeOutdoorsman on 2011-06-20
For anyone else experiencing this issue see *Option C* here:

[HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoders in FFmpeg](http://ubuntuforums.org/showthread.php?t=1117283)

---

### Post by xcommunistx on 2011-06-21
>  For anyone else experiencing this issue see *Option C* here:

[HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoders in FFmpeg]("http://ubuntuforums.org/showthread.php?t=1117283") 

That's what i have done before this Error...

---

