---
title: "Put one video on top of another"
date: 2013-12-16
forum: Multimedia Software
---

### Post by abhishes on 2013-12-16
I created one video using the screen capture recordmydesktop software.

I also created one video using gtk uvc video software. (basically made a recording from my webcam).

Now what I want to do is to superimpose the video captured by gtk uvc in the corner of the video captured by recordmydesktop.

So basically, people see my screencast which was captured via the recordmydesktop. but can also see me speak in the small corner of the video.

Is it possible to superimpose the video and put one in the corner of the other?

---

### Post by jones quest on 2013-12-16
You can overlay the two videos with OpenShot, which is available through the software center.
Just make a new project. Import both video files. Add the clips as two separate tracks (for example track 1 on bottom, track 2 on top). Change the layout of the top track to fill only a fraction of the screen (for example 25%), and change the position of the track (for example top left). Export the project as a new video file.

---

### Post by FakeOutdoorsman on 2013-12-16
Can you show some info about both inputs:
```
ffmpeg -i input1.ogv -i input2.mp4
```

---

