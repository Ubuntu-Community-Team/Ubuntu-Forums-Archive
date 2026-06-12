---
title: "Hard Code default route"
date: 2011-08-16
forum: Networking &amp; Wireless
---

### Post by Seq on 2011-08-16
I've recently set up OpenVPN on my machines. The goal was to ensure I have secure connections even over insecure (wifi) links. This seems to work pretty well: If I enable the VPN in network manager, my default route gets set to one that routes over the VPN. Yay.

My potential problem is that if my VPN disconnects and I don't notice, or if I neglect to manually start it, I'm back to using insecure wifi. I'd like to have my network connections secure by default (that is, secure or non-existent).

[LIST]
[*]One approach would be to override the default route to *always* have it use my VPN gateway (so if I'm not on VPN, I get no internet). I'd probably have to make a route to access my server via the old gateway (since it is on the internet), and possibly an entry for the network's DNS server (so I can resolve my server's address).

I'm thinking my best bet to do that is to just do some basic analysis and insert/remove routes. It would probably be in `/etc/network/if-up.d/` or `/etc/NetworkManager/dispatchers.d/`

[*]Another approach is to use iptables to only allow communication over the VPN, with again the same exceptions as routing above (and probably one to allow local network communication).
[/LIST]

Any thoughts? Anybody else attempting a secure-by-default network configuration?

---

