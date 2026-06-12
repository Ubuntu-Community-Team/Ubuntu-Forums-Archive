---
title: "Natty Alpha 1, Compiz video card problem"
date: 2011-02-01
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by jim11 on 2011-02-01
I was running Natty Alpha 1 (64 bit), and it was working fine for a few weeks. I updated it this afternoon and it said that I did not meet the hardware requirements to run Unity. I have an Acer 7740 laptop with an i5 processor, and integrated intel video card.

$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 12)

I have consistently had trouble getting the brightness to adjust, due to driver problems. I have tried several means of remedying the problem including editing the grub file so that acpi="Linux". And another grub change, nomodeset acpi_backlight=vendor caused Ubuntu to boot in text mode (so i reformatted). No drivers are listed under additional drivers.

How would I go about getting the drivers to adjust the brightness and allow me to use Unity/Compiz.

I have followed suggestions from the following links:

[https://help.ubuntu.com/community/AspireTimeline/Fixes](https://help.ubuntu.com/community/AspireTimeline/Fixes)
[http://ubuntuforums.org/showpost.php?p=8411337&postcount=5](http://ubuntuforums.org/showpost.php?p=8411337&postcount=5)

---

### Post by Elfy on 2011-02-01
Please post threads about dev versions of ubuntu in the correct forum.

moved to forum

---

### Post by marijus on 2011-02-01
check out this thread: [http://ubuntuforums.org/showthread.php?t=1679795](http://ubuntuforums.org/showthread.php?t=1679795)

hope it works for you... if it does please also confirm bugreport

best, marijus

---

### Post by vmonkey on 2011-02-01
Same here... just have to start computer from recovery. However, I'll try the suggestions you mentioned...

---

