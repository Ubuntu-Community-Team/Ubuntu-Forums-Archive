---
title: "convert image sequence to .mov? how to?"
date: 2010-11-08
forum: Multimedia Software
---

### Post by Unewbeginner on 2010-11-08
Hey everyone, my work need to convert image sequences(picture.0001.jpg, picture.0002.jpg......picture.0100.jpg) to .mov files. Anyone know how to do this? Thanks!!

---

### Post by Unewbeginner on 2010-11-09
help!! I really need to achieve this...:(

---

### Post by SeijiSensei on 2010-11-09
[Apparently ffmpeg can do this]("http://electron.mit.edu/~gsteele/ffmpeg/") though I've not tried using it.

---

### Post by FakeOutdoorsman on 2010-11-09
See the FFmpeg FAQ: [How do I encode single pictures into movies?](http://www.ffmpeg.org/faq.html#SEC14)

Note that FFmpeg will give your input images a default frame rate of 25 unless you change it with the *-r* option, as in:
```
ffmpeg -r 60 -i input ...
```

You may need to enable some additional encoders in FFmpeg depending on what output format you would like:
[url=http://ubuntuforums.org/showthread.php?t=1117283]
HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoders in FFmpeg[/url]

Also see the [FFmpeg x264 encoding guide](http://rob.opendot.cl/index.php/useful-stuff/ffmpeg-x264-encoding-guide/) if you are interested in encoding to H.264.

---

