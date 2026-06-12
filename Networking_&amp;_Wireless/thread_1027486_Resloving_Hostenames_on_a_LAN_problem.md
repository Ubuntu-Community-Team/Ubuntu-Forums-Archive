---
title: "Resloving Hostenames on a LAN problem"
date: 2009-01-01
forum: Networking &amp; Wireless
---

### Post by Wren on 2009-01-01
I'm hoping someone might be able to give me some tips on resolving network hostnames on Ubuntu 8.10.

I'm trying to connect a laptop and a Desktop via SSH to run Unison and synch my files between the two.  Both computers are running the latest version of Ubuntu Intrepid with all updates.

Every time I try to connect the computers I get a message stating that it could not resolve hostname, name or service not known.

If I connect via the IP address, the connection works perfectly, however, my router does not allow me to assign static IP addresses, and I've tried setting up the static IP addresses in the Network Connections window of Ubuntu, but every time I log out or reboot, the settings are lost.

The hostnames are displaying correctly on the router, so I know the names are being sent into the LAN, but I have no idea how to get them to resolve so I can actually use them.

Can anyone give me any help or suggestions?

---

### Post by htmlland on 2009-01-01
The ip address issue seems to be a bug. Try reading this and see if it works [http://linhost.info/2008/11/how-to-set-a-static-ip-on-ubuntu-810/](http://linhost.info/2008/11/how-to-set-a-static-ip-on-ubuntu-810/)

It does not fix the resolve issue but its a good step in the right direction :)

---

