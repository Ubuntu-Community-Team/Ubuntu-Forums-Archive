---
title: "Using Desktop Sharing over LAN"
date: 2013-08-16
forum: Networking &amp; Wireless
---

### Post by alex40 on 2013-08-16
Previously, I recall Ubuntu's remote desktop program having the ability to easily connect to a local Ubuntu machine that was set up using the Desktop Sharing utility. The local Ubuntu machines would simply appear in a list. However, the Remmina Remote Desktop Client either lacks this functionality, or I have been unable to find it. I am not sure why the software is now harder to use than  it was a few years ago.

---

### Post by TheFu on 2013-08-16
Is there a specific question?
You realize that you do not need to use Remmina if you don't like it.

---

### Post by alex40 on 2013-08-16
I was trying to figure out how to use Remmina to access a local VNC server without knowing the server's IP address. I assume it simply lacks this functionality.

---

### Post by TheFu on 2013-08-16
> **alex40 said:**
> I was trying to figure out how to use Remmina to access a local VNC server without knowing the server's IP address. I assume it simply lacks this functionality.

I suppose it could do a port scan across all systems on the subnet, if that subnet were of a limited size ... /24. Anything larger and I'd block it. You can use Xenmap to scan for all or specific services if you have root/sudo on the network.

OTOH, trying to access a server without knowing the IP ... well ... that's something that Windows does via broadcast or WINS methods. Not really something that UNIX systems do, that I've heard ... well, except multicast services like mbone.  That is a much different use case than this.

Interesting idea.  Someone should create a script to find all the machines running common services on a subnet - it probably already exists. Found something ... not a GUI like Xenmap, but nmap the CLI granddaddy [http://www.cyberciti.biz/networking/nmap-command-examples-tutorials/](http://www.cyberciti.biz/networking/nmap-command-examples-tutorials/)

Still, you have an interesting idea.

---

