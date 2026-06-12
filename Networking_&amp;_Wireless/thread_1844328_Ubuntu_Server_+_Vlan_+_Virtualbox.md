---
title: "Ubuntu Server + Vlan + Virtualbox"
date: 2011-09-14
forum: Networking &amp; Wireless
---

### Post by 03it503 on 2011-09-14
Hello all

I followed the post below to configure the network but it doesn't work the way I want.

My server is connected to switch over trunk line and I want to put server on vlan4 and all vms in virtualbox in vlan5 

Router (dd-wrt) -->(trunk) Switch(Trunk) --> Server (virtualbox) --> VM1,vm2

host server with static ip in vlan4

I followed the steps from the post below it only works for vlan4 e.g. when I start any vm with bridged with br4 and manual vlan4 ip it communicates over the network but the problem is when I assign vlan5 ip with br5 it doesn't communicate over the network, no packets are received 

[http://www.tolaris.com/2010/02/20/vlans-bridges-and-virtual-machines/](http://www.tolaris.com/2010/02/20/vlans-bridges-and-virtual-machines/)

Please help me to troubleshoot this issue.

Thank you very much in advance

---

