---
title: "HD4870 video card"
date: 2008-06-27
forum: Multimedia Software
---

### Post by jrharvey on 2008-06-27
I was wanting to get one of these beast and im worried about compatability with linux. Has anyone tried one yet? I know they are BRAND NEW but i dont want to sacrifice Ubuntu for a video card.

---

### Post by jrharvey on 2008-06-27
bump

---

### Post by jrharvey on 2008-06-27
anyone??? BTW how are the newer ati drivers doing these days with linux?

---

### Post by markbuntu on 2008-06-27
The new ati drivers are working pretty good for a lot of people but still some problems with compiz. As far as the latest driver release, 8.6, the HD 4870 is not even listed and the HD3870x2 or whatever is listed as not supported though the HD3870 is. So, in a nutshell, this HD4870 may push you over the bleeding edge and into the dark abyss of non-supported new stuff hell.

You might try talking to ATI to find out what the 8.6 driver will support on your card.

---

### Post by Melcar on 2008-06-27
The cards work:

[http://www.phoronix.com/scan.php?page=article&item=ati_radeonhd_4850&num=1]("http://www.phoronix.com/scan.php?page=article&item=ati_radeonhd_4850&num=1")

... but 3D performance is lacking.  However, given the rate of improvement of fglrx I would presume proper 3D functionality two driver releases from now.

---

### Post by jrharvey on 2008-06-30
Thank you, what a great find. I dont really care about how well it performs in ubuntu because i do all my work in windows due to the 3d programs i use. +1 thanks for you :)

---

### Post by G_ALAHAD on 2008-07-14
if anyone knows a step by step howto. I would appreciate it.

---

### Post by Janusz11 on 2008-07-14
The guys over at Phoronix said in their HD4870 test that the card worked "out of the box" on Ubuntu. But no luck here. When I install the new Catalyst v8.6 my whole system crashes/freezes when I startx (thats under Arch Linux & Zenwalk). My screen goes all black, the lights of my keyboard go off and I have to push the reset button of my box to start it again.

I couldn't try the card on Ubuntu since the latter doesn't find my SATA HD and I couldn't install it.

---

### Post by cristo-father on 2008-07-14
> **Janusz11 said:**
>  my whole system crashes/freezes when I startx (thats under Arch Linux & Zenwalk). My screen goes all black, the lights of my keyboard go off and I have to push the reset button of my box to start it again.

After installing catalyst 8.6 i cannot even start ubuntu.

---

### Post by markbuntu on 2008-07-14
Which directions did you follow? ATI has tested the 4870 with their driver 8.6 and it is known to work. I just found this out a few days ago.

The directions here should work for you, follow method 2:

[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)

If you are running 64 bit Hardy be sure to follow the special directions for 64 bit.

Also, run update manager after you install it, there seem to be some restricted kernel updates for this driver at least it apperaed that way to me.

---

### Post by cristo-father on 2008-07-26
It worked.

---

### Post by microft on 2008-11-09
How would this work on 64 bit intrepid?

---

### Post by Torqumada286 on 2008-11-09
> **microft said:**
> How would this work on 64 bit intrepid?

Well, I was just surprised.  After having lots of problems getting 3d acceleration with my 4870 with Hardy, loaded up Intrepid, fixed a few errors and then was able to play City of Heroes for the first time in Ubuntu.  So, from my experience, I am going to say it works great.  :D

Torqumada

---

### Post by microft on 2008-11-10
> **Torqumada286 said:**
> Well, I was just surprised.  After having lots of problems getting 3d acceleration with my 4870 with Hardy, loaded up Intrepid, fixed a few errors and then was able to play City of Heroes for the first time in Ubuntu.  So, from my experience, I am going to say it works great.  :D

Torqumada

Are you able to play videos without flickering?
If so, can you give me some insight to your xorg.conf?

What drivers did you use? The one from the ubuntu repositories?


Thanks!

---

### Post by microft on 2008-11-14
There is a new ati driver out: 8.11

---

