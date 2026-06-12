---
title: "Nvidia crashes again !!! although installed FROM REPO ??? ..."
date: 2013-02-04
forum: Multimedia Software
---

### Post by mind_exploit on 2013-02-04
Hello, everyone :)

Last night my kernel updated to 3.2.0-37 (from 3.2.0-36) - and it updated the headers as well, and when I rebooted - I get purple screen and can't get to login ... !!!

Run a live CD and checked /var/log/dmesg and /var/log/syslog - and on both places it says 

```
nouveau: probe of 0000:01:00.0 failed with error - 22
```

and I got soooo much pi**ed off ... !!!

I assume this happens cause the NVidia driver can't start and it fall-back to the nouveau driver, but it's disabled now from the nvidia xconfig file ... if so - I've encountered this problem so many times before, on different distros ... and I thought that this will never happen again after installed NVidia driver form repo, and not downloading .deb file or source and compiling or something like this ... 
I feel like I'm about to get kernel-update-phobia ... :)

Why is this happening? ... and more important - can you help me fix it? ... cause I can't run the previous kernel versions too :( ... same result - blank purple screen ... 

Info: Toshiba Satellite P855, Nvidia GT640M, driver version - 310, Ubuntu 12.04 64 bit.

---

