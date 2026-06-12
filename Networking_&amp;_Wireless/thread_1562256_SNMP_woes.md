---
title: "SNMP woes"
date: 2010-08-27
forum: Networking &amp; Wireless
---

### Post by Sabir_101 on 2010-08-27
Hello!

I'm currently trying to get my Ubuntu 9.04 server (IP 10.0.0.23) to talk to my Netgear GS748T switch (IP 10.10.128.1) via the SNMP protocol. 
I've installed snmpd on the server and am now using snmpwalk to send requests to the switch for testing. 
Trouble is, I keep getting "Timeout: No Response from 10.10.128.1" error back, so I set up a tcpdump on the eth0 interface to monitor what is coming back from the requests:

snmpwalk -c public -v 1 10.10.128.1

15:57:32.157708 IP 10.10.128.1.1034 > 10.0.0.23.162:  Trap(90)  .1.3.6.1.4.1.4526.100.4.1 10.10.128.1 authenticationFailure 193100[|snmp]
15:57:33.158549 IP 10.10.128.1.1034 > 10.0.0.23.162:  Trap(90)  .1.3.6.1.4.1.4526.100.4.1 10.10.128.1 authenticationFailure 193200[|snmp]
15:57:34.159697 IP 10.10.128.1.1034 > 10.0.0.23.162:  Trap(90)  .1.3.6.1.4.1.4526.100.4.1 10.10.128.1 authenticationFailure 193300[|snmp]
15:57:35.161242 IP 10.10.128.1.1034 > 10.0.0.23.162:  Trap(90)  .1.3.6.1.4.1.4526.100.4.1 10.10.128.1 authenticationFailure 193400[|snmp]
15:57:36.161721 IP 10.10.128.1.1034 > 10.0.0.23.162:  Trap(90)  .1.3.6.1.4.1.4526.100.4.1 10.10.128.1 authenticationFailure 193500[|snmp]
15:57:37.162836 IP 10.10.128.1.1034 > 10.0.0.23.162:  Trap(90)  .1.3.6.1.4.1.4526.100.4.1 10.10.128.1 authenticationFailure 193600[|snmp]

Timeout: No Response from 10.10.128.1

What's worrying me is why I'm getting a "timeout" response when clearly the switch is sending back an "authenticationFailure" trap (and the server is receiving it or tcpdump wouldn't show it). I have the switch set up so that the community is set to public and the server's ip address is in the management list.

Can anyone help?

---

