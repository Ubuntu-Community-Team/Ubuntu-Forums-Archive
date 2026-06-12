---
title: "cross wire between 2nd adapt. and LAMP server"
date: 2010-06-23
forum: Networking &amp; Wireless
---

### Post by isle on 2010-06-23
I'm very new to this so please excuse misused terminology. Not sure about prefix either.

I have a workstation with two network adapters.  One is linked to my router for home peer to peer networking and the Internet.  The other has a crosswire going to network adapter of my ubuntu LAMP server.

I did and ifconfig on the server and it listed loopback  "inet6 addr: ::1/128 Scope:Host"

I typed "http://::1/128" in the address field of firefox on the workstation and got.

"This address is restricted

This address uses a network port which is normally used for purposes other than Web browsing. Firefox has canceled the request for your protection."

The inet6 addr for eth0 (network card on server) is an address in a funny form (fe80::.....) not the same as if I connect workstation and server through a router (192.168....)

Is there anyway I can configure fire fox in ubuntu to
1. use that second network adapter if it's not using it already?
2. display the default web page of the server through a cross wire (I have already seen default web page in firefox on workstation from server when hooked up through router)?

---

### Post by Iowan on 2010-06-23
The localhost address is an internal address - it will try to connect you to your own machine. **ifconfig -a** on the server *should* provide an address for the server such as 192.168.1.2 - that is the one you should use - IF the webserver is properly configured. You might ping the address to confirm you can reach it. Of course, the workstation will need an address in the same subnet first...

---

