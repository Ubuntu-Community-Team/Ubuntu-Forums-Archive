---
title: "Iptables connection forwarding doesn't work from remote PCs."
date: 2009-07-23
forum: Networking &amp; Wireless
---

### Post by ratchet_XIII on 2009-07-23
Hi
 
Some friends and I have a root-server (IP = 91.121.X.X) and one account on a SMB server.
The SMB server allows multiple connections but only from a single IP so we would like to use our root-server to forward the connections to the SMB-server.
 
Currently we use Firestarter to manage the normal rules and this script for the con. forwarding:
 
YourIP=91.121.X.X
YourPort=41000
TargetIP=216.X.X.X
TargetPort=139
 
sudo iptables -t nat -A PREROUTING --dst $YourIP -p tcp --dport $YourPort -j DNAT \
--to-destination $TargetIP:$TargetPort
sudo iptables -t nat -A POSTROUTING -p tcp --dst $TargetIP --dport $TargetPort -j SNAT \
--to-source $YourIP
sudo iptables -t nat -A OUTPUT --dst $YourIP -p tcp --dport $YourPort -j DNAT \
--to-destination $TargetIP:$TargetPort
 
However this only works from our root-server itself. On the root-server I can connect to itself on port 41000 and it forwards it to the SMB server without problems. I opened the Port 41000 with firestarter, but it still doesn't work from our home PCs.
We really don't know whats wrong.
 
Can somebody please help us?
 
Thx

---

