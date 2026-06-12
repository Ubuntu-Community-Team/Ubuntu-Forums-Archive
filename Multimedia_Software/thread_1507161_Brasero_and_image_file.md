---
title: "Brasero and image file"
date: 2010-06-11
forum: Multimedia Software
---

### Post by Linuxforall on 2010-06-11
Unable to burn to an image file with brasero, trying to save to disk gives error, anyone else experiencing this, gnomebaker works perfectly.

---

### Post by labinnsw on 2010-06-13
What is the error?

---

### Post by Linuxforall on 2010-06-13
Doesn't specify, try burning to ISO and you will see it fail and a save to log but there is no such log that I can find on my system. This bug is also listed on Launchpad.

---

### Post by mc4man on 2010-06-13
You could try using this ppa to replace some packages - can't say here as to how it will do 

[https://launchpad.net/~brandonsnider/+archive/cdrtools](https://launchpad.net/~brandonsnider/+archive/cdrtools)

(gave up on linux burning apps a long time ago - only use Imgburn in wine which is always perfect for all media and tasks

---

### Post by Linuxforall on 2010-06-13
> **mc4man said:**
> You could try using this ppa to replace some packages - can't say here as to how it will do 

[https://launchpad.net/~brandonsnider/+archive/cdrtools](https://launchpad.net/~brandonsnider/+archive/cdrtools)

(gave up on linux burning apps a long time ago - only use Imgburn in wine which is always perfect for all media and tasks

Thanks mac4man, I use gnomebaker and it works fine, in Windows world I only used Imgburn as its the most reliable and least bloated of all burning apps there. I will check out this solution or continue to use gnomebaker till Brasero gets updated.

---

### Post by claracc on 2010-06-27
I have had the same problem with brasero. I tried to burn to a CD disk an iso image with brasero, at low speed, 10X and 16X, but at the end, the burn fails (two CD disks ruined unless I used simulate option, sometimes it gives the error at the end of simulation and sometimes at the end of the real recording) without any specific error:
Session error : unknown (brasero_burn_record brasero-burn.c:2811).

I have karmic Koala in my laptop and in the past, I could burned images to disk with brasero, so I think it can be some of the last updates.

I can burn audio CDs with adding files menu (using brasero 2.28.2 and ubuntu kernel 2.6.31-22), but the optical drive rotates doing a lot of noise ¿¿??.

I installed K3b (my desktop is gnome) and it burns images to disk perfectly well, also the rotation of optical drive is silent when it burns.

---

