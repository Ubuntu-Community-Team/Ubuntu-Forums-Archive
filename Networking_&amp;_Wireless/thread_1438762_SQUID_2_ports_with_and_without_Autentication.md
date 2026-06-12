---
title: "SQUID 2 ports? with and without Autentication"
date: 2010-03-25
forum: Networking &amp; Wireless
---

### Post by banutito on 2010-03-25
Hello all!
I need to make squid to listen on two ports. one for transparent proxy for all users in my LAN and one non transparent for authenticated users.

I have this situation!
  on my firewall I installed squid and dansguardian.
  squid is a transparent proxy and listen on 3128
  dansguardian listen on 8080 and redirect all to 3128
  iptables redirect all traffic from 80 to 8080.

  Now I need to make squid to listen on other port and make them to  request users to authenticate only on that port. dansguardian should not work for this port.

It is possible somehow???????????????????:confused:

---

### Post by banutito on 2010-03-26
Anyone?  :-?

---

### Post by banutito on 2010-03-27
Someone!!!!

---

