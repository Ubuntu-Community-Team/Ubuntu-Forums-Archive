---
title: "KWorld ATSC-110 driver needs update"
date: 2006-09-29
forum: Multimedia &amp; Video
---

### Post by wz2b on 2006-09-29
I am on Ubuntu 6.0.6 using the kernel 2.6.15.27-686.  Unfortunately, the saa7134 driver does not have support for my TV card, a KWorld ATSC-110.

The latest version of the saa7134 driver that I could find DOES have support for this board; the problem is, it is using kernel mutexes rather than semaphores, so it won't compile against ubuntu's 2.6.15-27 unless I modify it to not use kernel mutexes.

I'm not sure what to do.  My concern with developing a patch for the new driver is that there may be other differences than mutexes.  I don't really want to build a custom kernel because I don't want to live too far outside of the ubuntu packaging system.

---

### Post by pseudonym on 2006-09-29
You probably already thought of this, but is the card supported in later kernels from kernel.org? There are plenty of users who run such kernels without issues, myself included (2.6.17).

That's what I started doing to get my tv card working, back in the days of kernel 2.6.12, about a year ago. Someone had written a patch for it at linuxtv.org , and I was good to go.

---

