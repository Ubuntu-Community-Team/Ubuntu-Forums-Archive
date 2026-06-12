---
title: "wired network problem - missing packages/bad config"
date: 2011-04-24
forum: Networking &amp; Wireless
---

### Post by espressobeanie on 2011-04-24
I'm having problems with networking. I just installed Debian 6 SServer LAMP and it didn't autoconnect to internet. I plug in the internet to my eth0 (default) port, and I keep getting timeouts. I found that dhcp3-client was not installed and fixed that. My etc interfaces has this for eth0:  Auto eth0 Iface eth0 inet dhcp  What other packages or config do I need to make the internet work? It's missing something basic that wasn't setup properly.  I do get the correct dns address to my isp provider when I check etc resolv.conf. It just can't dhcp discover. Always says sleeping.

---

### Post by Ropes on 2011-04-24
Can you at least connect to the router?  or are you going strait to your modem?
Show what your
 ```

$ifconfig
$netstat

``` outputs.

---

