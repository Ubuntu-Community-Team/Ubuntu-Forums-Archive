---
title: "PPTP VPN routing"
date: 2010-04-04
forum: Networking &amp; Wireless
---

### Post by Robby710 on 2010-04-04
Hello,

I am trying to connect to a WIN2K3 pptp VPN.  I can connect fine, but I would like to be able to only access a share on this drive.  I would like all the other internet traffic to be routed locally, not through the vpn.   When I connect to the VPN the internet does not work locally, but I can ping the address 192.168.2.200 and 192.168.2.201.

In the windows pptp client I would uncheck "Use default gateway on remote network" in the TCP/IP settings.  I am not sure what the equivalent method for Ubuntu is.  I am assuming I need to add some entries in a routing table somewhere, but I am stumpted.
I included a snipped from the syslog.

Apr  4 15:08:47 linux NetworkManager: <info>  VPN connection 'XXXXX' (IP Config Get) reply received.
Apr  4 15:08:47 linux NetworkManager: <info>  VPN Gateway: XXXXX
Apr  4 15:08:47 linux NetworkManager: <info>  Tunnel Device: ppp0
Apr  4 15:08:47 linux NetworkManager: <info>  Internal IP4 Address: 192.168.2.201
Apr  4 15:08:47 linux NetworkManager: <info>  Internal IP4 Prefix: 32
Apr  4 15:08:47 linux NetworkManager: <info>  Internal IP4 Point-to-Point Address: 192.168.2.200
Apr  4 15:08:47 linux NetworkManager: <info>  Maximum Segment Size (MSS): 0
Apr  4 15:08:47 linux NetworkManager: <info>  Internal IP4 DNS: 208.67.222.222
Apr  4 15:08:47 linux NetworkManager: <info>  Internal IP4 DNS: 208.67.220.220
Apr  4 15:08:47 linux NetworkManager: <info>  DNS Domain: '(none)'


Any help is appreciated, thanks!

---

