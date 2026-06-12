---
title: "OpenVPN server and client at the same time?"
date: 2010-10-26
forum: Networking &amp; Wireless
---

### Post by eldaria on 2010-10-26
Hello I was wondering if anyone with OpenVPN experience has tried this.

I have an Ubuntu server that is currently running Ubuntu 8.10.

I was thinking of making it a VPN server for my iPhone and also for my laptop whenever i'm outside and need to access internet over insecure wireless networks.

Now that part should be easy I found several guides on how to configure OpenVPN server, as well as enabling clients on iPhone, and OSX.

However, the things is that my server is currently a OpenVPN client also, I have a paid tunnel set up to bypass my ISP blocking incoming traffic on various ports.

Is it possible to keep this setting but still enabling a VPN server?

Essentially causing traffic from my external device to go in through my tunnel to the VPN server, and then out through the external VPN provider.

Does it make sense? :-)

Kind regards.
Brian Levinsen

---

### Post by SeijiSensei on 2010-10-26
Sure.  Just set up each tunnel on a separate port address.  I have a box running half-a-dozen or more tunnels in both directions.  They all use unique port numbers in the 20000-60000 range.

Whether you can route the traffic out to the Internet depends on whether you have a firewall enabled.  One simple solution is to use rules like:

```

iptables -A INPUT   -j ACCEPT -i tun0
iptables -A FORWARD -j ACCEPT -i tun0 
iptables -A OUTPUT  -j ACCEPT -o tun0
iptables -A INPUT   -j ACCEPT -i tun1
iptables -A FORWARD -j ACCEPT -i tun1
iptables -A OUTPUT  -j ACCEPT -o tun1

```

All these rules come before the MASQUERADE rule for outbound traffic.

---

### Post by eldaria on 2010-10-26
Thanks, I will give it a try.

---

