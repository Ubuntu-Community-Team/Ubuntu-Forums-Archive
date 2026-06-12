---
title: "Mythbuntu 8.10 and disk performance problem (NVP: prebuffering pause)"
date: 2008-11-25
forum: Mythbuntu
---

### Post by evilg33k on 2008-11-25
Hi y'all,

After upgrading from a custom installation with Debian woody I find that playing a movie while recording at the same time causes stuttering of the playback. Examining mythfrontend logs show the above message.
I have already changed my playback profile to 'Slim' and this does improve things but after a while the disk led is almost constantly on and stuttering occurs.

Commercial flagging jobs have been disabled.

hdparm test result shows the drive can do +- 60MB/second, seems ok to me.

Only one thing I can come up with is the xfs filesystem. Maybe I should take a closer look at tuning this?


Thank you any help offered.

---

### Post by ian dobson on 2008-11-25
Hi,

What hardware are you using? 60MB/second is not bad but if your writing and reading at the same time you could be thrashing the harddisk quite abit. Maybe try increasing the buffer in mythtv-setup, that might help.

I don't know about xfs, I only use ext3 and YAFFS/JFFS2 (don't ask).

Regards
Ian Dobson

---

### Post by evilg33k on 2008-11-25
> **ian dobson said:**
> Hi,

What hardware are you using? 60MB/second is not bad but if your writing and reading at the same time you could be thrashing the harddisk quite abit. Maybe try increasing the buffer in mythtv-setup, that might help.


Thanks, I'll take a look at the buffer config this evening.

Hardware: 2.4ghz celeron cpu, 300gb maxtor diamondmax hd (sata), hauppage 350 pvr, 512m ram.

This is of course a front-and backend machine and the previous installation handled the disk i/o pretty well.

If I fail to find a solution I'll change the recordings filesystem to ext3 and post the results.

---

### Post by evilg33k on 2008-11-25
This guide looked promising and it seemed to result in less stuttering but not sufficiently:
[http://www.mythtv.org/wiki/index.php/Pvr350]("http://www.mythtv.org/wiki/index.php/Pvr350")

That's it, I'm changing the recordings filesystem to ext3.

---

### Post by evilg33k on 2008-11-26
Changing my /var/lib partition from xfs to ext3 solved my problem.
Prior to that I had done some write tests with dd on xfs and got 77MB/second.   Is this slow?

I don't understand why writes to my xfs filesystem created such an i/o bottleneck on my system?! 

Anyways, I hope this experience will come in handy to others.

---

### Post by ian dobson on 2008-11-26
Hi,

That doesn't make any sense to me, but if that works then OK. 77Mb second isn't that bad, what was the CPU load like?

Maybe xfs causes high CPU load on large writes or one of the logging deamons doesn't like logginf to xfs.

Regards
Ian Dobson

---

### Post by evilg33k on 2008-11-27
Morning,

CPU load was 50% back then and still is now.

I can see now that with xfs the hd led came on in very long bursts while with ext3 it rapidly blinks. I dunno, maybe my hd can't handle large buffer flushes... <grin>

---

