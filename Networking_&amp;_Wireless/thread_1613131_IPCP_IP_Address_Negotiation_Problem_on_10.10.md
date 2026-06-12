---
title: "IPCP IP Address Negotiation Problem on 10.10"
date: 2010-11-04
forum: Networking &amp; Wireless
---

### Post by TrevorHill on 2010-11-04
I recently installed 10.10 to use nmcli to automate the activation and deactivation of PPPoE connections. 
 
The nmcli command line interface works very well, but since installing 10.10 my PPPoE IPCP IP address negotiation fails. The ppp interface that is brought up has an IP address that was received earlier by the eth interface from a DHCP server, not the IP offered by the PPPoE server. 
 
Previously I was using 10.04 and there the address negotiation was fine. Any advice as to what I need to configure, or if any PPPD defaults have changed in 10.10, or if there is a problem in 10.10, will be much appreciated. I configure my DSL inetrfaces using the NetworkManager application.
 
 
SOLUTION  uncomment noipdefault in etc/ppp/options

---

