---
title: "Cannot ping outside network or IP after 12.04 upgrade."
date: 2013-03-31
forum: Networking &amp; Wireless
---

### Post by jamiehutber on 2013-03-31
So I am running 12.04 on my server but since the upgrade I can no longer reach any outside sources of the server.

I can SSH into the box, but from inside here I can not reach anything. At least, I can't ping, dig etc. 

I have provided everything that I could think that might give me more information, but can't see anything obviously wrong here.

```
root@sub:~# resolveip google.com
resolveip: Unable to find hostid for 'google.com': try again

```
```
root@sub:~# ping google.com
ping: unknown host google.com
```
```
root@sub:~# route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         77.68.108.1     0.0.0.0         UG    100    0        0 eth0
77.68.108.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0

```
```

root@sub:~# iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

```

Any ideas what has changed since the upgrade?

---

### Post by sanderj on 2013-03-31
What is the output of:

```
mtr -nrc2 8.8.8.8
```

---

### Post by prodigy_ on 2013-03-31
Most probably your **/etc/resolv.conf** is empty.

If so, use ```
sudo apt-get install resolvconf
sudo dpkg-reconfigure resolvconf
``` commands and add some DNS servers (e.g. 8.8.8.8 and 8.8.4.4 - Goggle DNS).

Another possibility is firewall blocking outgoing connections to UDP port 53.

---

