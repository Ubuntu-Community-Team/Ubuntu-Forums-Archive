---
title: "eth0 problems"
date: 2011-01-06
forum: Networking &amp; Wireless
---

### Post by TinuvaGeo on 2011-01-06
Hello,

I just installed Ubuntu 10.10 on this box and plugged an ethernet cable in but even though Ubuntu claims it is connected to the network I cannot access the internet.

ifconfig says an ip (192.168.2.9) is allocated to the computer but according to my router it is not (0.0.0.0 and idle connection). The LAN ethernet device on the box is a Realtek RTL8139. Running dhclient didn't solve the problems either.

Anyone got any suggestions? Ideas?

Thank you in advance,

~Tinuva

Edit: I can ping hostnames and IPs fine. I just tried to ping my router: success, pinged google.com success, pinged directly to the ip of google.com success and pinging ubuntuforums.org is a successfull ping too.

---

### Post by chili555 on 2011-01-06
> Edit: I can ping hostnames and IPs fine. I just tried to ping my router: success, pinged google.com success, pinged directly to the ip of google.com success and pinging ubuntuforums.org is a successfull ping too.Can you surf web pages with Firefox? I'm not sure what we can fix.

---

### Post by TinuvaGeo on 2011-01-06
> **chili555 said:**
> Can you surf web pages with Firefox? I'm not sure what we can fix.
No I cannot reach pages in FireFox :/ that's the problem.
I am able to ping them by both domain and IP but I cannot browse any site using either the domain or IP.

---

### Post by chili555 on 2011-01-06
Please run and post:```
traceroute www.google.com
```Also, in Firefox, open File and make sure Work Offline is unchecked. You might also look at Edit > Preferences > Advanced > Network. Is Firefox accessing the network as you expect?

---

### Post by TinuvaGeo on 2011-01-06
The traceroute is failing hard:
```

1 Extraction 0.170ms pmtu
1 dsldevice.lan 100.357ms *
1 dsldevice.lan 97.827ms *
2 195.190.241.7 41.561ms asymm
3 nl-rt-dc2-isp-bb21.wxs.nl 35.509ms asymm
4 nl-rt-dc2-isp-bb21.wxs.nl 36.389ms *
5 no reply *
6 no reply *
7 no reply *
```
So yeah it's obviously not in firefox.

---

### Post by endotherm on 2011-01-06
well, no, it actually is probably firefox. traceroutes often cannot determine hops after a certian distance, or will not be able to detect some hops as they occur. traceroute works by sending packets that would elicit an error message, and they use that message to determine information about the hop. if the IS in question does not respond to an error or the sent packet does not produce the error expected, then that hop will not be shown. 

if you can ping [www.ubuntuforums.com](www.ubuntuforums.com) by name, then your Internet is working fine, so your issue is most likely your browser. 

the first thing I would try is bleachbit, to vaccum my firefox configuration and clear all my cache. then i woudl check my connection settings, and make sure that all my config is as expected (no proxies, etc).

---

### Post by TinuvaGeo on 2011-01-06
Stuff like sudo apt-get update is taking very long or erroring on connecting some mirrors too though.

Edit: Checked firefox, no (strange) proxy settings, no offline mode, just looks like it should look

---

