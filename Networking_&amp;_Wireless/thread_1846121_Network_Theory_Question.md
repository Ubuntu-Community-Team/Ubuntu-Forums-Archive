---
title: "Network Theory Question"
date: 2011-09-18
forum: Networking &amp; Wireless
---

### Post by SparTacux on 2011-09-18
If you have a modem/router with say four ethernet ports and 4 computers are connected to the router -  could a packet sniffer on computer A catch packets on TCP port 80 ( going out to the internet ) from computer B. I thought routers acted like switches in that traffic is directed. Or would a packet sniffer on computer A only catch broadcast traffic from computer B.

---

### Post by grayraven on 2011-09-18
Hey SparTacux,

I believe you are right in the case of a switch. Your router should be acting as a switch. I know connections on a hub can see all traffic on each port. There are modes that switches can be put in to see traffic on a given port. For some more information and detail check out this article:

[http://www.sans.org/security-resources/idfaq/switched_network.php]("http://www.sans.org/security-resources/idfaq/switched_network.php")

Cheers,

James

---

### Post by redmk2 on 2011-09-18
> **SparTacux said:**
> If you have a modem/router with say four ethernet ports and 4 computers are connected to the router -  could a packet sniffer on computer A catch packets on TCP port 80 ( going out to the internet ) from computer B. I thought routers acted like switches in that traffic is directed. Or would a packet sniffer on computer A only catch broadcast traffic from computer B.

A router is a layer3 (TCP/IP) device. A switch is a layer 2 device (Ethernet) A modem/router (as you describe it is a combination of both of these.

The layer 2 device (switch) separates the traffic.  If you want to sniff traffic on the entire network you need to either pass all traffic through a  common interface (firewall or gateway (L3)) or have a switch (L2) with a port that will aggregate all its interfaces.

---

### Post by SparTacux on 2011-09-18
Cheers Guys

I was coming to the conclusion they acted like switches. 

I suppose a password stealer type program couldn't work on this type of network and steal plain text passwords for web sites from other computers on the same network?
Also, If I needed to do a detailed inspection of packets on this network then I'd have to install a program like wireshark on each computer?

---

### Post by SparTacux on 2011-09-19
> **grayraven said:**
> Hey SparTacux,

I believe you are right in the case of a switch. Your router should be acting as a switch. I know connections on a hub can see all traffic on each port. There are modes that switches can be put in to see traffic on a given port. For some more information and detail check out this article:

[http://www.sans.org/security-resources/idfaq/switched_network.php](http://www.sans.org/security-resources/idfaq/switched_network.php)

Cheers,

James

I've only just read the details at the sans.org link. So much for me thinking you couldn't sniff packets on a switched network. It looks like there are ways around it going off that document I read. 

My modem router uses plain text password to log on through a browser and going off that info then the password could be easily compromised with the right software.

---

