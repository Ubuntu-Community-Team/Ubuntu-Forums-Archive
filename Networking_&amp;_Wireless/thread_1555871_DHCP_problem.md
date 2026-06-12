---
title: "DHCP problem"
date: 2010-08-18
forum: Networking &amp; Wireless
---

### Post by ishokenmei on 2010-08-18
I set up a dhcp server in the lan and assigned static ips to two computers, computer A and B, according to their mac address.  Everything was running fine.  But when I turned off computer A, connected computer C to the network, and assigned computer A's static ip to computer C without changing dhcp setting.  Computer C was able to access the internet.  When I turned on computer A, dhcp couldn't assign an ip address to it, and computer C showed an error message of ip conflict and failed to use internet.  I wonder if dhcp server is able to prevent other computer from using the same static ip that is already assigned to a computer according to its mac address.   Thanks in advance.

---

### Post by Iowan on 2010-08-18
Just my opinion...
DHCP server can't stop a machine from claiming whatever static address it wants (or is configured to have). Every machine could be configured for the same address.  Network won't work, but...

---

### Post by ishokenmei on 2010-08-18
> **Iowan said:**
> Just my opinion...
DHCP server can't stop a machine from claiming whatever static address it wants (or is configured to have). Every machine could be configured for the same address.  Network won't work, but...

Thanks for your reply, Iowan.  After a static ip is assigned to a mac address in dhcp server, is that ip reserved?  Will dhcp server check the mac address and keep it out of the lan if a computer tries to connect to the lan with that ip?

---

### Post by Iowan on 2010-08-18
My opinion again...
The DHCP server will not assign the address to a machine with a different MAC address, but DHCP server is not a cop - it won't stop another machine from using that address. (or even one in it's DHCP range... though it might re-issue that IP and cause a conflict).

---

### Post by jaya28inside on 2010-08-23
bump!

hello, Iowan.
u just said IP cause a conflict.
how to detect that there's an ip conflict through command line anyway?

---

### Post by Iowan on 2010-08-23
> **jaya28inside said:**
> how to detect that there's an ip conflict through command line anyway?I'm not completely sure. I'll need to look up commands to see which IP's are in use, but if you can **ping** an address - it must be in use. Detecting which two machines are "sharing" an address seems difficult...

---

