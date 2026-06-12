---
title: "How to record a video from a webcam"
date: 2016-01-02
forum: Multimedia Software
---

### Post by s-kasimov55 on 2016-01-02
Hi,

Being very fresh to Ubuntu I cannot fathom how to to record video from my notebook internal camera. 
Please advise. The simplest option is preferable.

PS: I've tried **guvcview **but it keeps failing.

---

### Post by coldraven on 2016-01-02
> PS: I've tried **guvcview **but it keeps failing.
That's odd, guvcview is normally very good.
Try Cheese instead. It's in the Software Centre.

---

### Post by ajgreeny on 2016-01-02
> PS: I've tried guvcview but it keeps failing. 
Failing in what way?

Does it show the video and not manage to save it; does in not even show the video in real time; does it actually save the video but you are unable to find it or play it in anything?

I agree that guvcview is usually very good, and in my experience a lot better than cheese, which I never managed to get to produce a video at all!

---

### Post by s-kasimov55 on 2016-01-02
> **ajgreeny said:**
> Failing in what way?

Does it show the video and not manage to save it; does in not even show the video in real time; does it actually save the video but you are unable to find it or play it in anything?

I agree that guvcview is usually very good, and in my experience a lot better than cheese, which I never managed to get to produce a video at all!

**guvcview** doesn't show the video or image and then stops.

As for Cheese it seems to record the video but I cannot find the file and cannot find out how to setup the filename for the record.

In general it looks strange that such a basic task cannot be done in a strightforward way.

---

### Post by s-kasimov55 on 2016-01-03
Eureka!

I've found the video recorded by Cheese. It is in the folder Video ->Webcam.

Sorry for the trouble incurred.

Cheers. SK

---

### Post by Bucky Ball on 2016-01-03
*Thread moved to** Multimedia Software**.*

Well done. ;)

Please see the first link in my signature and mark the thread as solved. Don't hesitate to open a new one for any future issues.

---

### Post by FakeOutdoorsman on 2016-01-04
> **s-kasimov55 said:**
> The simplest option is preferable.

I suppose "simplest" can be interpreted several ways, but if you want a basic cli solution:

```
ffmpeg -f v4l2 -i /dev/video0 -pix_fmt yuv420p output.mp4
```

More info at [FFmpeg v4l2 docs](http://ffmpeg.org/ffmpeg-devices.html#video4linux2_002c-v4l2) and [FFmpeg Wiki: Capture/Webcam](http://trac.ffmpeg.org/wiki/Capture/Webcam).

---

