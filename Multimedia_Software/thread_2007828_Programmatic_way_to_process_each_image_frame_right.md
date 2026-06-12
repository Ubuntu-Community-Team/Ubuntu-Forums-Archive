---
title: "Programmatic way to process each image frame right after capturing using x11grab"
date: 2012-06-21
forum: Multimedia Software
---

### Post by cclinus on 2012-06-21
For example, I have a program that captures screenshots from x display using command:

ffmpeg -f x11grab -s cif -r 25 -i :0.0 /tmp/out.mpg

'-r 25' means there are 25 frames being captured in a second. And my question is how to process each frame(image) and decide whether I want to keep this frame or remove it right after each image is captured. I guess this should be done in C by adding some code to ffmpeg

Any ideas? Thanks!

---

### Post by gordintoronto on 2012-06-21
What are you trying to accomplish? You're capturing video, so removing frames will speed it up. Is that what you want?

---

### Post by cclinus on 2012-06-21
> **gordintoronto said:**
> What are you trying to accomplish? You're capturing video, so removing frames will speed it up. Is that what you want?

No, I want to drop some certain frames that do not meet my standard. Say I have a checkStandard($pathToSrcFrame) that will return a boolean.

---

