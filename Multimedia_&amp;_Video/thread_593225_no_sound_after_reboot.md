---
title: "no sound after reboot"
date: 2007-10-27
forum: Multimedia &amp; Video
---

### Post by xjgnsdof on 2007-10-27
I sometimes get no sound unless I reboot. Usually, I play games in my XP partition; when I'm done, I boot into Gutsy to do all of my other computing. On the first or second boots, I get no sound in Ubuntu. After a third reboot or so, I finally get sound. What's going on?

---

### Post by xjgnsdof on 2007-10-29
up

---

### Post by xjgnsdof on 2007-10-29
up

---

### Post by xjgnsdof on 2007-11-04
up

---

### Post by xjgnsdof on 2007-11-04
up

---

### Post by xjgnsdof on 2007-11-09
up

---

### Post by RockTonic3 on 2007-11-09
hah apparently nobody wants to help anyone with sound issues...  i can't find someone to help me with a similar problem.  no sound all of a sudden, even if i reboot.

---

### Post by christopherZA on 2007-11-09
Hi

If it helps I was also experiencing this problem and saw I had a bit of pebkac ... Yesterday I installed my soundblaster and today only my onboard was working. After investigating I saw I never set the sound in the System > Preferences > Multimedi Systems Selecter

I also know that one of the guys at work messed up his kernel and he could not get his sound working until we reinstalled his kernel - apt-get install linux-headers-2.6.22-14

run dmesg on bootup to check whats happening.

---

