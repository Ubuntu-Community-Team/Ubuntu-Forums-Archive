---
title: "Inconsistency detected by ld.so"
date: 2011-11-29
forum: Multimedia Software
---

### Post by lordbah on 2011-11-29
Today Miro and Banshee bomb when starting up.

Inconsistency detected by ld.so: ../sysdeps/x86_64/dl-machine.h: 466: elf_machine_rela_relative: Assertion `((reloc->r_info) & 0xffffffff) == 8' failed!

Anyone know what causes this?

They worked a couple of days ago. This is 64-bit Ubuntu 11.10 with 24GB RAM. I've been taking all of the updates in oneiric-proposed so it could be something in there. Is there a time-sorted list of packages installed which is more concise than /var/log/dpkg.log?

I don't know whether this is related but over the last two days I've also been seeing a lot of "Aw, snap!" from Chrome, but a reload successfully redraws the page.

So far I've only found a few references on the web and they lead to reinstalling Ubuntu, which seems like a crap shoot to me, just hoping that something went wrong during an install and won't go wrong again next time.

---

### Post by gordintoronto on 2011-11-29
[http://www.google.com/support/forum/p/chat/thread?tid=10ffe01c3a4779f5&hl=en&fid=10ffe01c3a4779f500048e4e32e57ab6](http://www.google.com/support/forum/p/chat/thread?tid=10ffe01c3a4779f5&hl=en&fid=10ffe01c3a4779f500048e4e32e57ab6)

The part which begins, "Then this is probably Debian bug #588582." has been reported as solving this problem.

---

### Post by lordbah on 2011-11-30
I wasn't seeing the ldd "not found" symptom, so I don't know that those steps would be helpful.

But that's moot at this point since the system no longer boots. Support suspects a memory issue. When that gets resolved, then I'll check whether this problem still exists.

Thanks.

---

