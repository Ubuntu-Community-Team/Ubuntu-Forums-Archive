---
title: "DMZ enabled in router--stop acess ssh port 22?"
date: 2006-02-24
forum: Networking &amp; Wireless
---

### Post by Hotchilli on 2006-02-24
Could having DMZ enabled in a router setup stop me from accessing ssh port22
on my box from a remote host, Even though 22 has been port forwarded.

hc:D :D

---

### Post by suRoot on 2006-02-24
Shouldn't.  On most home firewalls, the DMZ host you specify is usually permitted all incoming traffic.  Of course, you still need to port forward / etc.  But simply enabling a DMZ shouldn't prevent access.

What kind of router do you have?

Do you have a firewall running on the server?  Does the router act as a firewall?  If so to either, have you created the appropriate rules for inbound SSH traffic?  (besided just port forwarding)

---

### Post by Hotchilli on 2006-02-24
Yes i Have port forwarded but with no rules
you may want to take a look at this thread
[http://ubuntuforums.org/showthread.php?t=135588](http://ubuntuforums.org/showthread.php?t=135588)
its a linksys ag241 router

thanks

HC:???: :???:

---

