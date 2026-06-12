---
title: "Two Nvidia Video cards, Need help to setup"
date: 2006-06-10
forum: Multimedia &amp; Video
---

### Post by Quentusrex on 2006-06-10
I have two Nvidia video cards. An AGP GeForce4 Ti 4600, and a PCI GeForce4 MX 440. I have one 17" monitor plugged into each card. How do I configure ubuntu to use both monitors? I have read over a few posts talking about Twinview, but I have not found a complete list of the instructions.

Thanks.

---

### Post by blastus on 2006-06-11
Check out this thread [General 5.10 - HOWTO: TwinView](http://www.ubuntuforums.org/showthread.php?t=85769) and this link [Appendix D. X Config Options](http://download.nvidia.com/XFree86/Linux-x86_64/1.0-8762/README/appendix-d.html)

---

### Post by Quentusrex on 2006-06-11
Does that work for two video cards as well as the single dual out card he has?

---

### Post by Quentusrex on 2006-06-11
Has anyone successfully configured two video cards to work with ubuntu dapper?

---

### Post by Quentusrex on 2006-06-11
I have fixed it. There is a post on the gentoo forum that if you follow directly you will succeed in setting up two video cards, atleast 2 nvidia cards. 

Generally this is what you do:
open a terminal, and type command: sudo /etc/init.d/gdm stop
then sudo X -configure
then after it has configured it will give you a command to test the new settings.
then if any problems, compare new settings with old settings which weren't changed
fix problems and you are done.

---

