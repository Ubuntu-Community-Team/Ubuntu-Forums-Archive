---
title: "VPN server"
date: 2011-01-12
forum: Networking &amp; Wireless
---

### Post by frankhovin on 2011-01-12
I'm trying to set up a VPN server on a 9.04 machine, and I've ALLMOST got it. Here's what I've done:

1. Installed pptpd

2. In /etc/pptpd.conf, added:
localip 10.0.0.2 (the VPN server)
remoteip 10.0.0.150-155

3. In /etc/ppp/options:
ms-dns 81.167.36.3
ms-dns 81.167.36.11
(The ISP name servers)

4. Created user account and password in /etc/ppp/chap-secrets:
user1 pptpd a-strong-password *
user2 pptpd another-strong-password *

5. In /etc/sysctl.conf:
net.ipv4.conf.default.forwarding=1

$ sysctl -p to activate the new setting

6. Forwarded port 1723 in the router/firewall to the VPN server (10.0.0.2). Since it's a D-Link router, it is supposed to automatically forward GRE 47 to the PPTP server, so I haven't set up that.

- Restarted the pptpd server

Now, I am able to connect from a remote Ubuntu machine, using

```

pptpsetup --create <connectionname> --start --username user1 --server <router-ip> --encrypt

```

However, I cannot ping anything else on the LAN than the VPN server (10.0.0.2). Not even the router/gateway (10.0.0.1) from the (connected) remote machine.

Anyone got any ideas?

Another question: When I'm connected to a VPN server, shouldn't the VPN connection (ppp0) override the "normal" internet connection of the connecting machine, so that when I access the internet from the connecting machine, I'm in fact connecting through the VPN server, hence using the VPN server's gateway?

---

