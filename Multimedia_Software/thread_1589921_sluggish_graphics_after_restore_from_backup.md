---
title: "sluggish graphics after restore from backup"
date: 2010-10-07
forum: Multimedia Software
---

### Post by harbhag on 2010-10-07
I had perfectly working Ubuntu 10.04 system, Last night I tried to upgrade to 10.10 and things did not worked quit well. Before upgrade I took backup of complete system using remastersys on DVD. So I restored my system using that backup and everything was same as before expect one thing and that is my graphics. I am using ati raedon graphics card. Its drivers are install via jokey but I cant enable desktop effects. I tried re-installing drivers but that did not helped.
Any suggestions ?

---

### Post by harbhag on 2010-10-07
My problem is solved. I just had to issue the following command

> sudo aticonfig --initial

---

