---
title: "Simple wireless problem"
date: 2010-10-17
forum: Networking &amp; Wireless
---

### Post by Sequoia Bird on 2010-10-17
My wireless basically just quit on me in v10.04. I saw there was a 10.10, so I downloaded it hoping that it would fix my problem.

I have a Dell inspiron 1564, the wireless is enabled according to the network manager, when I type "rfkill list" into terminal it says wireless is

hard blocked: no
soft blocked: yes

My wifi card is a broadcom BCM4312... The additional driver I have for it is Broadcom STA wireless driver... The ethernet cable will let me have internet with absolutely no trouble. I tried "connect to hidden wireless network" with searching but no finding...

Thanks for the help! I've been at this all day and i'm starting to feel really stupid.

---

### Post by johnnytm on 2010-10-17
try this ```
 rfkill unblock all 
```

---

### Post by Sequoia Bird on 2010-10-17
Perfect, it took a little bit of poking around after but it worked. Thanks!

---

### Post by johnnytm on 2010-10-18
Good to hear, glad it worked.

---

### Post by TBABill on 2010-10-18
Is that a permanent fix or does it require being done every reboot?

---

### Post by johnnytm on 2010-10-18
if it is still requiring it on reboot there is a command to add it to rfkill conf . I just have to find it again, but will post it as soon as i find it. I like to try and make sure I'm not just adding to conf files from memory all the time.lol

---

### Post by johnnytm on 2010-10-18
I believe it to be a permanent fix. After checking my rfkill bin bash file it changes that. which does which does not revert after reboot. the soft block you were getting was software related, hard blocks are harder to deal with. Let me know if you are still having problems tho. there are a couple of other things that can be checked.

---

