---
title: "risk of port forwarding?"
date: 2009-04-15
forum: Networking &amp; Wireless
---

### Post by Mujaheiden on 2009-04-15
Hi,

From my router i forwarded all ports to my Ubuntu box. Now Im just wondering if theres any secutriy risk, as im sharing folders with Samba and have an ftp server set up?

Let me know! I wouldnt like to find my shared folders empty all of the sudden!!

---

### Post by Mordac85 on 2009-04-15
You have basically bypassed your router/firewall and placed your system on the net for all to play with.  If your box is secure and you enjoy letting anyone beat at the door until they find a way in then go ahead and leave it.  Otherwise, just forward the ports you really need and, if possible, never ever use the default ports.  It may take more time to setup the way you want, but it's also much more secure.

---

### Post by sedawk on 2009-04-15
Very unsecure!

Only open/forward well understood and selected ports.

E.g. port 80 if you run a web server for public access.
Or port 22 if you want to ssh your system from the outside.

Normally that is enough. Only when you run
some public servers locally (e.g. a dedicated server for some games)
or you want "seed" for P2P you have to open (well understood) ports.

Open ports are an invitation for so called "worms".
Normally a router is a good protection agains worms, so I always
recommend a (firewalled) router, even if only one PC is connected
(so a DSL modem would be sufficient). But with open ports the firewall
inside the router is worthless...

---

### Post by Mujaheiden on 2009-04-15
ok thanks, i just leave it at port 80 now then, untill i realy want more exitement :)

---

### Post by iponeverything on 2009-04-15
If you know the ip address ranges that your going to be access the server from, it is fairly trivial to be able to limit access to the various services to just that address range.

Using non-standard ports for things does not really buy you much, as it takes nmap very little time to scan and identify all 65535 ports on a machine.

---

### Post by Yashiro on 2009-04-15
You only forward ports to allow incoming connections.
Thus you do not need to forward port 80 to browse the internet, or any other port.

Opening ports does not lead to excitement. With the knowledge you have demonstrated it leads to a compromised machine and someone stealing your files.

If ever in doubt ask on here if you feel you need to forward/unblock certain ports and features.

---

