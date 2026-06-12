---
title: "DynDNS and Mythubuntu"
date: 2013-08-22
forum: Networking &amp; Wireless
---

### Post by dasaint80 on 2013-08-22
Ok so I'm trying to access my mythtv from outside my home network.

I've installed ddclient and it all passes clean, and I have the proper ports to allow access.

but I can't seem to access mythtv. I can access my windows server with no problem but i've never did tried to access ubuntu from outside a home network.


Thanks

Steve

---

### Post by dasaint80 on 2013-08-22
why does netstat -tnlp show up all 0.0.0.0?!?!?! but ifconfig -a shows proper ip address?

---

### Post by ian-weisser on 2013-08-23
Is your router forwarding a port to your Mythbuntu system?
The router is forwarding the port to the correct IP address?
Your external connection is using the correct port for forwarding?

Your Mythbuntu system firewall accepts connections on the port?

You Mythbuntu system has an server application (like an SSH server or VNC server) installed?
The server application is configured to listen on the correct port?
The server application is running?

Yeah, it's just the basics. 90% of I-can't-connect-to-my-remote-system is the basics.

Netstat showing 0.0.0.0 for listening network services **is normal**. 0.0.0.0 differentiates from other connections you could specify (like loopback) in really complex setups.

---

### Post by dasaint80 on 2013-08-23
> **ian-weisser said:**
> Is your router forwarding a port to your Mythbuntu system?.
[B]Yes.
[/B]
> **ian-weisser said:**
> The router is forwarding the port to the correct IP address?.
**yes.**

> **ian-weisser said:**
> Your external connection is using the correct port for forwarding?.
**Yes.**

> **ian-weisser said:**
> Your Mythbuntu system firewall accepts connections on the port?.
[B]Yes, I even disabled the firewall just to see if the firewall was an issue. but I have added the proper ports to be allowed through.
[/B]
> **ian-weisser said:**
> You Mythbuntu system has an server application (like an SSH server or VNC server) installed?.
**yea, I'm running ssh and VNC, I can connect to them through my LAN but not through dyndns.**

> **ian-weisser said:**
> The server application is configured to listen on the correct port?.
**Yup.**

> **ian-weisser said:**
> The server application is running?.
**yup.**

> **ian-weisser said:**
> Yeah, it's just the basics. 90% of I-can't-connect-to-my-remote-system is the basics.
**Yea, this is why i'm pulling my hair out!!** :confused::(

---

### Post by dasaint80 on 2013-08-23
I think I found my issue. I'm trying to  use 1 dyndns address for 2 different computers. I think that's causing my headaches! !

---

### Post by scbingham on 2013-08-24
I'm no expert, but my dyndns record just points to my router. My router then forwards port xx to ip xxx.xxx.xxx.xxx, which ever computer(s) that may be. Therefore I only need 1 dyndns address to point to anything behind my router.

Maybe I have misunderstood but it works.

---

### Post by ian-weisser on 2013-08-24
You are right.
Port-forwarding to multiple machines means you must administer the ports you are forwarding to each machine.

For example:
If I'm running multiple Foobar gameservers, then clients to each game use the same ip address, but a different port:
foobar.example.com:444 for Machine A.
foobar.example.com:555 for Machine B.

This means, of course, that the router port forwarding (444 -> A and  555 -> B) needs to be documented. Someday, when the router dies, it will need to be recreated.
This also means that the two servers, running the same application, have slightly different configurations (exception: Routers will happily reassign the port of a forwarded packet, *if* you have access to the feature). Those need to be documented, too. Someday the server may need to be replaced or reinstalled.

If I forget to specify the port, and simply connect to foobar.example.com, the client software automatically tries the default port.
If the default is 222, then the connection will fail. Port 222 isn't forwarded anywhere.
If the default is 444, then I will connect to Machine A, and perhaps never realize my mistake.

---

