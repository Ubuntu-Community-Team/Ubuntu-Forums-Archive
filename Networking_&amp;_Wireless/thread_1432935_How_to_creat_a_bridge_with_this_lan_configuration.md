---
title: "How to creat a bridge with this lan configuration"
date: 2010-03-18
forum: Networking &amp; Wireless
---

### Post by Duarte Azevedo on 2010-03-18
So in my school I have a router that receives internet, that router is connected with the main switch. That switch connects with the server and the other switches of the classrooms. The server have DHCP and gives IPs to all machines in the network. And I needed to implement a proxy server(between the router and the main switch by bridge) in the network to filter the internet trafic. So I started by creating a proxy server and testing it between a terminal and a classroom switch, it was really easy to creat: just serched a bit and added the following lines in /etc/network/interfaces
<code>
auto br0 inet dhcp
bridge_ports eth0 eth1
</code>

everytime i wanted to start the bridge i just needed to type: ifup br0 in the console, and the bridge was created, the terminal started to have internet and I could go to my shared folders in the server,etc. So, I think that was easy because the dhcp and the internet "come" from the same interface (in this case eth0) but now that I have configured my proxy, I wanted to finally put it in between the router and the main switch.
I think the solution is just telling the SO from what interface the IP is given, and what interface the internet comes, I just dont know what to put in /etc/network/interfaces to it recognize that the dhcp comes from eth1 and the internet comes from eth0 and bridge it by simply typing "ifup br0" in the console! Thanks to whoever can help.

---

