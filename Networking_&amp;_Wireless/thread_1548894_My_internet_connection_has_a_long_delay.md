---
title: "My internet connection has a long delay"
date: 2010-08-09
forum: Networking &amp; Wireless
---

### Post by dan_bwv1987 on 2010-08-09
Well, my problem is that every time I use the Ethernet connection (I don't have wireless card) there is a delay of around 30s, even though my download speed is not affected at all once the connection is "established" , no matter what application I use (Synaptic, ssh, firefox, google chrome,wget, update manager, etc.). A weird thing is that my ethernet connection always appears as active.
I'm sure I'm not the only one who has experienced this issue, since I've read the same problem on other forums, but no one has come up with a solution. I hope that there will be a solution at last by this time.
I've been around with this problem for about 1 month, I've tried all sorts of tweaks that involve disabling ipv6 and nothing happens. I don't really know what triggered off this issue because it all started all of a sudden and I don't remember having installed any important update by the time this happened (I did a clean installation of Ubuntu 10.04 32bits on the release date).

Thanks in advance for your help.

---

### Post by dineshs on 2010-08-09
Hope you have tried setting an open DNS eg:4.2.2.1
> there is a delay of around 30s you mean whenever you type a new address?

---

### Post by dan_bwv1987 on 2010-08-09
Yes, whenever I type a new address. 
Anyway, I followed your advice and I looked for an open DNS, and I found this 
link [https://store.opendns.com/setup/device/ubuntu/]("https://store.opendns.com/setup/device/ubuntu/") and it seems it finally worked. Nonetheless, I'm still puzzled because my internet connection was working pretty good, with no need for an open DNS, and suddenly the delays started. 
Well, at least there was a solution for the moment. 
Thanks dineshs.

---

### Post by dineshs on 2010-08-11
You may contact your ISP.Perhaps the DNS server/s maintained by the ISP  .....

---

