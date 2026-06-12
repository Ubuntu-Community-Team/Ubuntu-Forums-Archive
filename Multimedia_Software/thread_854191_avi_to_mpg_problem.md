---
title: "avi to mpg problem"
date: 2008-07-09
forum: Multimedia Software
---

### Post by stoppage on 2008-07-09
Im running Ubuntu „Feisty“, in trying to encode avi's (Xvid) to dvd-standard mpg the resulting file plays ok but duration is way out! Same result using avidemux and tovid. Can anybody help please?

---

### Post by tszanon on 2008-07-09
> **stoppage said:**
> Im running Ubuntu „Feisty“, in trying to encode avi's (Xvid) to dvd-standard mpg the resulting file plays ok but duration is way out! Same result using avidemux and tovid. Can anybody help please?
Oh well. I know next to nothing about video conversion, so I can't really help you. But Feisty is a little old by now. Maybe the programs you're using to convert these video files have bugs that have already been corrected in newer versions. I suggest checking if that is the case.

---

### Post by arsenic23 on 2008-07-09
You could use ffmpeg.

Here's some information:

[http://kylecordes.com/2006/03/31/dvd-ffmpeg/](http://kylecordes.com/2006/03/31/dvd-ffmpeg/)
[http://tuxicity.wordpress.com/2006/12/01/avi-to-dvd-with-ffmpeg-and-dvdauthor/](http://tuxicity.wordpress.com/2006/12/01/avi-to-dvd-with-ffmpeg-and-dvdauthor/)
[http://gentoo-wiki.com/HOWTO_Create_a_DVD:Encode](http://gentoo-wiki.com/HOWTO_Create_a_DVD:Encode)

---

### Post by FakeOutdoorsman on 2008-07-09
A basic ffmpeg command using "-target":
```
ffmpeg -i inputvideofile.avi -target dvd outputvideofile.mpg
```
Another example using "-target pal-dvd":
```
ffmpeg -i inputvideofile.avi -target pal-dvd outputvideofile.mpg
```

---

### Post by stoppage on 2008-07-10
I went ahead & encoded to DVD with DVD author & it burned and played no problem. But this doesn't explain why "Properties" window showed incorrect duration of mpg. And thank you for the help.

---

