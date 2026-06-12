---
title: "wireless printer works, but scanner doesn't after 10.04 upgrade"
date: 2010-04-30
forum: Networking &amp; Wireless
---

### Post by kelver69 on 2010-04-30
I'm stumped... 
I had 9.10 working flawlessly with my Brother MFC490-CW Wireless printer/scanner, but after upgrading to 10.04 LTS final, I cannot scan... I can print fine, but "no device detected" with xsane (or any other scanning app).  I've tried reinstalling xsane... I've tried reinstalling my Brother drivers, but to no avail.  I can print, but not scan.   Any help would be greatly appreciated.  I've also tried running xsane as root, but got same result.

---

### Post by sageros on 2010-05-31
Hi Kelver, 

I faced the same problem with my Samsung CLX-3170. Printig is fine, but scanning fails with "no device detected". 

I detected, that the the drivers from the manufactor failed to work with glibc-2.11. This could also be the case with other 3rd party drivers. 

Just run "xsane" from the command line and watch for error messages. If you see something like 
```
version GLIBC_2.0 not defined in file libc.so.6 with link time reference
```my hack will propably work for you. 

I described my solution (in german) at [http://forum.ubuntuusers.de/post/2507810/](http://forum.ubuntuusers.de/post/2507810/)
but the shell commands are all english. So maybe it is helpful for you.

---

