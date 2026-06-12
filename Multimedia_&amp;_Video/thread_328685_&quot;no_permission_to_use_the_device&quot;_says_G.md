---
title: "&quot;no permission to use the device&quot; says GnomeBaker"
date: 2006-12-31
forum: Multimedia &amp; Video
---

### Post by blunile on 2006-12-31
no body seems to know what's the problem that i have ??

I can't burn CDs with the gnome baker, it give that error message about "no permission to use cd writing device " and "unsolved issues with Linux kernel 2.6 ....  what's that ???

When I used k3b , it gave me the same exact error ??!!!!

How can i fix this ???

---

### Post by Choxo on 2006-12-31
run it as root:
```

sudo gnomebaker

```

---

### Post by blunile on 2006-12-31
**It still doesn't work**

I use k3b now , but still no change, when i try to write a cd the following error arrives 
> Cdrecord have no permissin to open the device
you may use k3bsetup2 to solve this problem 



---

### Post by blunile on 2007-01-01
Can somebody help me, I can't get permission to open my cd writer device  ](*,) !!!!!!

---

### Post by mervg on 2007-01-25
I have the exact same problem, but only with the external drive. I can burn audio to the internal drive, and can play cds in the external drive.  Can't find a solution. I've even tried chown/chgrp on the drive & cdrecord.  If anyone has an idea, post it on here, please.  I'm not dead in the water, but it's frustrating.:-$

---

### Post by PatrickPizinho on 2007-01-27
Try this...
k3b > settings > configure k3b > Programs > User Parameters
there type in dev=/dev/cdrw in the line cdrecord

it worked on my notebook

---

### Post by EisenPM on 2007-02-06
> **PatrickPizinho said:**
> Try this...
k3b > settings > configure k3b > Programs > User Parameters
there type in dev=/dev/cdrw in the line cdrecord

it worked on my notebook

this worked for me! thanks a lot!

---

