---
title: "Dell Latitude D-400 Intel Wireless issues..."
date: 2010-12-05
forum: Networking &amp; Wireless
---

### Post by honkytonkzero on 2010-12-05
Hello.  I have a Dell Latitude D-400 laptop.  It has an Intel wireless card, and I've scoured the forums as well as the rest of the internet for months trying to get this to work.  And I've had zero luck.

I can't even name all of the fixed I've tried, I've tried changing software, installing drivers, and have had no luck, with anything.  BUT, most of the fixes I've found online were for different machines, or different wireless cards.  So I'm hoping this thread may get me some results.

Right now, it recognizes that the card is there, but claims that 'wireless is disabled'.  This has been a maddening experience.  I really hope someone can help me.

Also, I've tried Xubuntu, Ubuntu, and now, Lubuntu.  All have given the same results.

HELP!!!

---

### Post by chili555 on 2010-12-05
Please post:```
rfkill list all
```Thanks.

---

### Post by honkytonkzero on 2010-12-05
It said this.

```
user1@user1-Latitude-D400:~$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
user1@user1-Latitude-D400:~$ 


```

---

### Post by chili555 on 2010-12-05
>  Hard blocked: yesThis suggests that the hardware wireless switch on your laptop is switched to 'Off." Can you find the switch and...switch it?

---

