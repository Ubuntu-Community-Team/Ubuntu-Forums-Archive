---
title: "Endian firewall"
date: 2010-02-23
forum: Networking &amp; Wireless
---

### Post by mosquetero on 2010-02-23
Hi!

I am using Endian firewall in order to connect two LANs but I am getting many problems and I don't know how to solve them since there is no much information about this software on the internet. Do yuo know  good webpage about this powerful program?

Thanks

---

### Post by pirateghost on 2010-02-23
[http://www.endian.com/en/community/](http://www.endian.com/en/community/)
[http://www.endian.com/en/community/get-help/support-forums/](http://www.endian.com/en/community/get-help/support-forums/)
[http://efwsupport.com/](http://efwsupport.com/)
[http://www.securitywithpassion.com.au/](http://www.securitywithpassion.com.au/)

---

### Post by mosquetero on 2010-02-23
Thanks but I have already tried them and they are not very helpful since few people read the topics :(

---

### Post by syncmasterpt on 2010-02-23
Sorry if I can't help you, but I was also an user of Endian firewall and I quit using it due to several issues and problems that where pretty annoying.

I replace it with Ubuntu LTS 8.04 server and a combination of Shorewall firewall, squid, postfix and Webmin. 

Works like a charm and it's fully documented.

---

### Post by mosquetero on 2010-02-23
My purpose is to connect two LANs so that hosts can connect between them using a VPN tunnel even if they are in different LANs. Can I do it with Ubuntu LTS 8.04 server and a combination of Shorewall firewall, squid, postfix and Webmin?

Thanks

---

### Post by pirateghost on 2010-02-23
i tried endian, but it fell short on its promises.  i decided the best option for me was vyatta.  huge learning curve but i have learned so much more going that route.

untangle is easy to set up and administer, but is a resource hog.
pfsense is fairly easy to setup, but almost offers too much, and the broken packages are a pain

if all you need is routing/firewall/vpn/squid+squidguard/ids/etc, check out vyatta.  if you are looking for a whole UTM, check out untangle if you have the horsepower

---

