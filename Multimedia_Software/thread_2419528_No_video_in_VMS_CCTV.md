---
title: "No video in VMS CCTV"
date: 2019-05-23
forum: Multimedia Software
---

### Post by wabi-one on 2019-05-23
I've installed VMS app from this [https://www.ctr.pl/m_download_programy-i-aktualizacje_lc-security.htm](https://www.ctr.pl/m_download_programy-i-aktualizacje_lc-security.htm) and I launch it by winne. I have connected cameras but video isn't seen. I can do snapshot. What should I do to see seven cameras on Ubuntu 18.04?

---

### Post by Holger_Gehrke on 2019-05-24
Wine is hit-and-miss. If the program you're trying to use is using the DirectShow-API then it's likely not to work. If the cameras you're trying to get video from are IP-cameras then [zoneminder]("https://www.zoneminder.com/") might work for you.

Holger

---

### Post by wabi-one on 2019-05-28
I finally managed the Xeoma program, which is also designed for Linux. I entered rtps into each camera.

---

