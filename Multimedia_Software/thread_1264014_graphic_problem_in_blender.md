---
title: "graphic problem in blender"
date: 2009-09-11
forum: Multimedia Software
---

### Post by imri on 2009-09-11
Hi guys,
I'm using Ubuntu 9.04 (and I'm completely clueless), and I've encountered some graphic problems when using certain applications.
In the attached file there is a screenshot of how Blender's opening screen looks on my computer.
I also have some weird graphic problem with wrokrave ([http://www.workrave.org/welcome](http://www.workrave.org/welcome)), but its harder for me to explain it precisely.

can you please help me?
thanks

---

### Post by overdrank on 2009-09-11
> **imri said:**
> Hi guys,
I'm using Ubuntu 9.04 (and I'm completely clueless), and I've encountered some graphic problems when using certain applications.
In the attached file there is a screenshot of how Blender's opening screen looks on my computer.
I also have some weird graphic problem with wrokrave ([http://www.workrave.org/welcome](http://www.workrave.org/welcome)), but its harder for me to explain it precisely.

can you please help me?
thanks

Hi and welcome, what is the model of the graphics card and the driver you are using? You may use the command ```
lspci | grep VGA
``` to identify your hardware.

---

### Post by imri on 2009-09-11
I'm using:
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)

I also should have mentioned that I had followed the instructions for Optimal configuration in **[http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582)** but it did not help.

---

### Post by imri on 2009-09-14
anyone, please?
can it be a problem in python tkinter?

---

### Post by rexo on 2009-09-16
same problem here :-(

here is my output of "lspci | grep VGA":
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)

w or w/o compiz the result is the same.

---

### Post by Mach1723 on 2009-09-16
Intel is notorious for bad open GL support thus meaning bad support for blender, i am not familiar with intel though and am currently having toubles with nvidia drivers but you could try and find a way to get blender to run in software mode for Open GL it would be slow but better than nothing.

---

### Post by rexo on 2009-09-16
yeap, that helped. I'll give it a try. The code is:

  LIBGL_ALWAYS_SOFTWARE=1 blender

see also:
[http://bbs.archlinux.org/viewtopic.php?id=71063](http://bbs.archlinux.org/viewtopic.php?id=71063)

---

### Post by imri on 2009-09-17
worked for me,
thanks guys

---

### Post by gabz8472 on 2009-09-29
Guys, this solution worked for me with one minor drawback. I need to run it everytime I start up and my laptop. Is there a way to make it permanent? I'm using an MSI Wind U100 laptop.

---

### Post by Raik.48 on 2009-10-05
Hi!

I am having same problem of the graphics in my ubuntu 9.04 desktop and the graphics is Intel X4500HD and in command line it says:
00:02.0 VGA compatible controller: Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03).

What may be the problem. Can anyone tell me?

Thanks

---

### Post by Raik.48 on 2009-10-05
that worked.

Thanks.

---

