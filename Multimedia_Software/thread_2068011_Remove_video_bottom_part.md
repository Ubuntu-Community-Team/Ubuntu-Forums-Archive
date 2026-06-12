---
title: "Remove video bottom part"
date: 2012-10-08
forum: Multimedia Software
---

### Post by alfirdaous on 2012-10-08
Hello there,

I have a video that  I would like to crop the bottom part by 50 pixels, is there any way to get it done using FFMPEG command line??

thx in advance

---

### Post by FakeOutdoorsman on 2012-10-08
You can use the crop filter. My example input is 640x480:
```
ffmpeg -i input -vf crop=iw:ih-50:0:0 output
```
This will result in an output that is 640x430 with the bottom 50 pixels removed. *iw* is "input width" and *ih* is "input height". See the *crop* section of **man ffmpeg** for more examples. Note that *libx264* will not accept odd values, so if you use that encoder you may have to crop more or less than 50 pixels or add padding to achieve an output height that is an even number.

---

### Post by alfirdaous on 2012-10-08
thanks [FakeOutdoorsman]("http://ubuntuforums.org/member.php?u=162846"), I will see the ffmpeg man page for the option crop :lolflag:

---

