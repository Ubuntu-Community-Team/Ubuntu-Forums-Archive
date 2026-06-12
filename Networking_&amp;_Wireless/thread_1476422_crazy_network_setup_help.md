---
title: "crazy network setup help"
date: 2010-05-07
forum: Networking &amp; Wireless
---

### Post by dpeterson3 on 2010-05-07
Hello. I have a crazy network I have been tasked with setting up and I am not sure what I am doing wrong. Here is the network scheme I need to setup.
> 
10.0.*.* — Robotics Local Network 
[LIST]
[*]10.0.0.* — Computers that stay in the lab, network equipment, printer
[LIST]
[*]10.0.0.1 — Gateway and authoritative DHCP server
[*]10.0.0.2 — Wireless Bridge
[*]10.0.0.3 — Printer
[*]10.0.0.4 — First Ethernet switch
[/LIST]
[*]10.0.1.* — Computers
[LIST]
[*]10.0.1.1 — Sun Machine
[*]10.0.1.2 — Aapel
[*]10.0.1.4 — Windows Box
[*]10.0.1.200+ — Computers visiting the lab (our laptops)
[/LIST]
[*]10.0.100+.* — Robot subnets
[LIST]
[*]10.0.100.* — [Aluminator]("http://robotics.mst.edu/trac/wiki/Aluminator") subnet
[LIST]
[*]10.0.100.1 — CPU1/backup DHCP server
[*]10.0.100.11 — aluminator-1 (Larry)
[*]10.0.100.2 —  aluminator-2 (Curly)
[*]10.0.100.3 —  aluminator-3 (Moe)
[*]10.0.100.4–8 — expansion
[*]10.0.100.9 — Motion Control Sensor Platform
[*]10.0.100.10 — Elmo Maestro controller (if present)
[*]10.0.100.200+ — Reserved for laptops at competition
[/LIST]
[*]10.0.101.* — [StereoOpticon]("http://robotics.mst.edu/trac/wiki/StereoOpticon") subnet
[LIST]
[*]10.0.101.1 — [StereoOpticon]("http://robotics.mst.edu/trac/wiki/StereoOpticon") CPU1/backup DHCP server
[*]...
[*]10.0.101.200+ — Reserved for Laptops at Competition
[/LIST]
[*]10.0.102.* — [MiniPrime?]("http://robotics.mst.edu/trac/wiki/MiniPrime") subnet
[LIST]
[*]10.0.102.1 — [MiniPrime?]("http://robotics.mst.edu/trac/wiki/MiniPrime") CPU/gumstix
[*]10.0.102.200+ — Laptops
[/LIST]
[/LIST]
[/LIST]

I have DHCP3-server up and running. I have attached a copy of its config file. The server looks like this
> 
eth0 --> wan
eth1 -->DHCP gateway (static address 10.0.0.1)

As it is, the machines listed as hosts to get the same address every time can get their addresses just fine. 

Problem 1: Nothing else (listed as visiting computers) can connect to the DHCP server, so I guess it has something to do with how I defined the subnets, but I am not sure what. I have setup networks before but never with multiple subnets. Could I get some help there please?

Problem 2: The machines that can get addresses can not access the internet. I have rules in the IP tables to forward everything, but I can't ping any outside address. I think it probably has something to do with my configuration also.

output of iptables -L
```

Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            
           all  --  anywhere             anywhere            
ACCEPT     all  --  anywhere             anywhere            

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destinati

```

Thanks in advance. Sorry about the long post.

---

