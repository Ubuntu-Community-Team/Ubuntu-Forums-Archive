---
title: "How to split a 2h mp3 file into 10min mp3 files?"
date: 2009-04-19
forum: Multimedia Software
---

### Post by susanne260 on 2009-04-19
I have an mp3 file that is exactly 2 hours long. I would like to split it into 12 mp3 files that all last 10 minutes equally. What ways are there to accomplish this? :KS

I know that Audacity could probably do it, but that program is just overwhelming. :D

---

### Post by logos34 on 2009-04-19
Installl mp3splt:

sudo apt-get install mp3splt

> mp3splt -t 10.00 2hrfile.mp3

more info:

man [mp3splt]("http://mp3splt.sourceforge.net/mp3splt_page/documentation/man.html")

---

### Post by susanne260 on 2009-04-20
That worked great, thanks! =)

---

