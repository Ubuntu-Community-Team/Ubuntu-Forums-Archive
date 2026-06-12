---
title: "jack problem"
date: 2006-09-23
forum: Multimedia &amp; Video
---

### Post by Phreaker on 2006-09-23
So I want to try ardour.
When I execute it ,it tells me that it needs jack
So i apt-get jack ,but it tells me: 

This is jack 3.1.1 (C)2004 Arne Zellentin <zarne@users.sf.net>
Access of CD device /dev/cdrom resulted in error: Input/output error

What should i do?

---

### Post by IanW on 2006-09-23
The jack you apt-got is a CD ripper, _not_ the sound driver you wanted.

The "JACK Audio Connection Kit" is in the repos as "jackd"

---

### Post by Phreaker on 2006-09-23
Thanks.now it works

---

