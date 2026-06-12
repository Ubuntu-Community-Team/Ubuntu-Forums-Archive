---
title: "SMC Router DNS Problems Solved"
date: 2006-04-29
forum: Networking &amp; Wireless
---

### Post by norm on 2006-04-29
I was having problems with ubuntu getting to the internet using an SMC 7004VBR router. I could enter the IP address and connect, but not using the name address such as [www.msn.com](www.msn.com), even though it worked in Windows operating systems.

I found that if I edited the dhclient.conf file and prepended the servers for cox cable ubuntu would work, but when I went back to Windows I had to add the servers into the networking configuration or Windows would not connect to the internet.

I went to SMC's home page and downloaded new firmware and that seems to have solved the problem. Both ubuntu and Windows will now connect to the internet using the router address as the name server.

So before trying all the other solutions for your router problems you might want to see if the manufacturer has new firmware as that might fix the problem.

Norm

---

### Post by Arzzka on 2006-05-11
Could you tell me the exact firmware version that solves this issue? I have SMC 7004VBR router (EU-model), part number 751.7924 and I am having the same problems. SCM webpage gives me a buch of firmware zips for other routers if I try to locate a version for the VBR EU model..

Thanks :)

---

