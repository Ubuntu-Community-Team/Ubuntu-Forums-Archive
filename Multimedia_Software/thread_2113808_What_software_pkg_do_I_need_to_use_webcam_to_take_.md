---
title: "What software pkg do I need to use webcam to take a picture?"
date: 2013-02-08
forum: Multimedia Software
---

### Post by nhtrader on 2013-02-08
xubuntu 12.04 (64bit)
xfe 4.8

I'd like to use my Logitech C110 on my xubuntu. What software pkg do I need?

I can add that my webcam works perfectly with Skype (audio and video and mic work great). I now would like to make: 1. a video diary and 2. take a shapshot.

---

### Post by ohwhynow on 2013-02-08
What you need may be simply Cheese:
[Cheese for 12.04]("http://packages.ubuntu.com/precise/cheese")

Oh, it's heavily dependent on gnome, yet xfce is fairly gnome-compatible, and it's probably the most user-friendly webcam app you will find on Linux platform.

You may also be interested in [Guvcview]("http://packages.ubuntu.com/precise/guvcview"). I think it may be lighter, and works too.

---

### Post by ajgreeny on 2013-02-08
I have found guvcview much better than cheese.

Cheese will take photos but not record video; guvcview will do both without a problem.  Your situation my be different, of course.

---

### Post by nhtrader on 2013-02-08
> **ohwhynow said:**
> What you need may be simply Cheese:
[Cheese for 12.04]("http://packages.ubuntu.com/precise/cheese")

Oh, it's heavily dependent on gnome, yet xfce is fairly gnome-compatible, and it's probably the most user-friendly webcam app you will find on Linux platform.

You may also be interested in [Guvcview]("http://packages.ubuntu.com/precise/guvcview"). I think it may be lighter, and works too.

> **ajgreeny said:**
> I have found guvcview much better than cheese.

Cheese will take photos but not record video; guvcview will do both without a problem.  Your situation my be different, of course.



Perfect. Thank you both. I tried guvcview. Works perfectly and it's perfect for xubuntu (low resources) b/c I have a 6 year old PC using a single core Sempron 2800+ CPU. Xubuntu enabled me to recycle this PC, and now it's a perfect desktop for my 82 year old mother. We skype; I use ssh; x11vncviewer; and remote access is a breeze, which enables to help her when she gets into trouble.

xubuntu is amazing. Now she can take a picture of the crafts that she makes and show us. It's incredible that with this old PC, it  still can do everything and anything (video playback included) without a hitch. All I have to do is avoid loading resource intensive pkgs and the system runs smoothly. guvcview was a perfect fit.

Thanks

---

### Post by FakeOutdoorsman on 2013-02-08
For anyone looking for a command-line tool to do the same:
```
ffmpeg -i -f video4linux2 -i /dev/video0 -vframes 1 output.png
```
See the [ffmpeg video4linux2 documentation](http://ffmpeg.org/ffmpeg-devices.html#video4linux2_002c-v4l2) for more examples.

---

