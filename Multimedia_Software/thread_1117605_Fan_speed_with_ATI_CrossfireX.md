---
title: "Fan speed with ATI CrossfireX"
date: 2009-04-06
forum: Multimedia Software
---

### Post by Karsa on 2009-04-06
Hello

I've got a noisy little bugger in one of my HD4850's. I'm wondering if there's a way to control the fan speed of the second card in a crossfire chain?

Manually adjusting the fanspeed of the first card with aticonfig is no problem, it works perfectly. However, when issuing the same command for the second card in the chain aticonfig gives me an error and no adjustment is done. 

Command issued:
```

aticonfig --pplib-cmd "set fanspeed 1 65"

```


The error is as follows:

```
PPLIB command execution has failed!
ati_pplib_cmd: execute "set" failed!
```

Thanks in advance.

---

### Post by greenone333 on 2011-10-01
What i did to solve this issue was the following aticonfig command

aticonfig --pplib-cmd 'set fanspeed all 75'

Have Fun :popcorn:

---

### Post by Ken UK on 2011-10-03
I'm guessing you have solved this problem (I have the same problem and might try this) but the only way I found to fudge it is to go into the BIOS at bootup, switch which PCI slot boots first then save and reboot. I then go into BIOS again and switch them back around to the original order. What I stumbled across is that when it starts up a second time the fans calm down. I have to do this everytime I start my computer up, its things like this that bug me about Linux, oh the things I do for it....

---

### Post by Trax007 on 2011-12-12
I have this same problem, aticonfig --pplib-cmd 'set fanspeed all 75' did not fix the problem for me either. I've looked all over for a solution but I just can't find anything that works.

---

