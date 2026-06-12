---
title: "Weird issue with NAT router and Windows PCs"
date: 2010-12-14
forum: Networking &amp; Wireless
---

### Post by Randy Jackson on 2010-12-14
Hello,

Today, I had a brief power outage.  Despite having all of my computers and peripherals hooked up to UPSs, one of my network switches was hosed.  Once I determined what the problem was, I replaced the switch and I was back in business--or so I thought.

I've been using a NAT router setup for at least 6 years, and generally no issues.  However, I've got a weird issue now that I've not seen before, and searching hasn't helped.  

I have two Windows PCs behind the router.  If I restart networking, both have internet access for about 10 minutes, then suddenly they lose connection.  The other Ubuntu machines are not affected.  I can still access network shares from the Windows computers, just no internet.

Does anyone have any thoughts on the matter?

---

### Post by synicalx on 2010-12-14
Quick question, DHCP?

I had a similar problem (with Vista though), fairly sure I managed to solve it by giving the Vista-problem-child a static IP.

---

### Post by Randy Jackson on 2010-12-14
Both Windows PCs have static IPs.  That's one of the things that makes this odd.  Internet works for about ten minutes, then poof, nothing.

---

### Post by Randy Jackson on 2010-12-15
It appears to be fixed now.  I updated my IPTABLES rules to ensure that internet connection sharing was working. Thanks for your help.

---

