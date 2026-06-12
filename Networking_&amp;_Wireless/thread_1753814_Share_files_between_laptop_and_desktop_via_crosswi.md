---
title: "Share files between laptop and desktop via crosswire cable?"
date: 2011-05-09
forum: Networking &amp; Wireless
---

### Post by Neo40 on 2011-05-09
Hi,

I did try to share files via my router between my desktop pc and my laptop. It works fine, but I find it has a slow transfer rate (It took almost 1 hour to transfer 7 Gb).
So, is it possible to use a crosswire cable and connect it directly to PCs without using my router?
-Is the transfer rate will be faster?
-do I still need to use Samba to communicate with my 2 machines?

Thanks

---

### Post by WthIteh on 2011-05-09
If your desktop and laptop connections to router are wired, then you would not sense any major performance upgrade by using cross-wire direct connection probably.
But it maybe due to other misconfigurations.
Just to be sure you could test a file transfer without Samba (for example using netcat) to check the real performance.
For testing you could run
```
nc -l 1234 > file.ext
```
on one machine (server) and then run
```
nc <server-machine-IP-address> 1234 < file.ext
```
on another machine (client) to transfer the "file.ext" file.

---

