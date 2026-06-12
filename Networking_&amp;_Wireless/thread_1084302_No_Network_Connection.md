---
title: "No Network Connection"
date: 2009-03-01
forum: Networking &amp; Wireless
---

### Post by mah_sa on 2009-03-01
Hello, 

I have a network connection problem. 
I have tried the followings: 
> sudo ifup eth4
>>ifup:interface eth4 already configure
> ifconfig eth4
>> 'gives the correct info'
IP is set statically. 
What else should I try?

Thanks,

---

### Post by Rokurosv on 2009-03-01
Have you checked your /etc/resolv.conf file? Is it blank?
BTW Welcome to the forums :P

---

### Post by mah_sa on 2009-03-02
Thanks :)
resolv.conf is not blank. It has 'seach' and 'nameserver'. 

I also tried dmseg | grep eth, and I am getting 
ADDRCONF (NETDEV_UP): eth4: link is not ready
r8169: eth: link is up
ADDRCONF (NETDEV_CHANGE): eth4: link becomes ready
r8169: eth: link down
eth4: no IPv6 routers present

---

