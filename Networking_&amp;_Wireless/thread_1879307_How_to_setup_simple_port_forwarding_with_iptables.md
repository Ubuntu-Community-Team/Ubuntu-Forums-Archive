---
title: "How to setup simple port forwarding with iptables?"
date: 2011-11-11
forum: Networking &amp; Wireless
---

### Post by jbm222 on 2011-11-11
I have a Linux box (machine A) connected to a LAN via eth0 and to another machine (machine B) on eth1.

I want to forward connections made to machine A port 80 to machine B.

Machine A's IP on eth0 (main LAN) is 192.168.1.126.
Machine A's IP on eth1 (my personal 2-machine LAN) is 192.168.10.1.

Machine B's IP on the mini-lan connected to eth1 is 192.168.10.2

First, I ran this script to get a clean slate with my IP table settings.

```
#!/bin/bash
echo "Stopping firewall...."
iptables -F
iptables -X
iptables -t nat -F
iptables -t nat -X
iptables -t mangle -F
iptables -t mangle -X
iptables -P INPUT ACCEPT
iptables -P FORWARD ACCEPT
iptables -P OUTPUT ACCEPT
```

Then I ran these commands to try to setup the port forwarding:
```

iptables -t nat -A PREROUTING -i eth0 -p tcp -d 192.168.1.126 --dport 80 -j DNAT --to 192.168.10.2:80
iptables -A FORWARD -p tcp -i eth0 -d 192.168.10.2 --dport 80 -j ACCEPT

```

When I test from another machine the eth0 main LAN, it doesn't work.  Can anyone tell me what I'm doing wrong?

---

### Post by Dangertux on 2011-11-11
Try doing the following

```

sudo echo "1" > /proc/sys/net/ipv4/ip_forward

```
This will enable packet forwarding as it is not enabled by default.

---

### Post by jbm222 on 2011-11-11
Close.  I had to this because redirection and sudo don't always play nice together.  But then it worked like a charm.

```

sudo sh -c "echo 1 > /proc/sys/net/ipv4/ip_forward"

```

---

### Post by Dangertux on 2011-11-11
> **jbm222 said:**
> Close.  I had to this because redirection and sudo don't always play nice together.  But then it worked like a charm.

```

sudo sh -c "echo 1 > /proc/sys/net/ipv4/ip_forward"

```

Yep you're right, glad it worked out for you though.

---

