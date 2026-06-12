---
title: "Desperately need help connecting to local IPs through college dorm connection"
date: 2005-02-27
forum: Networking &amp; Wireless
---

### Post by Zyme on 2005-02-27
I am running amd64 warty and connecting with my ethernet card simply by plugging into the wall.  Under windows xp, I was able to connect to all local IP addresses without incident.  For example, the link [http://10.254.0.50/account/whatsmypubip.php](http://10.254.0.50/account/whatsmypubip.php) is supposed to show me my private and public ips.  Under XP, it does just that, but with ubuntu, I am unable to connect (connection time out after some time).  Here is what I know:

-The school uses a lot of packetshaping things to prevent peer to peer transfers bogging down the network
-All computer conected to the internet in the way I am have a public IP (usually starts with 65.###), and a private IP (10.###).
-Windows XP can connect to both IPs just fine (maybe because it can automatically detect connection settings?)
-While I cannot load [http://10.254.0.50/](http://10.254.0.50/), I can ping 10.254.0.50 just fine:

```
PING 10.254.0.50 (10.254.0.50) 56(84) bytes of data.
64 bytes from 10.254.0.50: icmp_seq=1 ttl=127 time=0.158 ms
64 bytes from 10.254.0.50: icmp_seq=2 ttl=127 time=0.146 ms
64 bytes from 10.254.0.50: icmp_seq=3 ttl=127 time=0.145 ms
64 bytes from 10.254.0.50: icmp_seq=4 ttl=127 time=0.141 ms
64 bytes from 10.254.0.50: icmp_seq=5 ttl=127 time=0.144 ms
64 bytes from 10.254.0.50: icmp_seq=6 ttl=127 time=0.146 ms
64 bytes from 10.254.0.50: icmp_seq=7 ttl=127 time=0.149 ms
64 bytes from 10.254.0.50: icmp_seq=8 ttl=127 time=0.142 ms
64 bytes from 10.254.0.50: icmp_seq=9 ttl=127 time=0.147 ms
``` 

What I don't know:
-If there is a transparent proxy.  I think there probably is.  How would I find out?
-If there is a proxy, what I should do about it.

Any help would be greatly appreciated, as I have been trying to solve this problem for quite some time, and would be extremely happy with my linux installation if I could figure it out.

---

### Post by alastair on 2005-02-27
Someone should know if there is a proxy to configure - ask. Isn't this an XP setting in IE somewhere?

Does your ethernet get an IP via DHCP? Perhaps the settings are in there.

Mozilla and firefox (and gnome) let you setup HTTP proxies - so this should be solvable.

---

### Post by kleeman on 2005-02-27
Wierd I can't ping it in Ubuntu. Did you ping it from Winblows?
BTW dslreports.com has an ip discovery routine

---

### Post by alastair on 2005-02-27
That's a private IP - shouldn't be routed on the internet ...

---

