---
title: "Node.js WebServer on Ubuntu 12.04 not visible externally from the Internet (ext IP)"
date: 2013-01-10
forum: Networking &amp; Wireless
---

### Post by nesslersreagent on 2013-01-10
Hi,

**Router:** IP: 192.168.1.1
**Host OS:** Windows 7(64 bit) - IP: 192.168.1.2
**Guest OS(VMware):** Ubuntu 12.04 LTS(64 bit) - IP: 192.168.1.10

Guest OS has a NAT and a bridged connection via VMWare.

I'm running a basic Node.js server/website listening on port 8000. 
Port forwarded Router with internal/external port: 8000

I can access my website on LAN(via Windows OS) but not from the any computer outside it or via the internet.

**Tried:**
(1) Disabling Ubuntu firewall "ufw".
(2) Windows 7 firewall disabled.
(3) Problem persists even for apache2 or any other server.
**Result:  No change**

Also external port scans(nmap on external IP) show my port 8000 to be "filtered" rather than open.
Also running the same Node.js server on port 8000 in Win 7 works fine. Port 8000 is "open".

I have tried a "lot" of online solutions for several days but no progress. 
Any solutions/ideas please?

---

### Post by Cheesehead on 2013-01-10
There are a few possibilities:

-Router firewall
-Router port forwarding
-Server firewall
-Server application using the port

Since you can access the server from within the LAN, the server firewall and application seem to be correct.

Since an external port scan shows the port 'Filtered', a firewall (router or server) is suspect. The server firewall seems to work, and you said port forwarding is set, so the next place to check is the router firewall.

---

### Post by nesslersreagent on 2013-01-10
My router's a very basic model and it has no Firewall.
In fact, I tried running WAMP and the same Node.js Server on my Windows 7 system and it works fine.
I can access the website externally and the port scan shows port 8000 "open". 
Is there any other possibility?

---

### Post by nesslersreagent on 2013-01-10
**Problem solved**.

I switched over to "**Oracle's VirtualBox**" and it works flawlessly.

It's possible to employ a virtual server either by -
(1) NAT connection with port forwarding.
(2) NAT and a bridged connection. 

I used option 2 and used a static IP(192.168.1.10) for the bridged connection. The NAT connection defaults to 192.168.1.2 by DHCP.

Router port forwards as, incoming port: 8000, outgoing port: 8000 and outgoing IP: 192.168.1.10

For a **clear and concise tutorial**, here's a good link -> [http://www.howtogeek.com/122641/how-to-forward-ports-to-a-virtual-machine-and-use-it-as-a-server/](http://www.howtogeek.com/122641/how-to-forward-ports-to-a-virtual-machine-and-use-it-as-a-server/)

It's possible on "VMWare" too, but it's much simpler on "VirtualBox", in my opinion.

---

