---
title: "Ubuntu 10.04 LTS - No internet."
date: 2010-06-01
forum: Networking &amp; Wireless
---

### Post by wmx000 on 2010-06-01
Wired and Wireless connections do not work on Ubuntu 10.04 LTS, it says that the "Connection is Established" but when I open Firefox I don't have internet.

I've installed Ubuntu on my hard disk and in Vmware in Windows and I still get the same problem.
Updates do not work either, there's a connection but no internet. 

I've seen some people experience similar problems as this one with Ubuntu 10.04 but no solution yet has be offered.

---

### Post by mituw16 on 2010-06-02
open terminal and then post back the results of this command 

```

ifconfig

```

---

### Post by Iowan on 2010-06-02
If **ifconfig -a** shows an IP address, check results of **route -n** (gateway (UG) in particular). Finally, verify correct nameservers in */etc/resolv.conf*.  You can try pinging the router and internet by IP (74.125.95.147).

---

### Post by wmx000 on 2010-06-02
Thanks everyone for the suggestions, the updates were working fine, the problem turned out to be from firefox, it did not open any page. The following fixed the problem:


Open your Firefox and type **about:config** at URL address bar and hit  enter. To make a False into True, select the line to change, and double  click. On the 2nd option change, right click and select Modify
```

 - network.http.pipelining > Make it True
 - network.http.pipelining.maxrequests > Make it 8 or 10
 - network.http.proxy.pipelining > Make it True
 - network.dns.disableIPv6 > Make it True

```Source: ```
http://crenk.com/fix-the-firefox-slow-problem-in-ubuntu-10-04/
```

---

