---
title: "Speed UP UVCCapture / Webcam Snapshot"
date: 2012-12-14
forum: Multimedia Software
---

### Post by BackBONE7 on 2012-12-14
Hi,

i am using Agisoft Photoscan to create base-meshes for sculpting.
([http://www.agisoft.ru/products/photoscan/standard/](http://www.agisoft.ru/products/photoscan/standard/))
Right now i am taking all photos manually, witch is fine for inanimate objects.
For People a multi-camera set would be best.
I believe the easiest way would be to use multiple web-cams, because the
images can be directly transferred into a directory. 
With UVCCapture it is pretty easy to take snapshots from different sources,
however it takes time.
My script looks like this.
```

uvccapture -d"/dev/video0" -o"../snap0.jpg" -m
uvccapture -d"/dev/video1" -o"../snap1.jpg" -m

```Even with only 2 cameras it takes about 2 Seconds. My Goal is to get snapshots from 20 to 35 cameras in under 3 Seconds.
The best way would probably be, to use one mini PC for every camera, and send the images over a network to one directory. But for the same Money i could buy a
Structured Light scanner, with better performance. (and right now i don't have that amount of cash).

Is there a way to speed up the process? It is not important that the Images are transferred quickly. The only thing that matters is that the Images are taken at the same moment (+- 2 sec.).

Any suggestions??

---

