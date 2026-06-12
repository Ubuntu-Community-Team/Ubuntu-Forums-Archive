---
title: "VPN auto dial upon request"
date: 2011-01-17
forum: Networking &amp; Wireless
---

### Post by Blues- on 2011-01-17
I have a server running as a gateway for several computers ..
Is it possible to make the server automatically connect to a remote server via VPN when the server gets requests for the IP range that belongs to the remote server ?

scenario ..
- 10.0.10.45 asks the gateway (10.0.10.1) for webserver 192.168.253.23
- the gateway (10.0.10.1) initiates VPN dial to the remote server ..
- the gateway (10.0.10.1) routes the traffic for 192.168.253.* through the vpn interface
- the gateway (10.0.10.1) disconnects the VPN connection after 10 min idle time 


Is this possible ?

---

### Post by SeijiSensei on 2011-01-18
It ***might*** be possible if you "wrap" the VPN server daemon with [xinetd]("http://www.xinetd.org/"), though I'm not sure whether it will stay up this way.

A quick browsing of Google brings me to [this posting]("http://www.nslu2-linux.org/wiki/HowTo/SetUpOpenVPNServer") which provides code to use xinetd in this fashion.

---

