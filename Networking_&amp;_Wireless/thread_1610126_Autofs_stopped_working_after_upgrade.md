---
title: "Autofs stopped working after upgrade"
date: 2010-10-31
forum: Networking &amp; Wireless
---

### Post by frkstein on 2010-10-31
I recently upgraded from 9.10 through 10.04 to 10.10. When I was running 9.10 I was using autofs to automount some nfs shares. It was working fine. After the upgrade, whenever I try to cd into /nfs/share, I get a message stating that no such file or directory exists. I looked at /nfs/auto.master and have the necessary line of
/nfs /etc/auto.nfs

 I also looked at auto.nfs and made sure that it was properly defined as 

share server:/servedshare

I verified that the automount process is running.

I have this exact setup running on another machine which is also running 10.10 and autofs works just fine.

Any thoughts as to what is going on?

---

