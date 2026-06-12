---
title: "using a udp stream of jpg's as input to avconv"
date: 2013-01-14
forum: Multimedia Software
---

### Post by hhbell370 on 2013-01-14
I have a java program that does some drawing and then converts it to a jpg and sends it via udp to avconv.  I am getting the message: Invalid data found when processing input.
I tried saving the jpg to a file instead of transmitting it and was able to view it with firefox with no problem.  My avconv command line is:
avconv -s svga -codec jpg -i udp://127.0.0.1:8585 test.swf
Do I need to send any type of header before sending the sequence of jpg frames to avconv?  Any help would be appreciated.

---

