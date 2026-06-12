---
title: "Amarok wont play 24bit/96Khz flac"
date: 2011-01-15
forum: Multimedia Software
---

### Post by nafihsus on 2011-01-15
I am running ubuntu 10.04 and try to get 24bit/96 Khz flacs heard with Amarok (Xine engine). Amarok after some seconds jumps to the next title -> no sound.
No problems with Rhythmbox.
Any idea what I need to do?

---

### Post by NightwishFan on 2011-01-15
Try using the Gstreamer engine if possible, it apparently is better just less finished or something.

---

### Post by mc4man on 2011-01-15
I believe it was the 1.1.18 version of xine-lib that fixed that issue.
Available by default in 10.10, (10.04 missed out by several days, karmic obviously not.

It is possible to build 1.1.18 or .19 for 9.10 or 10.04 though not exactly trivial.
Otherwise search out a ppa or consider an upgrade.

---

### Post by nafihsus on 2011-01-18
:)
Thx for the help. gstreamer engine works fine. 
I am happy with the 10.04 version and didn't want to upgrade yet.

---

