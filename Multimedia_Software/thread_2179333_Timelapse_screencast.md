---
title: "Timelapse screencast"
date: 2013-10-07
forum: Multimedia Software
---

### Post by Norrolith on 2013-10-07
I am wondering if there is any software for ubuntu that will allow me to make a timelapse of my screen.
or even just to take picture at regular intervals, I can stitch them together myself.

---

### Post by FakeOutdoorsman on 2013-10-08
You can use ffmpeg to output a video:
```
$ ffmpeg -y -f x11grab -framerate 1/5 -video_size 1680x1050 -i :0.0 -c:v libx264 -preset ultrafast -crf 0 out.mkv
```

or images:
```
$ ffmpeg -y -f x11grab -framerate 1/5 -video_size 1680x1050 -i :0.0 out%04d.png
```

Also see:
[list]
[*][HOWTO: Proper Screencasting on Linux](http://ubuntuforums.org/showthread.php?p=8746719#post8746719)
[*][FFmpeg and x264 Encoding Guide](https://trac.ffmpeg.org/wiki/x264EncodingGuide)
[/list]

---

