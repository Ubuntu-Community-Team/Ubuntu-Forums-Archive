---
title: "Remote Desktop Access from outside LAN"
date: 2011-03-13
forum: Networking &amp; Wireless
---

### Post by seanksg on 2011-03-13
Hi all,

I just set up Remmina the other day to be able to access my desktop remotely.  However, I can only do this when I am connected to my home network.  Is there a way to set up Remmina so that I can connect to my desktop remotely from outside my home network?

Thanks.

-Sean

---

### Post by ursoouindio on 2011-03-31
I would like that also.

I get this message when trying from outside the local network:

Connection to host 1##.##.##.### was closed.

---

### Post by spiky001 on 2011-03-31
You must have port forwarding set up and firewall allowing outside connections on port

---

### Post by ursoouindio on 2011-03-31
is there an easy way to do so?

Ic can't event find a firewall settings on Ubuntu...

---

### Post by hugmenot on 2011-04-01
You have to open up ports on your router. If your computer plugs "directly into the internet" then the ports are blocked somewhere else, or you are on NAT and can do nothing to open up ports.

---

