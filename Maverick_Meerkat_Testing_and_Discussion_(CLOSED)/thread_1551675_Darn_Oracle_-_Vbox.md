---
title: "Darn Oracle - Vbox"
date: 2010-08-12
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by cariboo on 2010-08-12
I tried installing vbox-puel 3.2 today, and it won't install because of unmet dependency. It needs:

[list]
[*]libqt4-network (>= 4:4.5.3)
[*]libqt4-opengl (>= 4:4.5.3)
[/list]

While 

[list]
[*]libqt4-network_4%3a4.7.0~beta2-0ubuntu4
[*]libqt4-opengl_4%3a4.7.0~beta2-0ubuntu4
[/list]

are in the repository.

I installed vbox-ose from the repositories instead

---

### Post by plun on 2010-08-12
I am running ver 3.2.8 without any trouble.

[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)


( I also need USB support therefore the ose version is nothing for me)

---

### Post by cariboo on 2010-08-12
I just wanted to test the daily build before installing, so usb isn't important at this time.

---

### Post by xebian on 2010-08-12
> **cariboo907 said:**
> I just wanted to test the daily build before installing, so usb isn't important at this time.

what @plun is saying is you are the only having that problem.

BTW the version in the repo 4.7.0 satisfies the req of >=4.5.3

---

### Post by uRock on 2010-08-12
> **cariboo907 said:**
> I tried installing vbox-puel 3.2 today, and it won't install because of unmet dependency. It needs:

[LIST]
[*]libqt4-network (>= 4:4.5.3)
[*]libqt4-opengl (>= 4:4.5.3)
[/LIST]

While 

[LIST]
[*]libqt4-network_4%3a4.7.0~beta2-0ubuntu4
[*]libqt4-opengl_4%3a4.7.0~beta2-0ubuntu4
[/LIST]

are in the repository.

I installed vbox-ose from the repositories instead
The 3.2.8 version just released [last week]("http://www.virtualbox.org/wiki/News"), which may work fine. I would test it but I am not sure installing a vbox within a vbox would go over very well.

---

### Post by cariboo on 2010-08-13
Version 3.2 is the only stable version available on the web site. they don't officially have a version for Maverick yet.

I'm aware there are beta versions available, but before Oracle bought Sun, Sun was much quicker making updated versions during the testing phase available.

---

### Post by Starks on 2010-08-13
sudo dpkg -i virtualbox-3.2_3.2.8-64453~Ubuntu~lucid_i386.deb

Works for me.

---

### Post by cariboo on 2010-08-13
Already done. :)

---

