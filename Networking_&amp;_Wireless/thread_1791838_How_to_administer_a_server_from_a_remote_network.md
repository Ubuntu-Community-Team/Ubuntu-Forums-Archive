---
title: "How to administer a server from a remote network ?"
date: 2011-06-27
forum: Networking &amp; Wireless
---

### Post by leegold on 2011-06-27
Hi,

I have Ubuntu 10.4 Server, it's a local intranet server in back of a router in a "standard" home network. As I understand it laptops, PCs and the server are "hidden" from direct contact with the internet by Network Address Translation [NAT]. The router is a Linksys WRT54G all clients are connected to it, and the router itself is connected to a modem provided by the ISP. The server was given a static IP address. To admin the server I connect from a local client with SSH and get a command-line.

Is there a way to admin the server if I am a thousand miles away from this local network? Putting it another way, Is there a way to "tunnel" through to the server, give the user/pw and get a command-line from the internet? What software or hardware is needed?

I'm sure this is done a lot but I've never done it before. Help appreciated.

Lee G.

---

### Post by Beacon11 on 2011-06-27
Yeah-- do you have access to the router and (potentially) modem? You need to setup port forwarding for whatever port you use for SSH. Or, alternatively (what I'd recommend) is to just use Hamachi. It's a configure-less VPN option that take care of the tunneling for you. Check it out. The Linux version is here: [https://secure.logmein.com/labs/](https://secure.logmein.com/labs/) .

---

