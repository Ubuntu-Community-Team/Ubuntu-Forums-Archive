---
title: "Windows Media 9"
date: 2009-03-15
forum: Multimedia Software
---

### Post by kodiakmax on 2009-03-15
I've been having problems getting this to run on my amd64 machine runing jaunty(9.04)

After installing as many codecs as I could find nothing seemed to help.  I can get video if it is encoded with wmv9 but no audio if it is encoded with wma9.  here are some test files: [http://tiny.cc/llJEn](http://tiny.cc/llJEn)

What I finally did was download the combined community codec pack found here: [http://tiny.cc/rylOn](http://tiny.cc/rylOn)
I installed the pack with wine.  then added the following for the media player classic home cinema edition which is included with the pack.
have it run with Windows NT 4.0 and then override the devenum and quartz libraries.

After that wmv files using wma9 are able to play fairly well.

Any other ideas are welcome.

---

