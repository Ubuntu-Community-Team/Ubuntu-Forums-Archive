---
title: "IPTables error."
date: 2011-07-08
forum: Networking &amp; Wireless
---

### Post by Northernen on 2011-07-08
Hello.

I am trying to set up IPTables. However, every time I try to generate rules I get the error message:

"iptables v1.4.10: -X requires a chain and a policy
Try `iptables -h' or 'iptables --help' for more information."

This goes even for simple rules like "iptables -P OUTPUT -j ACCEPT". At first I thought it was just a warning, but iptables -L shows the rules as not having been accepted.

1) I am running it with sudo.
2) I have installed all the necessary kernel modules.

---

