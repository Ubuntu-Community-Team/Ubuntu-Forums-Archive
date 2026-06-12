---
title: "Can Not Browse to Google from behind &quot;Ubuntu Router&quot;"
date: 2012-10-21
forum: Networking &amp; Wireless
---

### Post by jonasjones on 2012-10-21
Hello all, my first time posting here. I have found many answers to questions on this site, but have run into something that is fully stumping me.

About a year ago I turned my Ubuntu Desktop into a router as well. I added a second ethernet port and a wireless card, and bridged them to create a LAN behind my desktop router. Everything has been working fine until recently.

I have been unable to browse to [www.google.com](www.google.com). I can ping the the host name google.com from any device behind the router, and i can ping any of google's IP addresses...(search, dns server etc) but i can not browse using IE, firefox, chrome, chromium or android browser on several different OSes. No other website has this problem. For example yahoo.com works fine. 

Now from the Ubuntu Router itself I can browse to [www.google.com](www.google.com) just fine.

I am using DNSmasq to on the router for DNS and DHCP, and i have tried restarting it to no avail. I have also tried changing /etc/resolvconf/resolv.d/head to a different DNS server, but that did not work either. I am at a complete loss, because it seems like DNS lookup is working as all other sites are browseable and I am able to ping [www.google.com](www.google.com).

Any ideas would be greatly appreciated. Thanks.

---

### Post by jonasjones on 2012-10-21
Update:

The original DNS server I was pointing to was 8.8.8.8. When the issue started I tried changing it to my service provider, then my edge router and neither resolved the original problem. I just changed it back to 8.8.8.8 and now it is working again. So at this moment I do not have any problems, but I would still like some insight as to what may have caused an issue like this... i.e. What would cause devices behind my Ubuntu Desktop router to not browse to a website when the hostname for that website can be pinged.

Thanks again.

---

