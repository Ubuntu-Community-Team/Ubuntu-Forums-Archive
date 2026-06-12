---
title: "iptables help"
date: 2009-07-25
forum: Networking &amp; Wireless
---

### Post by SGanesh on 2009-07-25
Dear All,

Our question is regarding iptables and networking with Firewall.

Please kindly help me with this problem, or forward me to the previous posts with the similar solutions, thanking you all

we have a linux box doing a firewall, proxy - it has 3 NICs

eth0 - wan ip - static IP - provided by ISP

eth1 - lan 1 ip - 10.0.0.200 - this is the gateway for the lan Clients(10.0.0.0)

eth2 - lan2 ip - 192.168.0.200 - this connects the 2nd Lan - where internet is not allowed


We are comfortable with NAT, port forwarding from the Internet,

i.e. 
1.) Internet is accessible from eth1 connected terminals

      2.) From WAN, clients are connecting to port 21, and 5900 to the terminals connected with eth1 connection.


Now, the requirement is we would like to connect a single terminal 10.0.0.211 on eth1 with a terminal 192.168.0.211 on eth2 through port 21 for some FTP access


(eth1) 10.0.0.211 ----> (eth2) 192.168.0.211:21


Please help us in creating IPTables rules for this requirement

Currently from the linux firewall box

1.) we could able to ping 192.168.0.211  (thru eth2- 192.168.0.200)
2.) also ping 10.0.0.211 (thru eth1- 10.0.0.200)

3.) But we cannot telnet to port 21 on 192.168.0.211 from eth1 connected 10.0.0.211

Kindly help us to solve this problem,

Thanks / S Ganesh

---

