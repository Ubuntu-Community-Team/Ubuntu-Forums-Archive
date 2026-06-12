---
title: "For those who only hear static noise on their TV card"
date: 2005-11-16
forum: Multimedia &amp; Video
---

### Post by yaztromo on 2005-11-16
Hello, first post. Just started with Ubuntu after being a long time Windows user and am very impressed so far :)

I have a Pinnacle PCTV card and was only getting static white noise for audio.

I've spent hours and hours trying to fix this, and I notice many other people have made threads about the same problem, without resolution.

Eventually I solved it from a post on the gentoo forums.

I created a file in /etc called modprobe.conf and added the lines

options tuner pal=i
options tda9887 pal=i

This fixed it. My region is UK so you will need to modify this to your needs.

---

