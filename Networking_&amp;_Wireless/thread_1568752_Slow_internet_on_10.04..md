---
title: "Slow internet on 10.04."
date: 2010-09-05
forum: Networking &amp; Wireless
---

### Post by StevenH94 on 2010-09-05
[http://www.speedtest.net/](http://www.speedtest.net/)

Now, this website used to say I have a 10 megabits per seconds (1.1 MB/s) download speed when I was running windows XP.. Now, unfortunately I'm only getting 1 - 2 megabits per second.

So far I have tried, 

/etc/default/grub
GRUB_CMDLINE_LINUX="ipv6.disable=1"

firefox - about:config
- network.http.pipelining >  True
 - network.http.pipelining.maxrequests >  10
 - network.http.proxy.pipelining >  True
 - network.dns.disableIPv6 > True


*/etc/sysctl.conf*
#disable ipv6
net.ipv6.conf.all.disable_ipv6 = 1
net.ipv6.conf.default.disable_ipv6 = 1
net.ipv6.conf.lo.disable_ipv6 = 1




Can anyone help in suggesting anything else to get my download speed back up to 1.1MB/s.. Thanks.

---

### Post by Dumpy Dumpster on 2010-09-06
I am very far from an expert, but it seems I had the same problem as you. After a fair bit of fiddling around, I dumped Firefox and installed Google Chrome.  What a difference!

---

### Post by kammmo on 2010-12-23
try to check your proxy server settings.. >>System>Preferences>Network Proxy if your connection use proxy you must set it:popcorn:

---

