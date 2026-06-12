---
title: "Can I use my DSLR as webcam through gphoto2 + v4l2loopback?"
date: 2015-01-28
forum: Multimedia Software
---

### Post by guilherme9 on 2015-01-28
So, what i'm trying to do may be a little complicated, by i'm finding my way.

Let me explain the basics:

1 - I have an DSLR camera and i want to use it as webcam (but v4l2 can't make a /dev/videoX device with it, so no internet application can use it, only specific applications such as Darktable)

2 - I can get get live frames from the camera through gphoto2 (but i'm not sure about how to pipe them, and if i'm going to need to scale and encode/decode them)

3 - I can use v4l2loopback to create a fake webcam device (like /dev/video1) and i can use gst-launch to pipeline data to it (But i'm not sure how can i pipeline frames to it tough)

And what i know about it:

1 - I can send the frames from the camera to stdout like this:

```
gphoto2 --capture-movie --stdout
```

2 - I can send data from a video test source to the fake webcam device like this (and it works, i can even use google hangouts with this):

```
gst-launch-0.10 videotestsrc ! v4l2sink device=/dev/video1
```

3 - the format used by gphoto2 is mjpg (JPEG format)

So, can you help me with this?

How can i pipeline the frames from gphoto2 to gst-launch, and use it with v4l2sink to send them to /dev/video1 (so i'll be able to use it as a webcam)? 

Thanks!

---

### Post by Reinaert_Albrecht on 2015-08-24
You can easily do this with the following commands:

    ```
modprobe v4l2loopback
```

And then issue this:

    ```
gphoto2 --stdout --capture-movie | gst-launch-0.10 fdsrc ! decodebin2 name=dec ! queue ! ffmpegcolorspace ! v4l2sink device=/dev/video0
```

Change the video device appropriately.

---

