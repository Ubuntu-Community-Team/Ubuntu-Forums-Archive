---
title: "firefox &amp; translate.google.com (say-it button) &amp; no sound"
date: 2012-05-20
forum: Multimedia Software
---

### Post by gam01hr on 2012-05-20
When I visit a site [translate.google.com]("http://translate.google.com") and type some word a button "say-it" speaker picture (span.jfk-button-img ) appears. But it doesn't play sound. It was working in past but after some updates (firefox updates) it is not working. Other sound in firefox, as playing youtube videos, works OK. Please does anybody know which MIME it is or which plug-in do I need?
edit1: [https://docs.google.com/open?id=0B5ZqzO2fp8UlTDBIQ0h5aDBzcVE](https://docs.google.com/open?id=0B5ZqzO2fp8UlTDBIQ0h5aDBzcVE) here is my about:plugins snapshot

---

### Post by Majlo on 2012-05-20
Hello 

You only need flash to make it work .As i can see you are using gnash and not macromedia flash and this could be a problem.

---

### Post by zombifier25 on 2012-05-20
Gnash is GNU's open source Flash clone, so it will not work with some websites. You should use Flash instead.

---

### Post by lovinglinux on 2012-05-20
It is not working on Firefox, Opera or Chrome, but I can't see any errors in the Console. I suppose it is a bug.

---

### Post by gam01hr on 2012-05-27
My problem is solved, the button works.

[LIST=1]
[*]I purged my Ubuntu 10.04 & installed Ubuntu 12.04
[*] I installed Shockwave Flash 11.1 r102
[*]I disabled all plugins except Shockwave Flash 11.1 r102
[/LIST]
My firefox version is 12.0
Now youtube videos and translate.google.com are OK

---

### Post by gri0 on 2012-08-01
I have  solve the problem too.
If you have Flashblock extension installed - just add translate.google.com
to the white list. 
Now translate.google.com speak fine.

---

