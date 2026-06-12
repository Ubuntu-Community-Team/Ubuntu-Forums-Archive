---
title: "Transmission not using VPN connection"
date: 2013-04-14
forum: Networking &amp; Wireless
---

### Post by mat28590 on 2013-04-14
Hello

I have a server at home running Ubuntu 12.04 for the purpose of downloading via transmission-daemon.
My home server is connected to my VPN provider via openVPN.
ifconfig shows RX bytes for eth0 is much greater than RX Bytes for tun0.
Considering the vpn was connected right after boot, this seems to indicate to me that my downloads via transmission are not being transferred over the vpn connection.

All inbound connections are blocked by my firewall, so the only peers I should be connected to, are those to whom I initiated the connection, and therefore should be routed via my vpn.

If I ssh to my server and mtr google.com, I can see I am being routed via the vpn.

So my question is, why is all my HTTP traffic (mtr) being directed via vpn, but my bit-torrent (transmission) traffic is not? 

Any help would be much appreciated.

---

### Post by mat28590 on 2013-04-14
On the server I did:

```
sudo route add default dev tun0
```

This seems to have solved this issue and all traffic is now being routed by via the vpn.

---

