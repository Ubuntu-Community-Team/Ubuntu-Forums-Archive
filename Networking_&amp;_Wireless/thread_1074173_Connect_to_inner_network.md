---
title: "Connect to inner network"
date: 2009-02-18
forum: Networking &amp; Wireless
---

### Post by abandonedthe_mulletator on 2009-02-18
I have a home network set up as follows:
Internet <--> Ubuntu Server <--> Router <--> Computers & XBOX

How can I connect to my inner network from a remote location?
I can ssh into my server from anywhere which is very handy.  I can't get into any of my other machines though.  I have tried logging in to my server first then trying to make a ssh connection from there but no luck.

I do not have a firewall set on my router.
I have tried putting different computers in the DMZ but that did not work either.

Another related issue I am having is I have Ushare set up on the server to share media files with my XBOX but the XBOX does not recognize the server.

---

### Post by yoyoned on 2009-02-19
You need to set the ubuntu server to forward the incoming ssh connections to the IP of the router, then have the router forward it's incoming ssh connections to the IP of teh machine ou want to connect to

---

### Post by superprash2003 on 2009-02-19
you could setup a VPN server..

---

### Post by abandonedthe_mulletator on 2009-02-19
> **yoyoned said:**
> You need to set the ubuntu server to forward the incoming ssh connections to the IP of the router, then have the router forward it's incoming ssh connections to the IP of teh machine ou want to connect to

Can you give me a little more information on how to do that?  I am using iptables for a firewall so I will have to add a rule.  The router has a web based configuration and I don't know how to forward ports on it.


What about the Ushare?  I don't think VPN will work for the XBOX.

---

### Post by abandonedthe_mulletator on 2009-02-19
I got the SSH working so that is great.
I learned how to forward the port from [THIS]("http://www.portforward.com/english/routers/port_forwarding/routerindex.htm") site.

I can't figure out the Ushare though.  It works if I plug the XBOX directly into the server so it has something to do with the router.  I forwarded all the ports that the XBOX said I should.:???:

What else should I do to the router?

---

### Post by abandonedthe_mulletator on 2009-02-20
I'm continuing this on a more suited forum.
[HOW TO: The Ultimate XBOX 360 Multimedia Sharing Guide]("http://ubuntu-virginia.ubuntuforums.org/showthread.php?p=6768397#post6768397")
Thanks.

---

