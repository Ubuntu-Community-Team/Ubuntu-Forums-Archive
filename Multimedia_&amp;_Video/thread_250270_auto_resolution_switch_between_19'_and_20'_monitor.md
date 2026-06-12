---
title: "auto resolution switch between 19' and 20' monitor"
date: 2006-09-03
forum: Multimedia &amp; Video
---

### Post by pingp on 2006-09-03
Hallo, all

I have a IBM X61 notebook with Intel 950 grapic chip. I alway use a extra monitor running in dual head mode. I would like to have one monitor home is 19' 1280x1024 and one monitor at office 20' 1600x1200.

My question is how can I configure the xorg.conf, so taht the X window recognize and switch the resolution for extra monitor? in section Device set option 1600x1200 1280x1024 ... it works?

---

### Post by Ziox on 2006-09-03
that should work, since Ubuntu uses the max resolution of the connected monitor.  I would also suggest add this option in both Device sections:

Option "DDCMode" "true"

---

