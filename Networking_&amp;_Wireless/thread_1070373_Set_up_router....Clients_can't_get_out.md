---
title: "Set up router....Clients can't get out"
date: 2009-02-15
forum: Networking &amp; Wireless
---

### Post by hakras on 2009-02-15
I installed Ubuntu Server with Shorewall.  I have 2 nics (eth0 is external and eth1 is internal) set up.  From the server, I can ping internal address and external address (google.com).  From the clients on the internal network, I can ping the server (both interfaces), but I cannot ping anything further.  I can't get to the internet from those machines either.  I even tried stopping shorewall, but that did not make a difference.  I am sure that I must be missing something, but after hours and hours of searching I am at a lose.  Do I need to specify some kind of bridge between the two interfaces?  If so, why can I ping eth0 from the internal network?  I am very confused on this one.  I also installed webmin hoping that it would help me identify something visually (no help).  Any ideas?

Also, both interfaces are set up with static addresses.  I have a Windows 2003 server on the internal network (DHCP/DNS) and I have a DSL modem on the external network (DHCP/DNS).

---

### Post by superprash2003 on 2009-02-15
you would need to setup ICS [http://ubuntuforums.org/showthread.php?t=91370](http://ubuntuforums.org/showthread.php?t=91370)

---

