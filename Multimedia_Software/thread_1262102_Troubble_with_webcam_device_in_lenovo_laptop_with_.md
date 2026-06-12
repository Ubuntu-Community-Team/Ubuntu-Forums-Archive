---
title: "Troubble with webcam device in lenovo laptop with usbid 17ef:4807"
date: 2009-09-09
forum: Multimedia Software
---

### Post by nidelius on 2009-09-09
Hello!

I'm trying to get my webcam in my lenovo x300 to work. People report that it should work by default in 9.04. But it didn't for me..

So I tried to install new uvc drivers two three times.. all I get now is a black window in skype, green window in mplayer and nothing in cheese.

Bus 002 Device 002: ID 17ef:4807 Lenovo

How do I check what's wrong. Tried to check in loggs but it didn't give me anything useful.

The most useful info I got was from:

```
mplayer tv:// -tv driver=v4l2:width=640:height=480:fps=25:device=/dev/video0
```
```
v4l2: ioctl get standard failed: Invalid argument
Selected device: UVC Camera (17ef:4807)
 Capabilites:  video capture  streaming
 supported norms:
 inputs: 0 = Camera 1;
 Current input: 0
 Current format: YUYV
v4l2: ioctl set format failed: Invalid argument
v4l2: ioctl set format failed: Invalid argument
v4l2: ioctl set format failed: Invalid argument
tv.c: norm_from_string(pal): Bogus norm parameter, setting default.
v4l2: ioctl enum norm failed: Invalid argument

```

I'll try downloading a new uvc driver and compile it to see if it gives me luck.

---

