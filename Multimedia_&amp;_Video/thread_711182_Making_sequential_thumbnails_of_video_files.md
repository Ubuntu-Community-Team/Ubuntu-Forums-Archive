---
title: "Making sequential thumbnails of video files"
date: 2008-02-29
forum: Multimedia &amp; Video
---

### Post by fettuohi on 2008-02-29
I was wondering if there is a similar tool on linux/ubuntu to make sequential thumbnails from video files like the Media Player Classic can under windows, i.e. 

[http://www.dotcomunderground.com/blogs/2006/09/20/how-to-make-sequential-thumbnails-of-a-video-using-free-tools/](http://www.dotcomunderground.com/blogs/2006/09/20/how-to-make-sequential-thumbnails-of-a-video-using-free-tools/)

I know that VLC, MPlayer, SMPlayer can take screenshots of playing video files but is there a tool that make several thumbnails and bind them all together in one jpg etc.?

Regards

André

---

### Post by rvm4000 on 2008-02-29
I made a script for myself (requires php, ImageMagick and mplayer), in case you want to try it: [videopreview.tar.gz](http://www.escomposlinux.org/rvm/temp/videopreview/videopreview.tar.gz)

Sample:
```

videopreview.php -tile 4x5 -w 640 -o image.jpg video.avi

```

produces an image like this:

[[IMG]http://img255.imageshack.us/img255/5884/cosabk5.th.jpg[/IMG]](http://img255.imageshack.us/my.php?image=cosabk5.jpg)

---

### Post by anoxi on 2008-05-30
try [http://developer.berlios.de/projects/qframecatcher/](http://developer.berlios.de/projects/qframecatcher/)

Dependencies
-------------------------------------

- Qt 4.1.0 or higher

- libxine 1.1.1 or higher

- libpng

---

