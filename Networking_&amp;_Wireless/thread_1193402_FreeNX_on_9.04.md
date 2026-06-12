---
title: "FreeNX on 9.04"
date: 2009-06-21
forum: Networking &amp; Wireless
---

### Post by hdensley on 2009-06-21
I'm having a hard time configuring Freenx server (Ubuntu 9.04) and client (Vista x86).  Ubuntu is running on Virtualbox on Vista.  So here's the issue, I config the server to it's IP address via ifconfig eht0 IP, 10.0.2.15, port 22... and vice versa, I config the client in Vista to VirtualBox Host-Only Network IP, 192,168.56.1, port 22

Vista firewall is off....

I keep getting a "connection refused" error.  Any idea why this is so?  Any idea on how to get this running?

I would describe myself as an advanced Noob, who is probably not good at networking.

Thanks

---

### Post by jhannah on 2009-06-24
When you configure the FreeNX server, it sounds like you are telling it to bind explicitly on 10.0.2.15. If you are only going to be connecting from the host running VirtualBox, you should be able to bind it to the 192.168.56.0/24 IP. However, if you wish to reach it from other machines in the 10.0.2.0/24 network, you will need to setup a bridged interface in VirtualBox. Otherwise, SSH traffic destined to the VM will never actually make it there.

---

