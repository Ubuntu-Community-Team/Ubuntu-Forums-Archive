---
title: "how to choose the best DNS server"
date: 2009-11-03
forum: Networking &amp; Wireless
---

### Post by afeasfaerw23231233 on 2009-11-03
The default DNS provided by my ISP seems not working well recently. It is slow while resolving names. However when I changes the DNS (from the home router) provided by other ISPs (those ISPs still locate within my country), the speed is much faster. Is there any command to test which DNS is the best?

---

### Post by Dishevel on 2009-11-03
208.67.222.222
208.67.220.220

---

### Post by Iowan on 2009-11-03
(Those would be the OpenDNS servers).

---

### Post by Dishevel on 2009-11-03
They would be. :)

---

### Post by sliketymo on 2009-11-03
> **afeasfaerw23231233 said:**
> The default DNS provided by my ISP seems not working well recently. It is slow while resolving names. However when I changes the DNS (from the home router) provided by other ISPs (those ISPs still locate within my country), the speed is much faster. Is there any command to test which DNS is the best?
  One thing would be to use the network ping tool,and compare your different servers.It would probably be a pain to do that very often.Of course servers in your own country are going to be faster,hopefully.Unfortunately,traffic to and from the server are going to effect it's resolution time.

---

### Post by duanedesign on 2009-12-16
Try out [namebench]("http://code.google.com/p/namebench/"). It hunts down the fastest DNS servers available for your computer to use. namebench runs a fair and thorough benchmark using your web browser history, tcpdump output, or standardized datasets in order to provide an individualized recommendation.

 * wget [http://namebench.googlecode.com/files/namebench-1.0.5.tgz](http://namebench.googlecode.com/files/namebench-1.0.5.tgz)
 * tar -xzvf namebench-1.0.5.tgz
 * cd namebench-1.0.5/
 * ./namebench.py

---

