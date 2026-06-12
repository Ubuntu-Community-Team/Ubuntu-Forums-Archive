---
title: "Monitor Out of Range"
date: 2011-03-10
forum: Multimedia Software
---

### Post by capemayal on 2011-03-10
Ubuntu 10.10
Viewwonic VG2030WM
Out of Range H. Frequency 90 khz   V. Frequency 6.0 Hz
Card Ati-All-in-Wonder X800XL PCIE DVI only card.
 
[LIST=1]
[*]Dual Boot with W XP-Pro
[*]No Problems booting into Windows from Dual-Boot Menu
[*]When booting into 10.10, even with recovery mode, I have the black screen with the Out of Range notice.
[*]I am unable to go back this black screen
[*]Ubuntu updates completed yesterday, 3/10
[*]Monitor Worked fine before updats.
[/LIST]I think the only way to accomplish this is to reinstall Ubuntu?
 
Any help would be appreicated.
 
Thanks,
Al

---

### Post by oracle2b on 2011-03-10
[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

To set your screen resolution back to normal, use xrandr like this:

> xrandr -s 0

The "-s" option allows you to specify the size, and the "0" parameter tells xrandr to reset the screen to its default size. You can also specify a resolution, like this:

> xrandr -s 1024x768

or 

> xrandr -s 1024x768 --output auto

---

### Post by capemayal on 2011-03-10
> **oracle2b said:**
> [https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

To set your screen resolution back to normal, use xrandr like this:



The "-s" option allows you to specify the size, and the "0" parameter tells xrandr to reset the screen to its default size. You can also specify a resolution, like this:



or

Thanks for the reply.  

My problem is, that I can't get in Ubuntu at all!  I can get into Windows XP with no problem.

I get stopped at the screen, while trying to get into Ubuntu, that says Out of Range.

Is there a way to fix this from Windows XP?

Thanks,
Al

---

### Post by oracle2b on 2011-03-11
Try connecting another monitor to the computer and see if a gui appears.. you should be able to access a terminal though.

---

### Post by capemayal on 2011-03-12
Thanks, Oracle.
 
I think the card died.
 
Another monitor with DVI showed the same problem.
 
I did start to notice some problems in the Windows OS too.
 
So, I think, at this point, the card is dead.
 
Thanks again,
Al

---

