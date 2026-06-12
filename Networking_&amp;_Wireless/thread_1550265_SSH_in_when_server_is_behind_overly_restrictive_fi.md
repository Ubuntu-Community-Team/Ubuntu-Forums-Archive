---
title: "SSH in when server is behind overly restrictive firewall"
date: 2010-08-10
forum: Networking &amp; Wireless
---

### Post by Lord.Quackstar on 2010-08-10
So here's my delema, there is a server on a network protected by a overly restrictive firewall. I can't connect to the server.

I was thinking, does a program exist where the server would connect to another server outside the firewall, then wait for commands? This way there is no port forwarding required.

The only program I know that does this is LogMeIn. If you check the logs it does use SSH, and thats even when I blocked the port. Since LogMeIn isn't what I was looking for (Windows Only, full screen capture instead of command line), does an alternative exist?

---

### Post by YesWeCan on 2010-08-11
What OS has your server got, what OS is your client?
You could certainly achieve what you want using OpenVPN - create a point to point tunnel between server and client with the server as the vpn client.

---

