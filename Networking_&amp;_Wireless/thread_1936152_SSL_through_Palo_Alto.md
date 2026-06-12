---
title: "SSL through Palo Alto"
date: 2012-03-05
forum: Networking &amp; Wireless
---

### Post by Rogueninja64 on 2012-03-05
Hey guys trying to keep 11.10 running for corporate stuff and so far I have succeeded in not having to revert to windows for anything. Now we are switching to a new vpn and I thought since Palo Alto requires JRE 6 on the other windows machines the jre 6 and jre 7 that I have here would work perfectly fine. Any one have any kind of insight on this stuff?

Thanks,

Joseph

---

### Post by atimonin on 2012-06-26
shrewsoft vpn client works with palo alto global protect.
The only thing you should do by hands:

sysconfig net.ipv4.conf.eth0.rp_filter=0

(or whatever net interface you use)
or permamnetly set it in /etc/sysconfig.d/...

---

