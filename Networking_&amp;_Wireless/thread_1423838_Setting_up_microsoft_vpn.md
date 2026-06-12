---
title: "Setting up microsoft vpn"
date: 2010-03-07
forum: Networking &amp; Wireless
---

### Post by hamid2c on 2010-03-07
Hi,

I'm using ubuntu 8.10.
So far, I was unable to setup a connection to the vpn we used in my university. However, I setup the connection in windows xp easily.

To setup a vpn connection in ubuntu, First I installed network-manager-pptp and all its dependencies then clicked on the networkmanager icon and tried several different configurations under vpn tab but none of them worked.

However, I could connect to the vpn by using virtual box and running windows xp on top of it (network: bridged).

To setup the vpn connection in windows xp, I simply apply all the default options available in the new connection dialog for setting up a vpn and uncheck 'Require data encryption box' in  the connection's property page.

Details of my vpn connection in windows xp are:
Default name: WAN miniport (pptp)
Device type: vpn
Server type: PPP
Transports: TCP/IP
Authentication: MD5 CHAP
Compression: MPPC
PPP multilink framing: off

Thanks,
Hamid

---

