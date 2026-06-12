---
title: "Segmentation fault with FFmpeg"
date: 2009-10-12
forum: Multimedia Software
---

### Post by atinazzi on 2009-10-12
I am posting this thread to share my findings with other people that may be experiencing the same issue.

My system is running Ubuntu 9.04 amd64
FFmpeg 0.5-svn17737+3:0.svn20090303-1ubuntu6
libavutil     49.15. 0 / 49.15. 0
libavcodec    52.20. 0 / 52.20. 0
libavformat   52.31. 0 / 52.31. 0
libavdevice   52. 1. 0 / 52. 1. 0
libavfilter    0. 4. 0 /  0. 4. 0
libswscale     0. 7. 1 /  0. 7. 1
libpostproc   51. 2. 0 / 51. 2. 0
built on Apr 10 2009 23:20:33, gcc: 4.3.3

The problem was caused by Openshot video editor.
Removing the application and related dependencies fixed the problem.

---

