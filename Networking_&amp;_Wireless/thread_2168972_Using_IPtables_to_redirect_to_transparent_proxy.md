---
title: "Using IPtables to redirect to transparent proxy"
date: 2013-08-20
forum: Networking &amp; Wireless
---

### Post by bytesoup on 2013-08-20
Hi folks,

I recently setup a transparent proxy using help from some folks on [this thread]("http://ubuntuforums.org/showthread.php?t=2167654"). I completed the setup ok and marked the thread as solved as I had essentially completed what I wanted to do. However some client PCs still weren't getting internet connections ok and on checking the machines I saw the gateway IP was set to the proxy and the DNS was set to open DNS server which is what I wanted to.

I ran tcpdump on the server and I could see requests coming into the server for websites but nothing getting returned. I checked iptables using "iptables -L" but I dont see the rule I added for forwarding?

I added the following rule:

```
sudo iptables -t nat -A PREROUTING -i eth0 -p tcp --dport 80 -j REDIRECT --to-ports 8080
```

I check iptables:

```
$ sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         


Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         


Chain OUTPUT (policy ACCEPT)
target     prot opt source  
```
 
Do I need to configure other iptables rules? **Note the server only has one interface** so im trying to route in port 80 and out to port 8080 (dansguardian) which is then setup to route out to port 3128 to squid. Also note that if a client is configured with the proxy on port 8080 it will work ok, so this is why I suspect iptables.

---

### Post by bytesoup on 2013-08-20
Here is an example tcpdump output, I connected my Andriod phone to the network with the router DHCP turned off and the DHCP server turned on, on the server. The router is at 192.168.0.1, the server is on 192.168.0.11. The .26 address is my phone requesting the webpage. We can see that the server is not returning the packets back to the client. I also do not see requests in the /var/log/dansguardian/access.log so this tells me that iptables does not seem to be forwarding packets.

```
sudo tcpdump -n src 192.168.0.26 or dst 192.168.0.26
tcpdump: verbose output suppressed, use -v or -vv for full protocol decode
listening on eth0, link-type EN10MB (Ethernet), capture size 65535 bytes


09:05:51.027197 IP 192.168.0.26.38124 > 184.173.136.75.5222: Flags [S], seq 816518151, win 64240, options [mss 1460,sackOK,TS val 18468428 ecr 0,nop,wscale 3], length 0
09:05:51.027274 IP 192.168.0.26.38124 > 184.173.136.75.5222: Flags [S], seq 816518151, win 64240, options [mss 1460,sackOK,TS val 18468428 ecr 0,nop,wscale 3], length 0
09:05:54.027120 IP 192.168.0.26.38124 > 184.173.136.75.5222: Flags [S], seq 816518151, win 64240, options [mss 1460,sackOK,TS val 18468729 ecr 0,nop,wscale 3], length 0
09:05:54.027149 IP 192.168.0.11 > 192.168.0.26: ICMP redirect 184.173.136.75 to host 192.168.0.1, length 68
09:05:54.027157 IP 192.168.0.26.38124 > 184.173.136.75.5222: Flags [S], seq 816518151, win 64240, options [mss 1460,sackOK,TS val 18468729 ecr 0,nop,wscale 3], length 0
09:05:59.033142 ARP, Request who-has 192.168.0.26 tell 192.168.0.11, length 28
09:05:59.062488 ARP, Reply 192.168.0.26 is-at 7c:61:93:f3:b4:6a, length 46



```

---

### Post by Doug S on 2013-08-20
To list the iptables rules in your nat table you would need to use:```
sudo iptables -t nat -L
```You could also list the entire iptables with```
sudo iptables-save -c
```Your phone seems to be trying to access port 5222 of 184.173.136.75 and therefore would not hit your rule. Since you have made 192.168.0.11 the gateway, I think it needs to know what to do with packets that are not destined for port 80. (It will take me awhile to recall and figure out the needed rules. I'll come back and edit this post if and when I do.)

---

### Post by bytesoup on 2013-08-20
> **Doug S said:**
> To list the iptables rules in your nat table you would need to use:```
sudo iptables -t nat -L
```You could also list the entire iptables with```
sudo iptables-save -c
```


Thanks, this is just what I needed, I found I had many lines of these:

```
Chain PREROUTING (policy ACCEPT)
target     prot opt source               destination         
REDIRECT   tcp  --  0.0.0.0/0            0.0.0.0/0           tcp dpt:80 redir ports 8080 
REDIRECT   tcp  --  0.0.0.0/0            0.0.0.0/0           tcp dpt:80 redir ports 8080 
REDIRECT   tcp  --  0.0.0.0/0            0.0.0.0/0           tcp dpt:80 redir ports 8080 
REDIRECT   tcp  --  0.0.0.0/0            0.0.0.0/0           tcp dpt:80 redir ports 8080 
REDIRECT   tcp  --  0.0.0.0/0            0.0.0.0/0           tcp dpt:80 redir ports 8080 
REDIRECT   tcp  --  0.0.0.0/0            0.0.0.0/0           tcp dpt:80 redir ports 8080 

```

I used the following to remove the excess

```
sudo iptables -t nat -D PREROUTING -i eth0 -p tcp --dport 80 -j REDIRECT --to-ports 8080
```

> **Doug S said:**
> 
Your phone seems to be trying to access port 5222 of 184.173.136.75 and therefore would not hit your rule. Since you have made 192.168.0.11 the gateway, I think it needs to know what to do with packets that are not destined for port 80. (It will take me awhile to recall and figure out the needed rules. I'll come back and edit this post if and when I do.)

Yes, silly me, its not a port 80 request. I'll try this again with a normal client PC and a browser. I think the Andriod phone might be using some google location service in its request and so its not getting through, so essentially the iptables is doing the right job. It would be interesting to see what requests are made outside of port 80 actually. Perhaps I can drop these to a log file?

---

