---
title: "How to ping eth0 from eth1 on my linux machine?"
date: 2010-10-20
forum: Networking &amp; Wireless
---

### Post by nitish777 on 2010-10-20
I have a linux machine with 2 ethernet ports(eth0 and eth1). eth0 is connected to a router which assigns it an IP address 192.168.1.2. eth1 is connected to a switch and I assigned it an IP address 192.168.1.254 using "ifconfig eth1 192.168.1.254 netmask 255.255.255.0 up". How do I ping eth0 from eth1?

---

### Post by psusi on 2010-10-20
Is the switch also connected to the router?

---

### Post by nitish777 on 2010-10-20
No. Its not.

---

### Post by Mr_Mischif on 2010-10-20
eth1 has to be connected to a network in order to ping another computer, you'll have to connect eth1 to the same router as eth0 to make it work.

---

### Post by psusi on 2010-10-20
> **nitish777 said:**
> No. Its not.

Then your question makes no sense.  How do you expect the packet to get from one to the other without a connection between them?

---

### Post by SeijiSensei on 2010-10-20
First it's certainly possible to ping one interface on a machine from another like this:

ping -I eth0 ip.addr.of.eth1

however the OP's setup probably won't work as configured.  First you'll probably need to enable IP packet forwarding in the kernel by setting the "net.ipv4.ip_forward" switch to 1 in /etc/sysctl.conf and rebooting.  Second you need to assign eth1 to another network besides 192.168.1.0/24.  Give it 192.168.2.1/255.255.255.0 and you should be able to run

ping -I eth0 192.168.2.1

---

