---
title: "high hardware irq cpu times with linux-rt"
date: 2009-05-21
forum: Multimedia Software
---

### Post by sharkcohen on 2009-05-21
This system is at idle.  This can't be normal.  Has anyone else seen this?  I'm running 9.04.

```

top - 23:00:18 up 3 min,  4 users,  load average: 0.44, 0.29, 0.11
Tasks: 287 total,   2 running, 285 sleeping,   0 stopped,   0 zombie
Cpu0  :  7.6%us,  2.0%sy,  0.0%ni, 89.4%id,  0.3%wa,  0.3%hi,  0.3%si,  0.0%st
Cpu1  :  0.7%us,  0.3%sy,  0.0%ni,  0.0%id,  0.0%wa, 99.0%hi,  0.0%si,  0.0%st
Cpu2  :  0.0%us,  0.0%sy,  0.0%ni, 25.0%id,  0.0%wa, 75.0%hi,  0.0%si,  0.0%st
Cpu3  :  0.0%us,  0.0%sy,  0.0%ni, 24.9%id,  0.0%wa, 75.1%hi,  0.0%si,  0.0%st
Cpu4  :  4.3%us,  1.3%sy,  0.0%ni,  0.0%id,  0.0%wa, 94.0%hi,  0.3%si,  0.0%st
Cpu5  :  0.0%us,  0.0%sy,  0.0%ni, 24.9%id,  0.0%wa, 75.1%hi,  0.0%si,  0.0%st
Cpu6  :  0.0%us,  0.0%sy,  0.0%ni, 24.9%id,  0.0%wa, 75.1%hi,  0.0%si,  0.0%st
Cpu7  :  0.0%us,  0.0%sy,  0.0%ni, 24.9%id,  0.0%wa, 75.1%hi,  0.0%si,  0.0%st
Mem:   3011144k total,   755164k used,  2255980k free,    14928k buffers
Swap:  2931852k total,        0k used,  2931852k free,   299032k cached

sharkcohen@sharkdesk:~$ uname -a
Linux sharkdesk 2.6.28-3-rt #12-Ubuntu SMP PREEMPT RT Fri Apr 17 10:09:12 UTC 2009 x86_64 GNU/Linux
```

---

### Post by sharkcohen on 2009-05-21
Anyone running ubuntustudio or just linux-rt want to pop into top real quick and see if this is what you see?  Would appreciate it.

---

### Post by sharkcohen on 2009-05-23
Something is definitely amiss.  I've compiled my own rt kernel against 2.6.29.4, and the new kernel is not doing this.

---

### Post by lorenzo.chiesi on 2009-06-11
Hi, 

I'm in your same situation running ubuntu 9.04 with legacy rt kernel on dual core laptop

htop show the second CPU at 100%...
top show the id% of the second CPU at about 86%

It seems that IRQ process are all scheduled by the second CPU fully take all its time...

You say that with self compiled kernel you have fixed the problem...Please can you send me some information about this solution... 
Wath source have you compiled?
Wath option have you set?

Many thanks

---

