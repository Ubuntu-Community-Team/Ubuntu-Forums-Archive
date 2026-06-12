---
title: "Want advice on NEW Video Board"
date: 2006-06-20
forum: Multimedia &amp; Video
---

### Post by zigx on 2006-06-20
Hey guys...

I would like to get a new video card that can support openGL and REALLY RIP IT UP :)

i want to use XGL and possibly play games.... Do you guys have any suggestions for boards that really kick booty AND work with ubuntu w/o much hassle?

Thank you!

---

### Post by zigx on 2006-06-21
Bump bc i modified subject to be more precise.  Thank you.

---

### Post by zigx on 2006-08-21
last bump.

---

### Post by Ziox on 2006-08-21
I would say that you should get a nVidia Card...depends on your budget...but nVidia is better supported than ATI, and it is faster (most of the time)

---

### Post by VirtuAlex on 2006-08-21
totally agree

---

### Post by kr4z on 2006-08-22
You may find this site useful: [http://www.free3d.org/](http://www.free3d.org/)

---

### Post by VirtuAlex on 2006-08-22
> **kr4z said:**
> You may find this site useful: [http://www.free3d.org/](http://www.free3d.org/)
Their benchmarks are quite lame, but they state they aware of it. They compare rather apples with oranges. It's promising though, that at least something free available. I'm looking at AMD-ATI merger right now and do not know if it is for better or for worse. I hope it will eventually lead to opensourcing the driver, but so far too many people report troubles with ATI cards. As for this benchmark, my rather mediocre card with nvidia driver gives me this:
```
$ lspci | grep VGA
0000:01:00.0 VGA compatible controller: nVidia Corporation NV18 [GeForce4 MX 440 AGP 8x] (rev a2)

$ cat /proc/cpuinfo | egrep "model name|MHz"
model name      : AMD Athlon(tm) 64 Processor 3400+
cpu MHz         : 1004.894 */* It actually runs 2.4G when 3d working */*

$ xdpyinfo | egrep "version:|dimensions|depth of"
X.Org version: 7.0.0
  dimensions:    1600x1200 pixels (542x406 millimeters) */* it is wrong with mm */*
  depth of root window:    24 planes

$ glxinfo | egrep -A2 "direct rendering|OpenGL vendor"
direct rendering: Yes
server glx vendor string: NVIDIA Corporation
server glx version string: 1.4
--
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce4 MX 440 with AGP8X/AGP/SSE2
OpenGL version string: 1.5.6 NVIDIA 87.62

$ glxgears -iacknowledgethatthistoolisnotabenchmark & sleep 25 ; killall glxgears
5579 frames in 5.0 seconds = 1115.679 FPS
5593 frames in 5.0 seconds = 1118.583 FPS
5589 frames in 5.0 seconds = 1117.771 FPS
5592 frames in 5.0 seconds = 1118.396 FPS
```

---

### Post by Ziox on 2006-08-22
> **VirtuAlex said:**
> Their benchmarks are quite lame, but they state they aware of it. They compare rather apples with oranges. It's promising though, that at least something free available. I'm looking at AMD-ATI merger right now and do not know if it is for better or for worse. I hope it will eventually lead to opensourcing the driver, but so far too many people report troubles with ATI cards. As for this benchmark, my rather mediocre card with nvidia driver gives me this:
```
$ lspci | grep VGA
0000:01:00.0 VGA compatible controller: nVidia Corporation NV18 [GeForce4 MX 440 AGP 8x] (rev a2)

$ cat /proc/cpuinfo | egrep "model name|MHz"
model name      : AMD Athlon(tm) 64 Processor 3400+
cpu MHz         : 1004.894 */* It actually runs 2.4G when 3d working */*

$ xdpyinfo | egrep "version:|dimensions|depth of"
X.Org version: 7.0.0
  dimensions:    1600x1200 pixels (542x406 millimeters) */* it is wrong with mm */*
  depth of root window:    24 planes

$ glxinfo | egrep -A2 "direct rendering|OpenGL vendor"
direct rendering: Yes
server glx vendor string: NVIDIA Corporation
server glx version string: 1.4
--
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce4 MX 440 with AGP8X/AGP/SSE2
OpenGL version string: 1.5.6 NVIDIA 87.62

$ glxgears -iacknowledgethatthistoolisnotabenchmark & sleep 25 ; killall glxgears
5579 frames in 5.0 seconds = 1115.679 FPS
5593 frames in 5.0 seconds = 1118.583 FPS
5589 frames in 5.0 seconds = 1117.771 FPS
5592 frames in 5.0 seconds = 1118.396 FPS
```

I doubt that AMD-ATI merger will have a main impact, atleast not for a decade.  From what I've heard, ATI doesn't make the card themselves, rather they rely on different companies to manufacture parts of the card, and it is extremely hard, even for ATI, to open source the code if you don't the hardware...and I agree that ATI has major problems with Linux...I would always go with nvidia

---

### Post by zigx on 2006-08-23
first off... thank you to all for providing those links/suggestions !

Secondly, Do you guys think the closed source drivers are better than open source?

---

### Post by VirtuAlex on 2006-08-23
In the long run open source is always better because anybody can contribute and you don't depend on manufacturer's will to continue support for the driver. But in practice you choose what works better now. Propriatry drivers are native to hardware. They are written by the company which produces the hardware and knows exactly its ins and outs. Ideal situation is when company open source their driver - then it becomes native to linux and to hardware at the same time. But it is rarely the case nowdays.

---

