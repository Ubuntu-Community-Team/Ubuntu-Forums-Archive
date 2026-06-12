---
title: "Mplayer built from source no video"
date: 2009-03-04
forum: Multimedia Software
---

### Post by videomax on 2009-03-04
I need some help. I built mplayer from source, but when I try to watch a movie, only the sound plays! I tried switching the -vo to everything listed in -vo help, but to no avail. I am on a Dell Inspiron 6400 laptop, running Ubuntu 8.10.

---

### Post by videomax on 2009-03-05
Problem solved.
I didn't have the libs downloaded for the video output drivers, lol!

If anyone has the same problem:

sudo apt-get install x-dev libxv-dev libx11-dev libxext-dev

---

