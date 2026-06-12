---
title: "Another oddity"
date: 2012-08-21
forum: Networking &amp; Wireless
---

### Post by Lloydb39 on 2012-08-21
My new computer has 8 gigs of memory, and the bios recognizes it, but sysinfo in Ubuntu 11.10 says only 2988 megs of memory total. Anybody know why?

---

### Post by drmrgd on 2012-08-21
Any chance you're running a 32.bit version of Ubuntu instead of 64-bit?  You can run the following to find out:

```
uname -a
```

Could be something else, but that's a pretty good first place to look

---

### Post by Lloydb39 on 2012-08-21
It says something about i686 athlon  i386 gnu'linux. is that a clue?

---

### Post by drmrgd on 2012-08-22
Yes, it looks like you are running the 32-bit version of Ubuntu, Which is not going to address all of that memory.  Although it's a pain as it will require a full re-install, it would be worthwhile to upgrade to 64-bit in order to utilize the extra RAM in you system.

---

### Post by Kirk Schnable on 2012-08-22
For the record, this is not a Ubuntu limitation, but a 32-bit limitation.

[http://en.wikipedia.org/wiki/RAM_limit#32-bit_x86_RAM_limit](http://en.wikipedia.org/wiki/RAM_limit#32-bit_x86_RAM_limit)

Kirk

---

