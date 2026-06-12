---
title: "Can't connect remotely to a service"
date: 2012-11-29
forum: Networking &amp; Wireless
---

### Post by Ncage1974 on 2012-11-29
I just created a service on ubuntu. I can telnet to the service just fine using:
telnet localhost 511

I tried to connect remotely to the service and it fails:
telnet 192.168.0.1 511

Whats weird if i use the ip of the machine locally rather than localhost (telnet 192.168.0.1 511) it also fails with:
"Unable to connect to remote host: Connection Refused"

When i do sudo ufw status i get:
"status:inactive"

So it looks like the firewall is not on. I'm definitely far from an expert in the linux area. Does anyone know what could be going on?

Oh btw this is ubuntu 12.04 workstation

---

