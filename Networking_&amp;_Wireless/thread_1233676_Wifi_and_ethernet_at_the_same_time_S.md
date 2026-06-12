---
title: "Wifi and ethernet at the same time :S"
date: 2009-08-06
forum: Networking &amp; Wireless
---

### Post by codeking on 2009-08-06
Downstairs is a computer for the family to use.  Connected to it is a modem and router.  The rest of the computers in the house get internet through wifi. Up in my office/room, I have a laptop and a desktop, which I sync through the house wifi.

Recently, our router's wifi broke.  We bought a new one, but since the old one's ethernet capability was still fine, I figured I could speed up the syncing of my desktop and laptop by having it through ethernet, which is a lot faster than wireless-G.  So I got both computers hooked up via ethernet.

But I realized I now have a problem:  I have two network connections.  One has internet, one doesn't.  Is there anyway I can use both at one time?  eg:  Sync my computers and still use internet.  Or is that a bit too complex, and I should just keep syncing with wifi, or only doing one at a time?

---

### Post by Iowan on 2009-08-07
I haven't done it, but I suspect it can be done.  The interface will (probably) need to be set up via */etc/network/interfaces*, and a route will need to be created/added. It will be less involved if the ethernet connection is a different subnet than the wireless. If only the two machines are involved, static addresses might simplify things.

---

### Post by codeking on 2009-08-07
So I pretty much need the DHCP address on the wifi to be the default 192.168.1.* and on the local something else, like 192.168.2.* and use /etc/network/interfaces/ to redirect the proper address to the proper network?

Phew, sounds hard. I'm sure I'll figure it out though. :)

---

### Post by Iowan on 2009-08-07
Sounds about right... but **route**, rather than */etc/network/interfaces* will direct traffic flow.  Check **man route** for details.

---

### Post by superprash2003 on 2009-08-07
hope this helps [http://www.cyberciti.biz/faq/linux-setup-default-gateway-with-route-command/](http://www.cyberciti.biz/faq/linux-setup-default-gateway-with-route-command/)

---

### Post by codeking on 2009-08-07
Tried using route, here's what I got:

> theron@theron-desktop:~$ sudo route add default gw 192.168.2.2 eth0
SIOCADDRT: No such process

---

