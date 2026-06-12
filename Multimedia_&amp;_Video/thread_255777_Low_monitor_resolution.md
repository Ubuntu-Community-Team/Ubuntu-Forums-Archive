---
title: "Low monitor resolution"
date: 2006-09-12
forum: Multimedia &amp; Video
---

### Post by alekz on 2006-09-12
Hi guys, i got a  Insignia™ 27" Widescreen Flat-Panel LCD HDTV and i connect my pc to it, the problem is that on ubuntu i can only reach 640*480 as maximun resolution and on windows i have 1024*768, so how can i have 1024*768 on ubuntu Dapper?

Thanks.

---

### Post by meborc on 2006-09-12
i would try

```
sudo dpkg-reconfig xserver-xorg
```

then go through the options and chose the default ones... when you reach the rezolution page, select ONLY the ones supported by your computer... good luck

---

