---
title: "Is there a bgb route query command?"
date: 2013-03-05
forum: Networking &amp; Wireless
---

### Post by apoth on 2013-03-05
Something along the lines of the tool available [here](http://lg.telia.net/?query=bgp&protocol=IPv4&addr=ubuntuforums.org&router=Hong%20Kong).

---

### Post by iponeverything on 2013-03-05
Assuming that you have installed and are running a bgp daemon and that you are peering with your upstream providers. Then yes - the command to show you your bgp routing table will vary according the routing suite that you have chosen to use.

If your talking about tool to query the bgp routing tables on routers that don't belong to you, routers generally are not open to random queries from strangers. If you have router and are looking for a tool to query the bgp routes from a Linux host, writing something is fairly trivial.  --

---

