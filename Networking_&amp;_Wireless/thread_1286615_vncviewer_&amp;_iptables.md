---
title: "vncviewer &amp; iptables"
date: 2009-10-09
forum: Networking &amp; Wireless
---

### Post by dc-zam on 2009-10-09
Hi, I have the following iptables configuration:

*filter
:INPUT DROP [32:10305]
:FORWARD ACCEPT [12:816]
:OUTPUT DROP [29:1880]
-A INPUT -p tcp -m tcp --dport 22 -j ACCEPT
-A INPUT -s 10.0.20.2/32 -p tcp -m tcp --sport 22 -j ACCEPT
-A INPUT -s 192.168.0.4/32 -j ACCEPT
-A OUTPUT -p tcp -m tcp --sport 22 -j ACCEPT
-A OUTPUT -d 10.0.20.2/32 -p tcp -m tcp --dport 22 -j ACCEPT
-A OUTPUT -d 192.168.0.4/32 -p tcp -m tcp --dport 5902 -j ACCEPT
-A OUTPUT -d 192.168.0.4/32 -p udp -m udp --dport 5902 -j ACCEPT
COMMIT

and I can't to connect via "vncviewer 192.168.0.4:5902"
If anyone knows where is the problem in the iptables configuration?
Without a firewall is working properly.

---

### Post by nixscripter on 2009-10-11
Try:

```

-A OUTPUT -d 192.168.0.**0**/32 -p tcp -m tcp --dport 5902 -j ACCEPT

```

(And UDP is not used by VNC, only TCP)

---

### Post by nixscripter on 2009-10-12
And another thing: 32 bits would match no hosts. I think you meant:

```
-A OUTPUT -d 192.168.0.0/**24** -p tcp -m tcp --dport 5902 -j ACCEPT
```

---

