---
title: "Help getting v4l2 with sane"
date: 2008-12-22
forum: Multimedia Software
---

### Post by scohar70 on 2008-12-22
I have an integrated webcam on my Dell Studio 15 laptop.  It shows up as /dev/video0.  It doesn't work as a v4l device, but it does work as v4l2.

It seems only some applications support v4l2. Among those that work for me are vlc and xawtv.

But sane (and xsane) and cheese don't work with v4l2.  Does anybody know how to get sane working with v4l2 devices?

---

### Post by wolfen69 on 2008-12-22
to get it working with cheese, open a terminal and type ```
gstreamer-properties
``` not sure what you'll have to configure, but i read it works for some people. an extensive search for your sane problem yielded no results.

---

