---
title: "Telling DVgrab to stop after a set # of seconds?"
date: 2009-12-26
forum: Multimedia Software
---

### Post by Amurko on 2009-12-26
Is it possible to use DVgrab to grab only X seconds of video from my camcorder and stop?  I want to write a script that does something like the following:

while (!end of DV tape){
  i++
  dvgrab X minutes of video to test{i}.dv
  upload test{i}.dv to server
  rm test{i}.dv
}

Btw, outputting the capture directly to the server is not an option due to lack of bandwidth.

---

