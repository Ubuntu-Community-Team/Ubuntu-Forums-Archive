---
title: "Songbird not playing MP3s"
date: 2009-04-28
forum: Multimedia Software
---

### Post by amitabhishek on 2009-04-28
So that's the problem, I tried installing:

```
sudo aptitude reinstall gstreamer0.10-plugins-ugly
```

it didn't work. Though I can play MP3s through VLC  etc. Please check attached thumbnail for the error. Any help?

---

### Post by HappyFeet on 2009-04-28
Try
```
sudo apt-get install libxine1-ffmpeg
```
Not sure, but you may need the Medibuntu repos enabled to install it.

---

### Post by amitabhishek on 2009-05-03
Thanks for your help but still the darn thing doesn't work...:confused:

---

### Post by xc3RnbFO8P on 2009-05-03
Read this:
[http://getsatisfaction.com/songbird/topics/media_core_error_resource_not_found]("http://getsatisfaction.com/songbird/topics/media_core_error_resource_not_found")

---

