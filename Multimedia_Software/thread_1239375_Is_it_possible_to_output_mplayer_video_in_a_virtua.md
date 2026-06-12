---
title: "Is it possible to output mplayer video in a virtual video device input?"
date: 2009-08-13
forum: Multimedia Software
---

### Post by Repgahroll on 2009-08-13
Hello.

My webcam isn't "app-friendly", it just don't work with some apps like Skype and OpenCV-based ones, i tried a lot of fixes (blacklising modules, preloading v4l libs, switching and removing modules) and the thing simply don't work.

I really need to use such apps, especially the OpenCV-based ones, so i had an idea... Mplayer can print on screen the webcam input flawlessly. So i want Mplayer to print in a "virtual app-friendly video device" the webcam input.

For example, the physical webcam is video0, so mplayer reads it and writes in realtime on video1, which is a virtual and fully compatible video device. Then i "point" all my apps to video1.

I know it's possible in theory, just don't have any idea on how to do it in real life.

I think such workaround will surely solve a lot of problems related to webcam for a lot of people... i know it should be cpu-intensive, but nowadays a lot of people has dual-cores and it should not be a problem for them.

Thank you very much.

---

### Post by gabro_1980 on 2009-08-27
bump!

Me too, I'd really like to use a workaround like this

G:

---

