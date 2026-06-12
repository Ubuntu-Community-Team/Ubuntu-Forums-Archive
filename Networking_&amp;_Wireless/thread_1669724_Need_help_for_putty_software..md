---
title: "Need help for putty software."
date: 2011-01-18
forum: Networking &amp; Wireless
---

### Post by honey_bee on 2011-01-18
Hi,
I am using ubuntu in my Lan envroment. I need guidance that how can i remotely access my linux pc from windows enviroment within lan ? **Yes putty is the software** which i have downloaded from net. 
The problem is when I trun off my Linux firewall I can access my linux  terminal and when I turn on the IPTABLES it stop to access me the Linux terminal.
**Which entry can I add in linux firewall so it may work with putty**
Please help me.
honey

---

### Post by SeijiSensei on 2011-01-18
Add a rule like this above any DENY or REJECT rules:

```

iptables -A INPUT -s 10.10.10.0/24 -d 10.10.10.1 -p tcp --dport 22 -j ACCEPT

```

This enables SSH access from any machines in the 10.10.10.0/24 network to the server at 10.10.10.1.  Change these addresses to fit your local network addressing scheme.

---

