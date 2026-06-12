---
title: "Winbindd errors"
date: 2009-05-08
forum: Networking &amp; Wireless
---

### Post by fusa on 2009-05-08
Since upgrading from Ubuntu 8.10 to 9.04 I am getting a lot of errors in my syslog.  They are:  

May  8 14:23:26 username winbindd[4643]: [2009/05/08 14:23:26,  0] winbindd/idmap.c:idmap_alloc_init(587) 
May  8 14:23:26 username winbindd[4643]:   ERROR: Initialization failed for alloc backend, deferred! 
May  8 14:23:26 username winbindd[4643]: [2009/05/08 14:23:26,  0] winbindd/idmap.c:idmap_alloc_init(587) 
May  8 14:23:26 username winbindd[4643]:   ERROR: Initialization failed for alloc backend, deferred! 
May  8 14:23:26 username winbindd[4643]: [2009/05/08 14:23:26,  0] winbindd/idmap.c:idmap_alloc_init(587) 
May  8 14:23:26 username winbindd[4643]:   ERROR: Initialization failed for alloc backend, deferred! 
May  8 14:23:26 username winbindd[4643]: [2009/05/08 14:23:26,  0] winbindd/idmap.c:idmap_alloc_init(587) 

I am able to connect to my Windows shares from Ubuntu, and Windows is able to connect to the shares I have for Ubuntu.  What could be causing this?  I don't think that I received the errors prior to upgrading to 9.04.

---

### Post by mattgyver83 on 2009-05-08
I dont have any real knowledge of winbind however I have had to use it to fix my windows shares on 9.04 as well.

If you have winbind installed make sure you edit /etc/nsswitch.conf

 edit 'files' line to include 'wins' before dns and m4dns
	hosts:          files mdns4_minimal [NOTFOUND=return] wins dns mdns4

Maybe that will work for you too!

---

### Post by fusa on 2009-05-08
Unfortunately my hosts line in nsswitch.conf is already exactly like yours.

---

