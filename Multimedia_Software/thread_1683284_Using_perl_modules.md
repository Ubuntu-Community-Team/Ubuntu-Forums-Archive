---
title: "Using perl modules"
date: 2011-02-07
forum: Multimedia Software
---

### Post by W29 on 2011-02-07
Hi

I installed the Audio::FLAC::Header module from CPAN.
They are installed properly, but when I run a perl script that loads this module, it gives the next error:
```
Can't locate Audio/Flac/Header.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.10.1 /usr/local/share/perl/5.10.1 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.10 /usr/share/perl/5.10 /usr/local/lib/site_perl .) at testje.pl line 3.
BEGIN failed--compilation aborted at testje.pl line 3.
```
After that, I copied the module folder to all these locations (it was already present in some folders, like etc/perl). But it still doesn't work.
Does someone got any idea how this comes?

Thanks

---

### Post by W29 on 2011-04-24
The problem solved itself. I get no more errors. Weird.. :p

---

