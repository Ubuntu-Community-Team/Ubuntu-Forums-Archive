---
title: "mythtv reports less swap area available"
date: 2010-12-31
forum: Mythbuntu
---

### Post by sami8519 on 2010-12-31
Hi,

My problem is that mythtv reports it has 3.4GB of swap available to it although I have close to 12GB available swap on my system, As you can see here:

root@myth:~# swapon -s
Filename                                Type            Size    Used    Priority
/dev/sda6                               partition       6034428 232     -1
/dev/sda9                               partition       5900284 0       -2

So my question gentlemen is how I can make mythtv uses more swap area then he is doing right now because I sometimes run out of memory(2GB RAM) and swap.

Thanks and best regards
Sami

---

### Post by stevanbt on 2010-12-31
Hi,
I don't know where your swap space is going, but I thought the rule of thumb was to have swap space twice the size of your physical RAM.  Otherwise your server will be doing an awful lot of disk IO using the swap space.

What do you get from

```
free
```

Thanks, Steve.

---

### Post by sami8519 on 2010-12-31
Hi,

Here is the output of free:

```
root@myth:~# free
             total       used       free     shared    buffers     cached
Mem:       2059680     892608    1167072          0      31876     608700
-/+ buffers/cache:     252032    1807648
Swap:     11934712          0   11934712

```

Thanks
Sami

---

### Post by ozybushwalker on 2011-01-03
If you are running a 32 bit version of an application then the application can't grow to use more than about 3GB of RAM, hence its unlikely to want to use more than about 3GB of swap (and then only if the application is completely non resident).

If you 12GB of swap and are running out then you will need to look for something other than a single application growing too large.

Are you able to reproduce the problem of running out of swap space?

---

### Post by sami8519 on 2011-01-04
> **ozybushwalker said:**
> If you are running a 32 bit version of an application then the application can't grow to use more than about 3GB of RAM, hence its unlikely to want to use more than about 3GB of swap (and then only if the application is completely non resident).

If you 12GB of swap and are running out then you will need to look for something other than a single application growing too large.

Are you able to reproduce the problem of running out of swap space?

Thanks mate for your reply. Now it seems to be working relatively well with memory usage peak around half the RAM size. Maybe it is due to the fact that I installed mythbuntu on a very small HDD space and watching livetv especially HD channels was excessive. Now all livetv recordings are shifted into an external HDD and is working good albeit  the usual video frame buffering failed many times problem which I noticed it to be a channel specific and does not have anything to do with RAM or HDD,....etc

Thanks again and regards
Sami
i

---

