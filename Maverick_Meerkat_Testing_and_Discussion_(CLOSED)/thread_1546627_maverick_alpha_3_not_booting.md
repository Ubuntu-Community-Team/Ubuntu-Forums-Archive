---
title: "maverick alpha 3 not booting"
date: 2010-08-05
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by tiamat1 on 2010-08-05
Hi there. 

I have upgraded a perfectly working lucid with 2.6.35 kernel from ppa to maverick alpha 3 and the system does not boot. Installing itself with no prblems. Clean install of alpha 3 - the same - does not boot. LiveCD working fine. Everything 64bit.

The system shows a blank screen when an Ubuntu splashscreen should appear and HDD stops reading anything. After several seconds the monitor goes blank. Have waited for something like 20 minutes and nothing.

System: Athlon X2 250 - 3GHz, Gigabyte GA-someting on AMD 780G (with IGP), no external graphics, 4GB RAM, Samsung f3 500GB ext4.

---

### Post by cariboo on 2010-08-05
Can you start in recovery mode? If you can once you have logged in, type:

```
sudo service gdm start
```

to see if that will take you to the desktop. i had the same problem several times last week, the above command always worked.

---

### Post by tiamat1 on 2010-08-05
Problem solved, don't actually know why.

I pressed several times ESC key while booting and the system just started  smoothly. 

Next couple of times everyting worked without ESC just like normal booting.

THX for the idea of recovery mode (that's why I pressed ESC).

---

### Post by cariboo on 2010-08-05
You have to press the shift key in order to get to the grub2 menu.

---

