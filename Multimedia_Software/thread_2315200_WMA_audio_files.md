---
title: "WMA audio files"
date: 2016-02-26
forum: Multimedia Software
---

### Post by Charlotte18 on 2016-02-26
In the olden days, I purchased some WMA files in Windows. Now I am using Ubuntu 15.10 and have a curious, but not especially urgent, situation. The WMA files play fine in Audacious and VLC, but they won't play in Banshee.  I guess something is missing in  gstreamer or another package, but can anyone tell me how to empower Banshee also to play WMA files? I am using Ubuntu 15.10.

---

### Post by deadflowr on 2016-02-27
Moved to *Multimedia Software*

---

### Post by Yellow Pasque on 2016-02-27
Do you have gstreamer1.0-libav package installed?

```
$ gst-inspect-1.0 | grep -i wma
libav:  avdec_wmavoice: libav Windows Media Audio Voice decoder
libav:  avdec_wmav2: libav Windows Media Audio 2 decoder
libav:  avdec_wmav1: libav Windows Media Audio 1 decoder
libav:  avdec_wmapro: libav Windows Media Audio 9 Professional decoder
libav:  avdec_wmalossless: libav Windows Media Audio Lossless decoder
libav:  avenc_wmav2: libav Windows Media Audio 2 encoder
libav:  avenc_wmav1: libav Windows Media Audio 1 encoder
typefindfunctions: video/x-ms-asf: asf, wm, wma, wmv
```

---

### Post by goofprog on 2016-02-29
I would just suggest to convert the WMA files to more of a cross platform accepted format.  I like converting them to M4A files.  WMA files are meant for Windows only but it can be played too.  I say if you have too many issues just convert them.  The issue is if they are DMA protected audio files.

---

### Post by Yellow Pasque on 2016-02-29
> **goofprog said:**
> I would just suggest to convert the WMA files to more of a cross platform accepted format.  I like converting them to M4A files.  WMA files are meant for Windows only but it can be played too.  I say if you have too many issues just convert them.  The issue is if they are DMA protected audio files.

Lossy -> Lossy conversions aren't recommended for music. Voice may be a different story.

---

### Post by Modanung on 2016-02-29
You may run into [this]("http://askubuntu.com/questions/508625/python-v2-7-requires-to-install-plugins-to-play-media-files-of-the-following-t/") problem.

---

### Post by Charlotte18 on 2016-03-16
Thanks to everyone. The solution ended up being that certain gstreamer packages were not installed in lububtu.

---

