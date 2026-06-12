---
title: "Unable to view websites"
date: 2011-02-16
forum: Networking &amp; Wireless
---

### Post by Asgeco on 2011-02-16
For some reason I'm unable to view most of websites while my laptop is on wired connection. If I use a router and connect to the internet through wireless everything is fine.

While I'm on wired connection I'm able to load most of google services (google.com, gmail, google maps, picasa). I'm also able to load youtube but then I press on any video page loads but youtube video never loads.

If I try to load [www.nvidia.com](www.nvidia.com) web page never loads same with other web sites.

I tried to ping [www.nvidia.com](www.nvidia.com) and I get this
```
ping www.nvidia.com
PING a1650.g.akamai.net (92.123.68.43) 56(84) bytes of data.
64 bytes from a92-123-68-43.deploy.akamaitechnologies.com (92.123.68.43): icmp_req=1 ttl=57 time=30.3 ms

```

tried telnet and get this 
```
telnet www.nvidia.com 80
Trying 92.123.68.18...
Connected to a1650.g.akamai.net.

```
and nothing more.

On the same laptop I have windows 7 and everything works perfectly.
I'm using ubuntu 10.10 32-bit desktop edition.
Forgot to mention that then I installed ubuntu, couple of hours wired connection worked fine but then I restarted my computer it stopped working.

Can anyone help me to solve this problem?

---

### Post by squenson on 2011-02-16
It may be a problem with IPv6 enabled.

Click on the menu System > Preferences > Network Connection, then select you wired connection and click the Edit button. Go to the tab IPv6 settings and select the Method "Ignore".

---

### Post by Asgeco on 2011-02-16
It doesn't help

---

