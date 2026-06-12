---
title: "Contradictory results, open firewall v. port blocked on Transmission"
date: 2009-07-20
forum: Networking &amp; Wireless
---

### Post by jennyjenny on 2009-07-20
I would like to open up port 1025 on my linux box (Ubuntu 9.04).  According to my reading of the firewall settings - I have all ports open.  According to Transmission the port I would like to open (1025) is blocked.

How do I open up port 1025 on my linux box?  Or is this getting stuck at the router? (2wire 2701HG-B) -- and I have spent a lot of time opening up port 1025 on the 2wire/router firewall.  Port 1025 is open (tcp and upd) for my linux machine.

1) I attempt to open port 1025 from the command line
 $ 487  OPEN_TCP_PORTS="1025:1025"
 $ 488  OPEN_UDP_PORTS="1025:1025"

no luck -- port remains blocked

2) I check to make sure the firewall is open on my linux box
jenny@jenny-desktop:~$ sudo iptables -L
[sudo] password for jenny: 
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination  

I think this indicates that the firewall on my linux box is letting all packets through.

3)canyouseeme.org  test port 1025
Error: I could not see your service on 99.30.228.22 on port (1025)
Reason: Connection refused

I am stuck. What next step would you recommend?

-j-:P

---

### Post by superprash2003 on 2009-07-21
looks like your router is blocking it.. could you post a screenshot of the port forwarding page of your router

---

### Post by jennyjenny on 2009-07-22
How very strange ... my proxy provider (bt guard) claims that Transmission does not work with BT Guard.

(their email)

Hello,

Transmission does not work with BTGuard, use Vuze.

Best,

BTGuard

jennyjenny wrote:

    hi,

    I am getting a little stuck when I open port 1025 on our router/gateway (2wire .. 2701HG-B),  I have gone to the firewall settings and opened up port 1024 (tcp and udp) for my desktop computer.

    unfortunately, my BT application .. Transmission .. reports the port as closed.

    I checked my system (ubuntu 9.04) - and I am not running a personal firewall.
    Any suggestions?

---

