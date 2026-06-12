---
title: "Bootscreen defect after activating display drivers"
date: 2010-10-15
forum: Multimedia Software
---

### Post by infected?! on 2010-10-15
Hi!

Installed ubuntu 10.10 without any problems. Everything works fine until i installed the ati display drivers. After this ubuntu shows me 3 different screens before login that [COLOR=#000000]apparently broken (see attachments). After the last screen the "normal" login screen is shown.

If i dont use the drivers everything looks fine, but then my gpu fan (radeon 4890hd) runs at 100% which is a bit noisy. :mad:
[/COLOR]

---

### Post by myandylai on 2010-10-15
I have the same problem too. I am using ATI 5670. But considering that it just happen for a few second and it doesn't seem too have any negative effect after login to gnome so I totally ignore it. And it also happen when I restart or shutdown Ubuntu 10.10. Seem that what should be displaying on terminal went out to the Ubuntu bootscreen.

---

### Post by .... on 2010-10-15
I don't see a problem except maybe misalignment of the error message in plymouth. This happens to me on some systems, especially with proprietary drivers, since they don't use kernel mode-setting and don't play nice with plymouth.

---

### Post by infected?! on 2010-10-16
Okay, i totally agree: It does not have any negative effect. Ubuntu works well. But it´s not the best way to ignore this issue just because everything is working... This is definetely the wrong way and this should be fixed.

---

### Post by sadaka on 2010-10-17
Is there any known bug report for that?
Also got ugly boot screen after enabling ATI drivers... =((

---

### Post by sadaka on 2010-10-17
JFY:
I followed solution no2 in
[http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml](http://news.softpedia.com/news/How-to-Fix-the-Big-and-Ugly-Plymouth-Logo-in-Ubuntu-10-04-140810.shtml)

And after some minor changes in [I]StartUp-Manager I've got reasonable boot screen
[/I]

---

### Post by .... on 2010-10-18
> **infected?! said:**
> But it´s not the best way to ignore this issue just because everything is working... This is definetely the wrong way and this should be fixed.

I agree, and so do the many other users who have reported the issue. Unfortunately, I don't see it being resolved any time soon since the issue is with a closed-source module (or maybe the issue is plymouth depending on who you ask).

At any rate, I'm glad someone posted a workaround. Thanks for that and good luck getting the bug fixed. Please mark thread solved.

---

### Post by infected?! on 2010-10-20
No, it´s solved when it´s really fixed. The workaround is nice and works well, **but i don´t like to fix so simple things on my own from release to release**. Why its so diffucult to implement this fix in a final version? Once implemented it doesnt hurt anyone. This fix also doesnt have any negative effect when using no video drivers... 

There are so many small bugs that already have could been fixed... Why we have to fix it always on our own?! I think know the answer: Because each time someone is saying "There´s a workaround for this, use it".

---

### Post by .... on 2010-10-20
> **infected?! said:**
> Why its so diffucult to implement this fix in a final version? 
I already answered this, but I'll try again. The problem (a well-known one) is in a closed-source module. Fglrx/Catalyst does not use KMS/DRI2, which is required for proper plymouth display. ATI does not have bug reports open to the public, so they will fix it if/when they feel like it.
The workarounds are dirty hacks and Canonical is not going to implement them as defaults, so you have the following options:
- implement the workarounds yourself
- Stop caring so much about your bootscreen appearance and/or wait for ATI to fix their closed-source Linux driver (good luck with that....)
- Use open-source ATI driver and work on finding solution for fan control (the 2.6.36 kernel should have improved support)

---

### Post by sadaka on 2010-10-20
The stuff you guys are talking about is actually a price we sometimes have to pay for using cutting edge techs. I've been using LTS 10.04 for quite some time, and noticed only 2 or 3 minor defects (some of them present in 10.10, btw =( ).
You can always fall back to LTS if latest release is not stable enough for you configs. Or even to debian :D.

Anyway, I am eagerly waiting for Canonical to resolve as much defects as possible, and as soon as possible (ATI driver from their repos suck big time in 10.10 comparing to the one from official site).

Many thanks for them for awesome work.

---

### Post by SeePU on 2010-10-21
ATI doesn't give a crap about Linux.  They hire two guys and place them in a dungeon with a large amount of crack while paying them one dollar bill each.

---

