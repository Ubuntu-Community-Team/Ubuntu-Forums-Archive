---
title: "dhcpd Vs. Firestarter"
date: 2006-04-25
forum: Networking &amp; Wireless
---

### Post by AlphaMack on 2006-04-25
Recently I installed Mac-on-Linux, which also required dhcpd, ipmasq, and dnsmasq.  I have had Firestarter running on my system.  After installing and configuring MOL, I suddenly lost all network connectivity in Ubuntu unless I either launched MOL or Firestarter.  I have never had this issue until installing MOL and its required dependencies (see above).

I spent several hours in frustration only to find that the culprit was under my nose the entire time...

The problem is definitely with the firewall and I'm not sure what is going on that is preventing any kind of network connectivity (by that I mean being able to surf the web, get the weather item in the panel to display, etc.).  Firestarter/iptables doesn't like something...

Only when I launch Firestarter, which is set to "restart" itself upon launching the program, do I get any connectivity back...

Please help me out here with what I need to make sure of.

---

