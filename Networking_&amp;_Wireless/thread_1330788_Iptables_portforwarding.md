---
title: "Iptables portforwarding"
date: 2009-11-18
forum: Networking &amp; Wireless
---

### Post by Dosshell on 2009-11-18
Hi!
I want to forward the port 3000 from internet to my desktop machine. I have an Ubuntu NAT between the Desktop and the Internet.

Internet---->[eth0] Ubuntu NAT [eth1 192.168.0.1]----->[192.168.0.50] Win XP Desktop
eth0 = Internet
eth1 = LAN

I have tried the following script in "/etc/rc.local"

```
#port forwarding ---DOES NOT WORK---
/sbin/iptables -t nat -A PREROUTING -i eth0 -p tcp --dport 3000 -j DNAT --to 192.168.0.50:3000
/sbin/iptables -A FORWARD -p tcp --destination-port 3000 -j ACCEPT

#block VNC from internet
/sbin/iptables -I INPUT -i eth0 -p tcp --dport 5900 -j REJECT --reject-with tcp-reset

#NAT
/sbin/iptables -P FORWARD ACCEPT
/sbin/iptables --table nat -A POSTROUTING -o eth0 -j MASQUERADE

exit 0
```
The VNC block and the NAT works great but not the port forwarding. Any clue why?

---

### Post by eremyja on 2009-11-18
try turning off iptables and making sure your isp isnt blocking that port

---

### Post by Dosshell on 2009-11-18
If I connect directly to the internet:
Internet---->Win XP Desktop
The port is open and i can connect to it, so the problem must be with the Ubuntu machine? right?

What do you mean by turning off iptables?
1. How can i turn it off?
2. How can portforwarding with iptables work if iptables is off?

---

### Post by eremyja on 2009-11-18
sorry i wasnt clear! i meant bypass it! and you did so then it must be a problem on your end... 

try this:
```

-A INPUT -p tcp --dport 3000 -m state --state NEW -s 192.168.0.50 -j ACCEPT

```

---

### Post by Dosshell on 2009-11-18
I changed port forwarding section into this:
```
#port forwarding
/sbin/iptables -t nat -A PREROUTING -i eth0 -p tcp --dport 3000 -j DNAT --to 192.168.0.50:3000
/sbin/iptables -A INPUT -p tcp --dport 3000 -m state --state NEW -s 192.168.0.50 -j ACCEPT
```
As you suggested, and also tried (i tried a lot of things)to swith the "-s 192.168.0.50" to "-d 192.168.0.50" but nothing seems to work. Can it be something else which is blocking it? I have tried other ports too.

---

### Post by Dosshell on 2009-11-19
I tried tcpdump and iptables -L while I connected from the Desktop to my external IP.
I used the iptables settings in my first post.
```
§iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
REJECT     tcp  --  anywhere             anywhere            tcp dpt:5900 reject-with tcp-reset 
ACCEPT     all  --  anywhere             anywhere            

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     tcp  --  anywhere             anywhere            tcp dpt:3000 

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere
```

xx.xx.xx.xx is my external IP.
```
§tcpdump -n -i any port 3000
tcpdump: verbose output suppressed, use -v or -vv for full protocol decode
listening on any, link-type LINUX_SLL (Linux cooked), capture size 96 bytes
17:48:34.938824 IP xx.xx.xx.xx.3000 > 192.168.0.50.4117: R 0:0(0) ack 1644879593 win 0
17:48:35.439196 IP 192.168.0.50.4117 > xx.xx.xx.xx.3000: S 1644879592:1644879592(0) win 65535 <mss 1460,nop,wscale 2,nop,nop,sackOK>
17:48:35.439275 IP xx.xx.xx.xx.3000 > 192.168.0.50.4117: R 0:0(0) ack 1 win 0
17:48:35.941301 IP 192.168.0.50.4117 > xx.xx.xx.xx.3000: S 1644879592:1644879592(0) win 65535 <mss 1460,nop,wscale 2,nop,nop,sackOK>
17:48:35.941373 IP xx.xx.xx.xx.3000 > 192.168.0.50.4117: R 0:0(0) ack 1 win 0
^C
5 packets captured
7 packets received by filter
0 packets dropped by kernel
```

I cought the exception:
```
SocketException: System.Net.Sockets.SocketException: No connection could be made
 because the target machine actively refused it xx.xx.xx.xx:3000
```

Can any one help me to troubleshoot or am I doomed to reinstall Ubuntu?

EDIT: Does anyone knows any otherway then iptables to portforwarding?

---

