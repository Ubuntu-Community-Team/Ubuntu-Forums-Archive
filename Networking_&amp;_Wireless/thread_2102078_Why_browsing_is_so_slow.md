---
title: "Why browsing is so slow?"
date: 2013-01-06
forum: Networking &amp; Wireless
---

### Post by Muratturat on 2013-01-06
I've used all browsers (chromium, firefox...) but browsing is very slow. 

For example it takes over 20 seconds to load my facebook page.
But when I am downloading files, the average downloadspeed is 2 mb/s.

I tested my internet speed at (speedtest.net) and it shows 49 Mbps.

1. I checked channel, no one use same channel.
2. I changed Wi-Fi anten to better place
3. I disabled IPV6
4. I checked router settings and firewall.


Laptop: Fujitsu L. AH-531
Connecting with Wi-Fi
Signal level -71dBm
Link quality 37%

Could the problem be from wireless card driver or from of ubuntu settings? If it is, how I can fix it, thanks for the answers.):P

---

### Post by offgridguy on 2013-01-06
I use a wireless air card also, it can be painfully slow at times probably due to signal reception.   When it is slow, all browsers are slow, plus i have a dual boot with windows7 and if ubuntu is slow so is windows. So i don't think it is related to settings in ubuntu.                                                                              The only cure for slow connection, due to reception that i know of would be to buy a booster, not sure what the official name is. It works for both cel phone service and internet air card. But that may not be an option where you live?

---

### Post by The Spectre on 2013-01-06
Try setting a different DNS Server in your Router like Google or OpenDNS.

[http://pcsupport.about.com/od/tipstricks/a/free-public-dns-servers.htm](http://pcsupport.about.com/od/tipstricks/a/free-public-dns-servers.htm)

---

### Post by The Spectre on 2013-01-06
You could also run this Benchmark to determine which DNS Server would be best for you.
It is a Windows program but it will run in Linux with Wine installed. 

Domain Name Speed Benchmark
[http://www.grc.com/dns/benchmark.htm](http://www.grc.com/dns/benchmark.htm)

---

### Post by Muratturat on 2013-01-06
> **offgridguy said:**
> I use a wireless air card also, it can be painfully slow at times probably due to signal reception.   When it is slow, all browsers are slow, plus i have a dual boot with windows7 and if ubuntu is slow so is windows. So i don't think it is related to settings in ubuntu.                                                                              The only cure for slow connection, due to reception that i know of would be to buy a booster, not sure what the official name is. It works for both cel phone service and internet air card. But that may not be an option where you live?

I live in Finland

---

### Post by Muratturat on 2013-01-06
> **The Spectre said:**
> You could also run this Benchmark to determine which DNS Server would be best for you.
It is a Windows program but it will run in Linux with Wine installed. 

Domain Name Speed Benchmark
[http://www.grc.com/dns/benchmark.htm](http://www.grc.com/dns/benchmark.htm)

thank you, I will try and let you know if it work.

---

### Post by Muratturat on 2013-01-06
> **The Spectre said:**
> You could also run this Benchmark to determine which DNS Server would be best for you.
It is a Windows program but it will run in Linux with Wine installed. 

Domain Name Speed Benchmark
[http://www.grc.com/dns/benchmark.htm](http://www.grc.com/dns/benchmark.htm)

it helped, I do not know what I did but now it is up to 2 times faster:D:D 
HOLY THANKS!

---

