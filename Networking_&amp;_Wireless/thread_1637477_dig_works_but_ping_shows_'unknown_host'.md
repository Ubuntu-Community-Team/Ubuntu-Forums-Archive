---
title: "dig works but ping shows 'unknown host'"
date: 2010-12-04
forum: Networking &amp; Wireless
---

### Post by slava_ on 2010-12-04
Hello, 

I've encountered a problem after doing a fresh install with xubuntu 10.10 (2.6.35-23-generic).

some sites are blocked like 'www.skypeassets.com'

if I do **dig www.skypeassets.com** - I receive the A, CNAME records and the IP address and everything

when **ping www.skypeassets.com** - I receive 'unknown host'.

when **ping <theipaddress>** - I receive responses


Please help me finding out what is the problem and fix it...

Thanks

---

### Post by Brandon Williams on 2010-12-06
When you "dig", it always goes to DNS for resolution. When a utility performs name resolution, it might check somewhere else first, such as /etc/hosts. My guess would be that there is a higher priority lookup source that is screwing this up for you, but I'm not sure what it might be. 

What is the output of 'grep hosts /etc/nsswitch.conf'? On my machine, it's "hosts: files dns", which means that name resolution will first check files (e.g. /etc/hosts) and then check dns, so a listing in /etc/hosts would over-ride the return from dig. Try temporarily changing /etc/nsswitch.conf to "hosts: dns" so that name resolution only uses dns. Does the ping work? If so, then some other entry in /etc/nsswitch is causing trouble.

---

### Post by slava_ on 2010-12-08
> **Brandon Williams said:**
> When you "dig", it always goes to DNS for resolution. When a utility performs name resolution, it might check somewhere else first, such as /etc/hosts. My guess would be that there is a higher priority lookup source that is screwing this up for you, but I'm not sure what it might be. 

What is the output of 'grep hosts /etc/nsswitch.conf'? On my machine, it's "hosts: files dns", which means that name resolution will first check files (e.g. /etc/hosts) and then check dns, so a listing in /etc/hosts would over-ride the return from dig. Try temporarily changing /etc/nsswitch.conf to "hosts: dns" so that name resolution only uses dns. Does the ping work? If so, then some other entry in /etc/nsswitch is causing trouble.

thanks, for reply.

The output of 'grep hosts /etc/nsswitch.conf' is: 

**hosts: files mdns4_minimal [NOTFOUND=return] dns mdns4**


I've tried to comment this line and leave only the "hosts: dns". After restart, ping does not work, as it was before.
It seems something else is causing problems.

Also I found in one [thread]("http://www.phwinfo.com/forum/linux-debian-user/330053-possible-dns-issue-debian-lenny.html") that disabling the IPv6 can clean the issue -- but not in my case, I have the IPv6 disabled.

---

