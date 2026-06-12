---
title: "squid and guidedog problem with fixed port internet pages"
date: 2006-02-21
forum: Networking &amp; Wireless
---

### Post by rubenjavier on 2006-02-21
I have an Ubuntu machine working as a Proxy for internet with squid, the rest of the machines are Win2000 or Ubuntu machines too. My proxy uses port 8989 and all the machines can see the Internet trough it. I need the other machines to be able of use some internet pages that are in a different port than the 8989, for example the page [http://www.infraestructura.gov.ve:7784](http://www.infraestructura.gov.ve:7784) , so I oppened that port too in squid, but the rest of the machines can't see the page, only the Proxy can because is the one connected directly to the internet, every time I try from another machine the only thing I see is the squid error page. I've also tried using guidedog to do a port forwarding form the port 7784 of the internet eth connection to the port 8989 of the LAN eth connection of the proxy but this isn't working either...
what can I do???? I really need the rest of the machines to be able of seeing this kind of pages
Thanks in advance

---

### Post by suRoot on 2006-02-21
Don't have a firewall in front of the squid box blocking those ports, do you?

You have the ports defined in 'acl Safe_ports' in squid.conf?

---

### Post by rubenjavier on 2006-02-21
Nope... no firewall and the ports are open, som eof the win2000 machines use ewido as antivirus and for the update ewido needs the port 503 open, the updates succeds but because the ewido executable connects directly to this port, the explorer instead connects to the Proxy port (8989) and then to the page port (7784)
The ports are also open but not in a bidirectional way, because the same machines that connects to the ewido update, can't see the port 503 using the page [http://www.canyouseeme.org/](http://www.canyouseeme.org/) (this page lets you check wich ports are reachable of your machine).
But this same ports CAN be seen from the proxy, so the problem is the proxy machine blocking something.
thanks in advance

---

