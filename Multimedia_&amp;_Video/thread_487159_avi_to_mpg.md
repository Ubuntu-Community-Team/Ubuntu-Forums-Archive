---
title: "avi to mpg?"
date: 2007-06-28
forum: Multimedia &amp; Video
---

### Post by linuxmann on 2007-06-28
I need a converter to convert a avi file to an mpeg or an mpg. is there any converters out there for Linux? Converting a avi file in to a smaller one would be great too. I just want to decrease the size of an avi file.

---

### Post by moore.bryan on 2007-06-28
[I]one way is to install ffmpeg
```
sudo aptitude install ffmpeg
```
and then run 
```
ffmpeg -i video_to_convert.avi -target vcd new_video.mpg
```[/I]

---

