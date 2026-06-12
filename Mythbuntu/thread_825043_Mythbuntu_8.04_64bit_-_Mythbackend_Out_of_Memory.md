---
title: "Mythbuntu 8.04 64bit - Mythbackend Out of Memory"
date: 2008-06-10
forum: Mythbuntu
---

### Post by reslip on 2008-06-10
I've been almost successful in getting my Mythbuntu machine in working order. Some tv shows appear to record fine, but after a few recordings the memory in my system decreases to the point where mythbackend is killed by the kernel. Previously I had used the exact same hardware for over a year running Gentoo so I suspect that it is not a hardware issue. It's AMD Sempron 2800+, 512Mb Ram, Hauppauge 350, w/ 1.5Gb swap partition on a 250Gb hard drive. 

My kern.log after a mythbackend crash is as follows:
```
May 20 00:04:01 deception kernel: [360353.657488] ivtv0: All encoder MPG stream buffers are full. Dropping data.
May 20 00:04:03 deception kernel: [360353.657494] ivtv0: Cause: the application is not reading fast enough.
May 20 00:09:08 deception kernel: [360655.454918] ivtv0: All encoder MPG stream buffers are full. Dropping data.
May 20 00:09:09 deception kernel: [360655.454924] ivtv0: Cause: the application is not reading fast enough.
May 20 03:30:11 deception kernel: [372705.539011] ivtv0: All encoder MPG stream buffers are full. Dropping data.
May 20 03:30:11 deception kernel: [372705.539018] ivtv0: Cause: the application is not reading fast enough.
May 20 09:29:23 deception kernel: [394211.676175] mythbackend invoked oom-killer: gfp_mask=0x1201d2, order=0, oomkilladj=0
May 20 09:29:23 deception kernel: [394211.676184] Pid: 18736, comm: mythbackend Tainted: P        2.6.24-16-generic #1
May 20 09:29:23 deception kernel: [394211.676187]
May 20 09:29:23 deception kernel: [394211.676187] Call Trace:
May 20 09:29:24 deception kernel: [394211.676221]  [oom_kill_process+0xf6/0x110] oom_kill_process+0xf6/0x110
May 20 09:29:24 deception kernel: [394211.676236]  [out_of_memory+0x21e/0x260] out_of_memory+0x21e/0x260
May 20 09:29:24 deception kernel: [394211.676255]  [__alloc_pages+0x399/0x3d0] __alloc_pages+0x399/0x3d0
May 20 09:29:24 deception kernel: [394211.676277]  [__do_page_cache_readahead+0xe0/0x210] __do_page_cache_readahead+0xe0/0x210
May 20 09:29:24 deception kernel: [394211.676299]  [xfs:filemap_fault+0x28e/0x570] filemap_fault+0x28e/0x390
May 20 09:29:24 deception kernel: [394211.676315]  [__do_fault+0x6a/0x430] __do_fault+0x6a/0x430
May 20 09:29:24 deception kernel: [394211.676338]  [handle_mm_fault+0x1b2/0x7b0] handle_mm_fault+0x1b2/0x7b0
May 20 09:29:25 deception kernel: [394211.676360]  [do_page_fault+0x1ab/0x840] do_page_fault+0x1ab/0x840
May 20 09:29:26 deception kernel: [394211.676374]  [thread_return+0x3a/0x57b] thread_return+0x3a/0x57b
May 20 09:29:26 deception kernel: [394211.676389]  [sys_futex+0xab/0x140] sys_futex+0xab/0x140
May 20 09:29:26 deception kernel: [394211.676403]  [error_exit+0x0/0x51] error_exit+0x0/0x51
May 20 09:29:26 deception kernel: [394211.676428]
May 20 09:29:26 deception kernel: [394211.676429] Mem-info:
May 20 09:29:26 deception kernel: [394211.676431] Node 0 DMA per-cpu:
May 20 09:29:26 deception kernel: [394211.676435] CPU    0: Hot: hi:    0, btch:   1 usd:   0   Cold: hi:    0, btch:   1 usd:   0
May 20 09:29:26 deception kernel: [394211.676437] Node 0 DMA32 per-cpu:
May 20 09:29:26 deception kernel: [394211.676440] CPU    0: Hot: hi:  186, btch:  31 usd: 155   Cold: hi:   62, btch:  15 usd:  49
May 20 09:29:26 deception kernel: [394211.676444] Active:61345 inactive:46288 dirty:0 writeback:0 unstable:0
May 20 09:29:26 deception kernel: [394211.676446]  free:1196 slab:3612 mapped:14 pagetables:3719 bounce:0
May 20 09:29:26 deception kernel: [394211.676448] Node 0 DMA free:2004kB min:60kB low:72kB high:88kB active:732kB inactive:1048kB present:10944kB pages_scanned:5839 all_unreclaimable? yes
May 20 09:29:26 deception kernel: [394211.676453] lowmem_reserve[]: 0 488 488 488
May 20 09:29:26 deception kernel: [394211.676456] Node 0 DMA32 free:2780kB min:2796kB low:3492kB high:4192kB active:244648kB inactive:184104kB present:500708kB pages_scanned:648454 all_unreclaimable? yes
May 20 09:29:26 deception kernel: [394211.676461] lowmem_reserve[]: 0 0 0 0
May 20 09:29:26 deception kernel: [394211.676464] Node 0 DMA: 12*4kB 149*8kB 48*16kB 0*32kB 0*64kB 0*128kB 0*256kB 0*512kB 0*1024kB 0*2048kB 0*4096kB = 2008kB
May 20 09:29:26 deception kernel: [394211.676471] Node 0 DMA32: 40*4kB 4*8kB 1*16kB 0*32kB 0*64kB 0*128kB 0*256kB 1*512kB 0*1024kB 1*2048kB 0*4096kB = 2768kB
May 20 09:29:26 deception kernel: [394211.676480] Swap cache: add 21699817, delete 21699817, find 1257423/4259897, race 2+7
May 20 09:29:26 deception kernel: [394211.676482] Free swap  = 0kB
May 20 09:29:26 deception kernel: [394211.676483] Total swap = 1461904kB
May 20 09:29:26 deception kernel: [394211.676485] Free swap:            0kB
May 20 09:29:26 deception kernel: [394211.681648] 131008 pages of RAM
May 20 09:29:26 deception kernel: [394211.681651] 3113 reserved pages
May 20 09:29:26 deception kernel: [394211.681652] 618 pages shared
May 20 09:29:26 deception kernel: [394211.681654] 0 pages swap cached
May 20 09:29:26 deception kernel: [394211.681656] Out of memory: kill process 18728 (mythbackend) score 270804 or a child
May 20 09:29:26 deception kernel: [394211.681712] Killed process 18728 (mythbackend)

```

I've also noticed CPU utilization is near 90% when recording shows. With Gentoo and using Hardware MPEG encoding it was closer to 5%.

Any help would be appreciated.

---

### Post by ian dobson on 2008-06-10
Hi,

Do you see anything strange in your mythbackend.log in /var/log/mythtv?

Sounds alot like the problem that I found in my 64Bit backend except I see it with DVB-c (see [http://ubuntuforums.org:80/showthread.php?t=800023](http://ubuntuforums.org:80/showthread.php?t=800023)).

One thing to try is to disable upnp if your not using a upnp client. Just edit your /etc/defaults/mythtv-backend file and change the extra_options line to include -noupnp. the restart the backend.

Regards
Ian Dobson

---

### Post by blackoper on 2008-06-10
another thing to check is if EIT is on. For some reason it always seems to have memory leak issues. if you don't need it and are running dvb cards make sure to disable eit on each card in mythtv-setup for the cards when adding them

---

### Post by superm1 on 2008-06-10
Another thing to consider, make sure you are running on the latest available kernel (-18).  There was a scheduling related bug fixed in -17, and you should make sure to rule out any possible race conditions.

8.04 shipped with -16.

---

### Post by ian dobson on 2008-06-11
> **superm1 said:**
> Another thing to consider, make sure you are running on the latest available kernel (-18).  There was a scheduling related bug fixed in -17, and you should make sure to rule out any possible race conditions.

8.04 shipped with -16.

It looks as if -18 is still held back for 64 bit.

```
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages have been kept back:
   linux-generic (2.6.24.16.18 => 2.6.24.18.20)
   linux-image-generic (2.6.24.16.18 => 2.6.24.18.20)
   linux-restricted-modules-generic (2.6.24.16.18 => 2.6.24.18.20)
   openssh-client (4.7p1-8ubuntu1 => 4.7p1-8ubuntu1.2)
   openssh-server (4.7p1-8ubuntu1 => 4.7p1-8ubuntu1.2)
   ssl-cert (1.0.14-0ubuntu2 => 1.0.14-0ubuntu2.1)
0 upgraded, 0 newly installed, 0 to remove and 6 not upgraded.
```

Regards
Ian Dobson

---

### Post by superm1 on 2008-06-11
> **ian dobson said:**
> It looks as if -18 is still held back for 64 bit.

```
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages have been kept back:
   linux-generic (2.6.24.16.18 => 2.6.24.18.20)
   linux-image-generic (2.6.24.16.18 => 2.6.24.18.20)
   linux-restricted-modules-generic (2.6.24.16.18 => 2.6.24.18.20)
   openssh-client (4.7p1-8ubuntu1 => 4.7p1-8ubuntu1.2)
   openssh-server (4.7p1-8ubuntu1 => 4.7p1-8ubuntu1.2)
   ssl-cert (1.0.14-0ubuntu2 => 1.0.14-0ubuntu2.1)
0 upgraded, 0 newly installed, 0 to remove and 6 not upgraded.
```Regards
Ian Dobson
You might consider using update-manager, or at least trying apt-get dist-upgrade.  Usually things like this are held back if they are introducing "NEW" packages.

---

### Post by tgm4883 on 2008-06-11
You stuff is getting held back because of the random number problem.  You need to do a dist-upgrade because there is a new -blacklist package you need

---

### Post by ian dobson on 2008-06-11
Hi,

Did a apt-get dist-upgrade and now have the updated kernel. 

Thanks for the tip. I always thought a dist-upgrade was for upgrading versions, for example from 7.10 to 8.4.

Regards
Ian Dobson

---

