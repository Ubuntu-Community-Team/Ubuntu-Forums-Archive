---
title: "How do I reduce avi video file size?"
date: 2010-06-07
forum: Multimedia Software
---

### Post by kwabena39 on 2010-06-07
Hello,

I have rendered out less than two minutes of High Definition animation to Avi-Jpeg Format in Blender.  Now, I have this 2 GB file.  Going at this rate, it's going to take a whole DVD set to play a 15 min movie.

Surely, this file doesn't need 2 GB just for 1:45 min/sec, right?  Even at high def?

How do I reduce this file size down to like a manageable number, say, 20 miB?

Thanks

---

### Post by no2498 on 2010-06-08
you can try tragtor

[http://mein-neues-blog.de/tragtor-gui-for-ffmpeg/](http://mein-neues-blog.de/tragtor-gui-for-ffmpeg/)


hope that helps

---

### Post by FakeOutdoorsman on 2010-06-08
> **kwabena39 said:**
> Hello,

I have rendered out less than two minutes of High Definition animation to Avi-Jpeg Format in Blender.  Now, I have this 2 GB file.  Going at this rate, it's going to take a whole DVD set to play a 15 min movie.

Surely, this file doesn't need 2 GB just for 1:45 min/sec, right?  Even at high def?

How do I reduce this file size down to like a manageable number, say, 20 miB?

Thanks
FFmpeg is the perfect tool for video encoding, but I have some questions before I give you an example command:
[list][*] What version of Ubuntu are you using?
[*] I'm unfamiliar with Blender. What video export options or other formats does Blender allow you to use?
[*] Can you show some more details about your input file? You can do that with:[/list]
```
ffmpeg -i input.foo
```
**input.foo** being the name of your input file of course.

---

