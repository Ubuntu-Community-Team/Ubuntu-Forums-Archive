---
title: "network-manager-vpnc doesn't add default route through tun0"
date: 2012-05-19
forum: Networking &amp; Wireless
---

### Post by _Groove_ on 2012-05-19
I had the Network Manager applet working with VPNC up until a couple of releases ago; it broke after an upgrade and I've been using the command-line vpnc client since then but I'd like to get the applet fixed.

Basics:
 * Xubuntu 12.04, but was previously Ubuntu 11.10 and had the same issues.
 * VPN does connect successfully (with respect to IPSec negotiation etc).
 * Original default route through my wireless access point remains in place.
 * Two routes are inserted via tun0, which come from the environment variables VPN_IP4_ROUTE_0 and VPN_IP4_ADDRESS_0 respectively, but these only cover the VPN endpoint segments.
 * In syslog there is the line:
May 19 12:12:10 localhost NetworkManager[819]: <info> Forbid Default Route: yes
 * "Ignore automatically obtained routes" is NOT enabled.
 * "Use this connection only for resources on its network" is NOT enabled.

When connecting with the vpnc command-line client:
 * Default route goes through tun0
 * Route to VPN endpoint is inserted via my wireless access point IP.

I attempted to fix the issue by adding a small script in /etc/network/if-up.d that changes the default route when the VPN is brought up, but the highly dynamic nature of Network Manager means that various other events destroy this and it soon goes back to my wireless access point IP.

I'm not sure if the "Forbid Default Route: yes" message is coming from the remote end, or from Network Manager configuration. In any case, vpnc doesn't seem to suffer from the same problem so it should be possible to override somewhere. Any ideas?

Alternatively, is there a better way of fixing the routing outside of Network Manager that doesn't get mangled by every event that NM processes?

---

### Post by _Groove_ on 2012-05-19
OK, after a read through some of the code and the following bug report it seems to be by design:
[https://bugzilla.gnome.org/show_bug.cgi?id=621698](https://bugzilla.gnome.org/show_bug.cgi?id=621698)

So if the remote VPN server sends back *any* routes (which mine does, although unfortunately they are useless to me) it will override any user configuration, not use the default route and just configure what was sent from the server.

Therefore I either have to make use of these routes and other manually configured routes or get the VPN admins to fix their config.

---

### Post by _Groove_ on 2012-05-19
Also FYI it's in commit 5238aa410764f58c615465da3767d73571fc34d4 of NetworkManager.

---

