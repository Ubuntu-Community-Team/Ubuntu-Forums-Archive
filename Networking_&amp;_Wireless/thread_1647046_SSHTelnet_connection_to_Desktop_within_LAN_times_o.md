---
title: "SSH/Telnet connection to Desktop within LAN times out."
date: 2010-12-16
forum: Networking &amp; Wireless
---

### Post by valros on 2010-12-16
Wrong prefix, its Ubuntu not Lubuntu.

Three devices:

Laptop 1:
---Can ssh to any device.
---Accepts any internal ssh.

Desktop 1:
---Can ssh to any device.
---Accepts any internal ssh.

Desktop 2:
---Can ssh to any device.
---Can ssh to itself through localhost or 192.168.1.130.
---Any ssh(and telnet) aimed at this device times out.


All three devices recently had openssh-server installed yet only one seems deviant...
I've been trying to ssh into desktop 2 to no avail, yes the machine is reachable, yes sshd is running, yes ufw is disabled, and no there is no external firewall that I know of. Anything else I can try?

The router for the LAN being dd-wrt.

---

### Post by cavalier911 on 2010-12-18
Start with debug mode on the client of Laptop 1 with the -v switch
to see what is exactly failing in the connection process with server on Desktop 2.
```
ssh -v username@Desktop 2
```
Now use debug mode on client of Desktop 1 to try connection to Desktop 2.Does connection fail at same point with both clients. 
Copy/Paste debug output of clients 
between code tags showing connection failure
if you can't figure it out.

---

