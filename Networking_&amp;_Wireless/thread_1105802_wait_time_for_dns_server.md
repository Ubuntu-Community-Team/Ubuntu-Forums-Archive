---
title: "wait time for dns server"
date: 2009-03-25
forum: Networking &amp; Wireless
---

### Post by sefs on 2009-03-25
From time to time my primary dns server goes down and my desktop needs to fall back to the secondary dns server...but i find the wait (the time my computer takes to decide the primary is down and go to the secondary) i annoyingly long.

Is there a way to tweak the wait time in linux?

Thanks.

---

### Post by sefs on 2009-03-25
I see that i can tweak the time out from this link
[http://manpages.ubuntu.com/manpages/dapper/man5/resolv.conf.5.html](http://manpages.ubuntu.com/manpages/dapper/man5/resolv.conf.5.html)

by entering timeout:n where n is in seconds to wait before timing out. 

I tried this but if i restart networking and reboot...resolv.conf seems to be rewritten and the timout entry is lost.

Is there a special way to set these options?

---

