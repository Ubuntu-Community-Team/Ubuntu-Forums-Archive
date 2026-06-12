---
title: "Check who is connected to your router ?"
date: 2012-10-11
forum: Networking &amp; Wireless
---

### Post by Herbalist on 2012-10-11
Hi guys
in windows there is a command in cmd,that allows you to check all the PCs that are connected to your router or network its (net view) if im correct,
is their a similar command that can be written in the terminal to do that ?
Regards

---

### Post by steeldriver on 2012-10-11
You could use nmap, e.g.

```
nmap -sP 192.168.1.0/24
```(adjust as appropriate for you own LAN subnet range)

If run with sudo it will give additional info (MAC, vendor if available) - otherwise it will just confirm the connected IPs

---

