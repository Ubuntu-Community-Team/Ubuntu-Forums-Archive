---
title: "Convert flv to wmv"
date: 2008-08-01
forum: Multimedia Software
---

### Post by simonlugi on 2008-08-01
I have Ubuntu Hardy install and would like to know what is the best application for converting flv files to wmv
Simon

---

### Post by kahlil88 on 2008-08-01
In my experience, converting FLV results in a terribly out-of-sync video. Why not just open them in [VLC]("http://www.videolan.org/")?

---

### Post by kostkon on 2008-08-01
> **simonlugi said:**
> I have Ubuntu Hardy install and would like to know what is the best application for converting flv files to wmv
Simon
You could try doing it with *FFmpeg* and a GUI frontend like [*WinFF*]("http://www.winff.org/") (or any other you like). But you'll have to install the version of *FFmpeg* that is offered by the [*Medibuntu* repository]("http://www.medibuntu.org/") (instructions on how to add this repository are on the site) and has the support for restricted formats enabled.

Thus, add this repository, install *FFmpeg* and use it with a frontend or from the command line.

---

### Post by simonlugi on 2008-08-01
Thanks.

---

### Post by windozh8ter on 2011-03-05
Using ffmpeg and winff is still a good tip, even almost 3 years later. I was trying to convert .flv files in OpenShot Video Editor, but wasn't getting good results getting these to play in MS PowerPoint (ugh) even after several attempts at a variety of formats. ffmpeg with winff was really easy to use, can convert to .wmv, and even powerpoint specific settings. I also like that it can handle batch conversions. Thanks, Kostkon.

---

