---
title: "Custom nameservers w/ NetworkManager in Lucid"
date: 2010-05-10
forum: Networking &amp; Wireless
---

### Post by seattlegaucho on 2010-05-10
Hi,

This used to work in Karmic to set up additional nameservers when using NetworkManager, but it stopped working with Lucid:

[LIST]
[*]Edit /etc/dhcp3/dhcplient.conf to add the following line:
```
append nameserver <your_favorite_server(s)>;
```  
[/LIST]

However, when I upgraded to Lucid, this stopped working, even after rebooting.

But if I restarted the network services after logging in, it works just fine. The command line:
```
sudo /etc/init.d/networking restart
```

Google didn't bring up any bug or forum post with this particular issue and I'm not even sure it's reproduce-able (I can on my machine). Anyone else has the same issue or knows of the proper bug #?

The system is running Kubuntu Lucid Lynx + updates:

```

cat /etc/issue
Ubuntu 10.04 LTS

cat /proc/version
Linux version 2.6.32-22-generic (buildd@yellow) (gcc version 4.4.3 (Ubuntu 4.4.3-4ubuntu5) ) #33-Ubuntu SMP Wed Apr 28 13:28:05 UTC 2010

network-manager version: 0.8-0ubuntu3

```

---

