---
title: "Webcams problem"
date: 2012-06-25
forum: Multimedia Software
---

### Post by anna30wr on 2012-06-25
Hi everyone.

I've got a problem with video devices using V4L.

Assume, that I've got 2 USB webcams and one bult in laptop. All of them are seen as /dev/video*.
And the problem occurs, when I want to display (stream) video from two webcams at time.

So, for example, I run an aplication to preview webcam and choose /dev/video0. Then I run the same application once again, and I try to choose /dev/video1 or 2 (or 0, the result is the same). I can see nothing, till I exit an application which I run before. The main window in this application is a VLC plugin. So it's the same, when I run VLC two times and try to stream two different webcams. It works only for one webcam I choose firstly - no matter which one it is.
The error message is the most often "device is busy". But I don't want to stream the same device at the same time, but two different devices.

I tried to find some solution, but according to a lot of people, it is a matter of USB limits. Not in my case. My webcams has very low resolution, and it's even when I try to preview USB and built in webcams at time (no USB overload)

All I know is that mentioned devices use the same driver - V4l (or v4l2 actually) - and it looks like they have to share the driver but they can't, so always works the one I run as first.

What can I do?

---

### Post by anna30wr on 2012-06-26
Please, excuse me acting this way but I really need your help.
Because of certain important reasons I need it working...

---

