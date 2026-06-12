---
title: "DNS and short names question"
date: 2008-12-28
forum: Networking &amp; Wireless
---

### Post by jakev383 on 2008-12-28
I have a server running here that is my DNS and DHCP server.  We can browse the Internet fine.
What I would like to do is have every computer that gets a DHCP address from the server be able to browse to other machines by simple names.  For example, I have a mythtv setup. The myth server's name is myth-server.  I want to be able to type "http://myth-server" in the address bar of whatever browser I'm using, and have that translate to the actual IP address.  I'm not sure what to search to find how to do this, so I'm asking here.
Would I set up my DNS server to recognize "myth-server" as a zone and create a zone file as I would if running a .com name?  I tried it to the firewall server's (the one running DHCP and DNS) /etc/hosts file, but that did not work.
Thanks in advance!

---

