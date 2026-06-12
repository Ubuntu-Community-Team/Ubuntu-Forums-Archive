---
title: "NDIS Wrapper Question"
date: 2006-01-03
forum: Networking &amp; Wireless
---

### Post by doug.barrett on 2006-01-03
I figured out the make (thanks!) but when I run it, this is what I get when I try to install NDIS:

```
root@dougslaptop:/home/doug/Desktop/ndiswrapper-1.7# make
make -C driver
make[1]: Entering directory `/home/doug/Desktop/ndiswrapper-1.7/driver'
Can't find kernel sources in /lib/modules/2.6.12-9-386/build;
  give the path to kernel sources with KSRC=<path> argument to make
make[1]: *** [prereq_check] Error 1
make[1]: Leaving directory `/home/doug/Desktop/ndiswrapper-1.7/driver'
make: *** [all] Error 2

```

I have put the drivers in the driver folder, so I don't know what I am doing wrong.

Thanks :)

EDIT: Sorry for posting in here, it seems the people in the New Users section are able to help me out.

I didn't post in both sections hoping to get a faster answer, I just realized after I had asked it in the other forum that this one would be the more appropriate one.

Sorry again.

---

