---
title: "Converting files to wmv, avi, etc"
date: 2010-01-26
forum: Multimedia Software
---

### Post by sophicsage on 2010-01-26
My Ubuntu 9.10 is working great.  It's quite stable.  I'm having issues with being able to convert videos I record of me saying hi to my family back home, but they are recorded in OGV format and I'm having trouble using the VLC media player to convert it to a file so that it can be seen and heard on the receiving end.  What's an easy way to record in wmv, mpeg, avi, etc?  I've seen this issue address before, but unfortunately the answer is usually "rename it to ogg", but this is apparently more difficult than just doing it.  I'm sure I'm not doing something right, but I'd like to be able to send these messages to my kid back home.  Thanks for any help...

Oh....I've been using Cheese to record and was trying to use VLC of course to convert, if that helps any.

---

### Post by chewearn on 2010-01-27
[https://help.ubuntu.com/community/Webcam](https://help.ubuntu.com/community/Webcam)

---

### Post by howefield on 2010-01-27
> **sophicsage said:**
> ...What's an easy way to record in wmv, mpeg, avi, etc?

You could try converting with Winff or Handbrake.

Another option (but not one I've tried) is described here

[https://wiki.ubuntu.com/ogg2avi](https://wiki.ubuntu.com/ogg2avi)

---

### Post by Enigmapond on 2010-01-27
also ffmpeg will do it...

```
ffmpeg -i *file.wmv file.avi*
```

---

### Post by howefield on 2010-01-27
If ffmpeg can do it, Winff will also, given that Winff is merely a front end to the excellent ffmpeg. 

Command line or GUI, your choice, but essentially the same thing.

---

### Post by Chronon on 2010-01-27
> **sophicsage said:**
> My Ubuntu 9.10 is working great.  It's quite stable.  I'm having issues with being able to convert videos I record of me saying hi to my family back home, but they are recorded in OGV format and I'm having trouble using the VLC media player to convert it to a file so that it can be seen and heard on the receiving end.  What's an easy way to record in wmv, mpeg, avi, etc?  I've seen this issue address before, but unfortunately the answer is usually "rename it to ogg", but this is apparently more difficult than just doing it.  I'm sure I'm not doing something right, but I'd like to be able to send these messages to my kid back home.  Thanks for any help...

Oh....I've been using Cheese to record and was trying to use VLC of course to convert, if that helps any.

You could also encourage them to use VLC on their end.  I find VLC to be an excellent media player on any platform.

---

### Post by Enigmapond on 2010-01-27
Very true. It's just a matter of personal preference. I prefer using the command line for things rather than a GUI frontend.

Cheers!

---

