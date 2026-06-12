---
title: "ffmpeg and blender"
date: 2009-04-12
forum: Multimedia Software
---

### Post by freakinjonathan on 2009-04-12
Ok I am new to blender and everytime I try to import a movie file it gives the error that ffmpeg is not compiled in.
A sudo apt-get install ffmpeg shows that it is installed.
I installed the Blender 2.48a, Python 2.5 (16 MB) from this page:

[http://www.blender.org/download/get-blender/](http://www.blender.org/download/get-blender/)
It says it includes ffmpeg support with the downlaod but I still have this error.

---

### Post by muhkayoh on 2009-05-08
It may be that you don't have all of the codecs and such that you need for the particular file you tried.  I followed just the first step at this link:

[https://wiki.ubuntu.com/ffmpeg](https://wiki.ubuntu.com/ffmpeg)

It solved a similar problem for me.

Matt

---

