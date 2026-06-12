---
title: "Enable NAT using UFW on 10.04"
date: 2011-05-27
forum: Networking &amp; Wireless
---

### Post by Anonymouslemming on 2011-05-27
Hi all,

I'm trying to move from CentOS to Ubuntu and the last task I have is my firewall. I am following the instructions at [https://help.ubuntu.com/10.04/serverguide/C/firewall.html](https://help.ubuntu.com/10.04/serverguide/C/firewall.html)

I have added the following to /etc/ufw/before.rules near the bottom (before the commit line)

```
# nat Table rules
*nat
:POSTROUTING ACCEPT [0:0]

# Forward traffic from eth1 through eth0.
-A POSTROUTING -s 192.168.87.0/24 -o eth0 -j MASQUERADE
```
When trying to restart the box, I see the following error on my console:

```
  Bad Argument `*nat'
Error occurred at line: 65
Try `iptables-restore -h' or `iptables -restore --help' for more information.
Problem running '/etc/urw/before.rules'
```

Line 65 in my before.rules file is
*nat

Any advice would be much appreciated

---

### Post by bedge on 2012-02-29
Put it after the commit line, and add another commit at the end.

---

