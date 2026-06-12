---
title: "Q-Tec web cam program"
date: 2007-08-17
forum: Multimedia &amp; Video
---

### Post by DamjanDimitrioski on 2007-08-17
[CENTER]**Q - Tec Web camera**[/CENTER]
Hi, is there any good program for capturing pictures from a **webcam**, but to have ability to configure the web camera, especially _q-tec 100k_.
:KS

---

### Post by PatrickB on 2007-08-18
Have you tried [this](http://mxhaard.free.fr/spca5xx.html) driver yet? It provides a V4L device for accessing the webcam. I used it myself for my Q-Tec 100k webcam.

EDIT: And don't make the same mistake I just did (I just reinstalled it) by forgetting to download the viewer tools. V4L doesn't seem to work real good with my webcam (Q-Tec 100).

---

### Post by DamjanDimitrioski on 2007-08-18
My web camera is supported, but i need a software for capturing from the camera, or lib for making my own program. :)

---

### Post by PatrickB on 2007-08-18
If your camera is supported via V4L, then you can capture via MEncoder. You have to install MPlayer for this.

If you have installed it, you can find documentation about how to use it in **/usr/doc/MPlayer-1.0rc1/HTML/en/index.html**. I believe it is section 10, TV. There are some examples about how to record from TV (V4L!) in subsection 3 I tought.

EDIT: Or download the toolspackage from the site I mentioned earlier, it gives you the option to capture, and to set color, brightness and contrast. It is called SPCAview.
I mean [this program (source download)](http://mxhaard.free.fr/spca50x/Download/spcagui20060127.tar.gz), more info is [here](http://mxhaard.free.fr/sview.html).

---

