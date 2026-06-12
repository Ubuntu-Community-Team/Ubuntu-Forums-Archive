---
title: "qjackctl version 0.2.21"
date: 2007-01-30
forum: Multimedia &amp; Video
---

### Post by DonQuichotte on 2007-01-30
Hey guys

I'm attempting to install the very newest version of qjackctl. Old versions don't support FreeBoB, which I have succeeded to install and configure properly in order to set up my Edirol-FA101 for recording. 

Now, my problem is the following: 

I have downloaded a package called "qjackctl_0.2.21-1_i386.deb".

when I'm doing:

$dpkg -i qjackctl_0.2.21-1_i386.deb

my dpkg produces the following output:

> [....]
dpkg: dependency problems prevent configuration of qjackctl:
 qjackctl depends on libasound2 (>> 1.0.12); however:
  Version of libasound2 on system is 1.0.11-7ubuntu3.
[....]



Of course, I have configured, compiled and installed the newest version of libasound. Unfortunately, I was unable to find out how I can configure dpkg to link qjackctl to these libraries.

Buildin qjackctl is not an option - I've been trying that for 4 days and have made a post in here - noone has been able to help me so I guess there is no solution to this problem.

Can anyone give me a hint there?

Thanks a lot.

-DQ

---

