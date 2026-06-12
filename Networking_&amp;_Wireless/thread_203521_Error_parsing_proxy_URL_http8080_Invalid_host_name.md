---
title: "Error parsing proxy URL http://:8080/: Invalid host name"
date: 2006-06-25
forum: Networking &amp; Wireless
---

### Post by csscll on 2006-06-25
When I try to do a 

wget [http://robotgeek.org/eu/easyubuntu-3.0.tar.gz](http://robotgeek.org/eu/easyubuntu-3.0.tar.gz)

I get the following error message 

Error parsing proxy URL [http://:8080/:](http://:8080/:) Invalid host name

Any ideas? I'm a newbie. Thanks.

---

### Post by bscbrit on 2006-06-25
Try to deselect any proxy settings that you might have made.  Use System -> Preferences -> NetworkProxy  and make sure that you have Direct connection to the Internet selected.  Let me know if this solves the problem.

Can you browse the web using Firefox, Epiphany or whatever?  Has this problem only just started occuring and, if yes, what were you doing just before it occurred?

---

### Post by csscll on 2006-06-26
That worked. Brilliant. Thanks a lot.

---

### Post by bscbrit on 2006-06-26
Glad the problem is solved.  See you around.

---

### Post by mkquist on 2006-08-17
been having the same problem with [http://packages.freecontrib.org/ubuntu/plf/pool/dapper/i386/non-free/w32codecs/w32codecs_20060611-1plf1_i386.deb](http://packages.freecontrib.org/ubuntu/plf/pool/dapper/i386/non-free/w32codecs/w32codecs_20060611-1plf1_i386.deb)
and others, checked the settings and changed to direct connect, still no go...  anyone have any thoughts?  Id appreciate the help, newbie to linux myself mostly... :D

---

