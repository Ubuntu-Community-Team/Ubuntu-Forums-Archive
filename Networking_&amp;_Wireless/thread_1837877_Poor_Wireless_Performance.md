---
title: "Poor Wireless Performance"
date: 2011-09-02
forum: Networking &amp; Wireless
---

### Post by Daouuu on 2011-09-02
Hello,

My problem is weak wireless signal strength using Ubuntu.  Using the same laptop running Windows XP I usually get 2-3 bars more on the signal meter.  I know this isn't just how the software displays the signal because generally if I can't get a signal with Ubuntu I boot into Windows and I have 2-3 bars.  Also while in Ubuntu I frequently cannot connect to a 2 bar signal or less whereas in Windows it will connect to 1 bar no problem.  I should mention I have no problem connecting with a strong signal.

I travel for work so I'm in hotels a lot and I'm almost always forced to use Windows do to the weak signal.  I really despise Windows so if anybody knows a fix for this it would be great.  

I'm using an Asus laptop with Intel Pro/Wireless 3945.  I'm running 11.04 but this problem surfaced somewhere around 9.04, I can't remember for sure.

---

### Post by praseodym on 2011-09-02
Have a look at this thread:

[http://ubuntuforums.org/showthread.php?t=1837729](http://ubuntuforums.org/showthread.php?t=1837729)

---

### Post by Daouuu on 2011-09-03
Thanks I'll try that and see what happens.

---

### Post by Daouuu on 2011-09-03
Well that didn't seem to work. Using Windows I moved to a distance where I was down to a 2 bar signal. I then rebooted in Ubuntu and it didn't even pick up the signal at all.

---

### Post by praseodym on 2011-09-04
Try to update your driver:


```
sudo apt-get install linux-backports-modules-cw-2.6.39-natty-generic
```
and reboot

---

### Post by josephmills on 2011-09-04
best $40 I spent in a while 
[http://www.google.com/products/catalog?oe=utf-8&rls=org.mozilla:en-US:official&client=firefox-a&q=alfa+2000mw&um=1&ie=UTF-8&tbm=shop&cid=3368611088902792917&sa=X&ei=kmhjTviuAsLr0QHm9vy3Cg&ved=0CEQQ8gIwAg](http://www.google.com/products/catalog?oe=utf-8&rls=org.mozilla:en-US:official&client=firefox-a&q=alfa+2000mw&um=1&ie=UTF-8&tbm=shop&cid=3368611088902792917&sa=X&ei=kmhjTviuAsLr0QHm9vy3Cg&ved=0CEQQ8gIwAg)

---

### Post by Daouuu on 2011-09-04
> **praseodym said:**
> Try to update your driver:


```
sudo apt-get install linux-backports-modules-cw-2.6.39-natty-generic
```
and reboot

Thank, but this is the driver I'm currently using. That or a new laptop, this one is almost 5 years old now. I hope the newer hardware doesn't have the same issue.

---

### Post by Daouuu on 2011-09-04
> **josephmills said:**
> best $40 I spent in a while 
[http://www.google.com/products/catalog?oe=utf-8&rls=org.mozilla:en-US:official&client=firefox-a&q=alfa+2000mw&um=1&ie=UTF-8&tbm=shop&cid=3368611088902792917&sa=X&ei=kmhjTviuAsLr0QHm9vy3Cg&ved=0CEQQ8gIwAg](http://www.google.com/products/catalog?oe=utf-8&rls=org.mozilla:en-US:official&client=firefox-a&q=alfa+2000mw&um=1&ie=UTF-8&tbm=shop&cid=3368611088902792917&sa=X&ei=kmhjTviuAsLr0QHm9vy3Cg&ved=0CEQQ8gIwAg)

Ya, something like that might be the answer.

---

