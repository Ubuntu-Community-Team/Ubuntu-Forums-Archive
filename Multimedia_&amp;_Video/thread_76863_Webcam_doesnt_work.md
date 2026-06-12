---
title: "Webcam doesnt work"
date: 2005-10-15
forum: Multimedia &amp; Video
---

### Post by Teleyinex on 2005-10-15
Well, I have upgraded yesterday to breezy and this is my second problem. I have a creative webcam that worked in hoary, but now in breezy doesnt. I have recompiled the module spca5xx. The module compiles ok, and loads ok, but when I try to run camorama or gnomemeeting the system hangs.

Someone has the same problem?

---

### Post by uptimebox on 2006-01-13
[QUOTE=Teleyinex]Well, I have upgraded yesterday to breezy and this is my second problem. I have a creative webcam that worked in hoary, but now in breezy doesnt. I have recompiled the module spca5xx. The module compiles ok, and loads ok, but when I try to run camorama or gnomemeeting the system hangs.

Someone has the same problem?[/QUOTE]

I have axactly the same problem. System hangs after any process tries to access /dev/video0.

---

### Post by uptimebox on 2006-01-13
Found this in bugzilla:
[http://bugzilla.ubuntu.com/show_bug.cgi?id=16727](http://bugzilla.ubuntu.com/show_bug.cgi?id=16727)

I belive it's only partial solution, but it works.

---

### Post by chele on 2006-01-14
I installed a newer webcam driver with EasyCam. [https://wiki.ubuntu.com/Webcam]("https://wiki.ubuntu.com/Webcam")  That solved the problem for me.

---

### Post by sameeer_s on 2006-01-14
I have a creative notebook webcam.. i followed the steps on the Wiki, and got it installed (easycam ran though fine, and the webcam shows up in the Device Manager..) the problem is, i cannot seem to test it.. camorama says it cannot connect to /dev/video0, and all the other programs which can access it say the same.. i thought maybe it got installed as /dev/video1, but even that didn't work...

any idea on what the problem is... is it me? :rolleyes:

---

### Post by lnxpwr on 2006-01-17
the spca5xx driver in breezy is faulty !
try this :  [http://www.ubuntuforums.org/showthread.php?t=75284&highlight=spca5xx](http://www.ubuntuforums.org/showthread.php?t=75284&highlight=spca5xx)
it worked for me
greetinx

---

