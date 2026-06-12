---
title: "Video Editor - Multi Rotate (FF)"
date: 2020-07-15
forum: Multimedia Software
---

### Post by hextonum on 2020-07-15
Hi,  I've taken a longish video on my iPhone, but I was more interested in capturing the best image than considering orientation; so when transferred over (it was 800mb+.mov but I've run it through handbrake to a more reasonable webby mp4 to about 100mb). 
However I still have my orientation issue. Can someone advise of some software that I can stretch out and reorient selected sections? Out of 15 minutes there are about 4 or 5 landscape to portrait switches. 
I want to be able to upload it without the viewers having to bend their neck every couple of minutes.
Thanks
FocalFossa 20.04 \Gn3.36.3

---

### Post by vanadium on 2020-07-15
A simple linear editor like Avidemux can do that. You will have to split your video, process the sections you want separately and make sure they end up being in the same format again as the unchanged sections, after which you can concatenate the sections again. Unchanged sections would not need reencode this way.

Otherwise, most non-linear ("full") video editors (kdenlive, cinelerra, ...) should be able to do transformations on selected sections, after which you write out the whole project in a final video file.

---

