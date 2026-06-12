---
title: "Intermittent Wifi / Firefox ? issues ?"
date: 2010-04-02
forum: Networking &amp; Wireless
---

### Post by Tom_T on 2010-04-02
Hi

Ubuntu 9.10 running on Acer Aspire D150 using Atheros Wireless:
```
01:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)

```
Wireless connection is at 80% - 95%, DHCP address, with static DNS. IP 6 is set to ignore.

The wireless connects fine to my router, but occasionally I have to 'double' load pages in firefox or Google Chrome.

eg: [www.google.com](www.google.com), press return... pause.. pause... press return WORKS !!

pinging a network address local or on the Internet seems to work fine, it just appears to be browsing.

I've tried using the following as my DNS, all with the same results: My Router, My Win2003 Server (running DNS) my ISP & OpenDNS.

Any Ideas ??

Thanks :)

---

### Post by Tom_T on 2010-04-10
Can anyone offer any advice on this ?


Thanks :)

---

### Post by chili555 on 2010-04-10
Is IPv6 disabled in Firefox? Type about:config in the address bar and search for:

```
network.dns.disableIPv6
```


and toggle it to TRUE.

---

### Post by Tom_T on 2010-04-11
Thanks for the reply.

I have already got that set.

Also this affects Chrome !

Any other ideas ?

---

### Post by Tom_T on 2010-04-17
Can know one help with this ?
 :(

---

