---
title: "Forwarded Packets Getting Dropped Somewhere"
date: 2011-12-22
forum: Networking &amp; Wireless
---

### Post by whchapman on 2011-12-22
I am trying to use iptables to forward port 8888 from my server (11.11.11.11) to my home PC (22.22.22.22). The problem is the packets are not reaching my home PC, despite the fact that tshark shows they are being sent. 

The server, which is a VPS, runs Ubuntu 11.04 and the home PC runs 10.04. Neither machine is behind a NAT or firewall.

I ran the following iptables commands on the server to set up forwarding.

```
root@server# iptables -t nat --flush
root@server# iptables -t filter --flush
root@server# iptables --table nat -p tcp --destination-port 8888 --append PREROUTING -j DNAT --to-destination 22.22.22.22:8888
```My default policies are ACCEPT. Here are the filter and nat tables.

```
root@server# iptables -t nat --list
Chain PREROUTING (policy ACCEPT)
target     prot opt source               destination         
DNAT       tcp  --  anywhere             anywhere            tcp dpt:8888 to:22.22.22.22:8888 

Chain POSTROUTING (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         

root@server# iptables -t filter --list
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
```I should also mention that forwarding is enabled in the kernel.
```
root@server# cat /proc/sys/net/ipv4/ip_forward
1
```The problem is simply that the forwarding does not work. I can use netcat to connect directly to 22.22.22.22:8888, but when I attempt to connect to 11.11.11.11:8888, the connection times out.

I have used tshark to troubleshoot the problem. It appears the iptables command is working, but for some reason the packets never make it to my home PC. Below are the packets captured by tshark during a failed connection attempt from 33.33.33.33.

On the server:

```
root@server# tshark -i venet0 -f "port 8888"
tshark: Lua: Error during loading:
 [string "/usr/share/wireshark/init.lua"]:45: dofile has been disabled
Running as user "root" and group "root". This could be dangerous.
Capturing on venet0
  0.000000 33.33.33.33 -> 11.11.11.11 TCP 54278 > ddi-tcp-1 [SYN] Seq=0 Win=5840 Len=0 MSS=1460 SACK_PERM=1 TSV=22127814 TSER=0 WS=7
  0.000032 33.33.33.33 -> 22.22.22.22 TCP 54278 > ddi-tcp-1 [SYN] Seq=0 Win=5840 Len=0 MSS=1460 SACK_PERM=1 TSV=22127814 TSER=0 WS=7
2 packets captured
```And on the home PC:

```
root@home# tshark -i eth0 -f "port 8888"
Running as user "root" and group "root". This could be dangerous.
Capturing on eth0
0 packets captured

```This is where I hit a dead end in my troubleshooting. Packets appear to be leaving the server destined for my home PC, yet they never make it there. I have no idea what could be getting in the way, or how to research it.

---

### Post by whchapman on 2011-12-23
Alternatively, if anyone could help direct me to a more appropriate forum, I'd appreciate it.

---

### Post by whchapman on 2011-12-27
Found the solution. The outgoing packets need to have their source address rewritten to the IP of the server.

This requires an extra iptables rule. My new iptables script, which now properly forwards port 80 from 11.11.11.11 to 22.22.22.22 is below. 

```
#!/bin/bash
# empty the filter and nat tables
iptables -t filter --flush
iptables -t nat --flush
# rewrite the destination ip to my home PC before routing
iptables -t nat -A PREROUTING -p tcp -i venet0 --dport 80 -j DNAT --to-destination 22.22.22.22:80
# rewrite the source ip to this server after routing (so packets make it back)
iptables -t nat -A POSTROUTING -p tcp --dport 80 -j SNAT --to 11.11.11.11
```I'm still not sure why the forwarded TCP SYN packets weren't making it to their destination. It makes sense that the response packets would get misdirected since they would be sent to the host that initiated the connection, rather than through my server. But the initial connection request packets should have arrived properly. At this point, my working theory is that some router between my server and my home PC was dropping the packets because their source address did not match the subnet corresponding to their incoming interface (which would look like spoofing).

I also don't understand why this extra rule didn't appear in any of the port forwarding tutorials I found online. I deduced it from my own understanding of networking - not from any source on the Internet. This leaves me a bit nervous that I might still be missing something.

And finally, I'm still looking for a good system admin or networking forum. Any suggestions are welcome.

---

