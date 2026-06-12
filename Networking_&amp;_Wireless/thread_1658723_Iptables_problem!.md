---
title: "Iptables problem!"
date: 2011-01-03
forum: Networking &amp; Wireless
---

### Post by mighty mouse on 2011-01-03
Hi All
 
I am facing a problem in IPtables. I am unable to ssh into the server after it reboots inspite of saving TP/ssh rule in my iptables config.
 
Here is the output of iptables -L
 
>  
Chain INPUT (policy DROP)
target prot opt source destination
ACCEPT tcp -- anywhere anywhere tcp dpt:ssh
ACCEPT all -- anywhere anywhere
ACCEPT all -- anywhere anywhere state RELATED,ESTABLISHED
input_ext all -- anywhere anywhere
input_ext all -- anywhere anywhere
input_ext all -- anywhere anywhere
LOG all -- anywhere anywhere limit: avg 3/min burst 5 LOG level warning tcp-options ip-options prefix `SFW2-IN-ILL-TARGET '
DROP all -- anywhere anywhere
Chain FORWARD (policy DROP)
target prot opt source destination
LOG all -- anywhere anywhere limit: avg 3/min burst 5 LOG level warning tcp-options ip-options prefix `SFW2-FWD-ILL-ROUTING '
Chain OUTPUT (policy ACCEPT)
target prot opt source destination
ACCEPT all -- anywhere anywhere
ACCEPT all -- anywhere anywhere state NEW,RELATED,ESTABLISHED
LOG all -- anywhere anywhere limit: avg 3/min burst 5 LOG level warning tcp-options ip-options prefix `SFW2-OUT-ERROR '
Chain forward_ext (0 references)
target prot opt source destination
Chain input_ext (3 references)
target prot opt source destination
DROP all -- anywhere anywhere PKTTYPE = broadcast
ACCEPT icmp -- anywhere anywhere icmp source-quench
ACCEPT icmp -- anywhere anywhere icmp echo-request
ACCEPT icmp -- anywhere anywhere state RELATED,ESTABLISHED icmp echo-reply
ACCEPT icmp -- anywhere anywhere state RELATED,ESTABLISHED icmp destination-unreachable
ACCEPT icmp -- anywhere anywhere state RELATED,ESTABLISHED icmp time-exceeded
ACCEPT icmp -- anywhere anywhere state RELATED,ESTABLISHED icmp parameter-problem
ACCEPT icmp -- anywhere anywhere state RELATED,ESTABLISHED icmp timestamp-reply
ACCEPT icmp -- anywhere anywhere state RELATED,ESTABLISHED icmp address-mask-reply
ACCEPT icmp -- anywhere anywhere state RELATED,ESTABLISHED icmp protocol-unreachable
ACCEPT icmp -- anywhere anywhere state RELATED,ESTABLISHED icmp redirect
reject_func tcp -- anywhere anywhere tcp dpt:ident state NEW
LOG all -- anywhere anywhere limit: avg 3/min burst 5 PKTTYPE = multicast LOG level warning tcp-options ip-options prefix `SFW2-INext-DROP-DEFLT '
DROP all -- anywhere anywhere PKTTYPE = multicast
LOG tcp -- anywhere anywhere limit: avg 3/min burst 5 tcp flags:FIN,SYN,RST,ACK/SYN LOG level warning tcp-options ip-options prefix `SFW2-INext-DROP-DEFLT '
LOG icmp -- anywhere anywhere limit: avg 3/min burst 5 LOG level warning tcp-options ip-options prefix `SFW2-INext-DROP-DEFLT '
LOG udp -- anywhere anywhere limit: avg 3/min burst 5 LOG level warning tcp-options ip-options prefix `SFW2-INext-DROP-DEFLT '
LOG all -- anywhere anywhere limit: avg 3/min burst 5 state INVALID LOG level warning tcp-options ip-options prefix `SFW2-INext-DROP-DEFLT-INV '
DROP all -- anywhere anywhere
Chain reject_func (1 references)
target prot opt source destination
REJECT tcp -- anywhere anywhere reject-with tcp-reset
REJECT udp -- anywhere anywhere reject-with icmp-port-unreachable
REJECT all -- anywhere anywhere reject-with icmp-proto-unreachable
 

 
Everytime i reboot the server i have to manually run : iptables -I INPUT -p tcp -m tcp --dport 22 -j ACCEPT and after which i am able to remote login to my server.
 
How can i not do this manually and abe to remote lgoin into the server?
 
Thanks in advance ... :)

---

