---
title: "Router setup?"
date: 2006-05-05
forum: Networking &amp; Wireless
---

### Post by nayrt on 2006-05-05
Hi

I'm trying configure a linux PC as a router to direct connect 2 solaris systems for testing purposes!

I'm not at all familiar with linux networking..and am having no success so far!

Is it possible to setup such a router by connecting the systems direct via cross over cables? 

Setup So far:
  Linux Box (3 NICS!)
     |
      --- eth0 (10.2.6.22) ----> Solaris Box 1 ip 10.2.6.31
      --- eth3 (10.1.7.19) ----> Solaris Box 2 ip 10.1.7.30
      --- (eth1 ----> Public Network)

Any ideas????

---

### Post by mips on 2006-05-05
Look into IPv4 Forwarding...

The following is probably overkill for you needs, [http://www.ubuntuforums.org/showthread.php?t=111972](http://www.ubuntuforums.org/showthread.php?t=111972)

---

