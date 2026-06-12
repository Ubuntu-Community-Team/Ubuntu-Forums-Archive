---
title: "Sharing internet connection via code rather than Firestarter"
date: 2006-03-19
forum: Networking &amp; Wireless
---

### Post by alamba on 2006-03-19
Hi,

I'm able to share the internet connection on my ubuntu box by using firestarter and clicking on share internet connection (or similar words). I don't have DHCP running cos I have a dhcp server running on my primary AP. 

How can I do this on a ubuntu server install? That is, what code and where is firestarter modifying in order to do packet forwarding? Is it in /etc/interface?

Akshay

---

### Post by dermotti on 2006-03-19
firestarter is a frontend for iptables i belive. It is writing a config file for iptables to read somewhere.

---

### Post by Iain on 2006-03-19
Check out this: [https://wiki.ubuntu.com/ThinClientHowtoNAT](https://wiki.ubuntu.com/ThinClientHowtoNAT)

---

### Post by alamba on 2006-03-20
Thanks Iain that did explain it. Evidently it does manipulate the /etc/network/options file and runs a script to enable NAT on iptables. 

a

---

