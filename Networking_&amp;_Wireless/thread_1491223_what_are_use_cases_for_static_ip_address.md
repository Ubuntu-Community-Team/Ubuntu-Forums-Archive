---
title: "what are use cases for static ip address?"
date: 2010-05-23
forum: Networking &amp; Wireless
---

### Post by legolas_w on 2010-05-23
Hi,

what are use cases for static ip address for clients or servers.

Thanks.

---

### Post by wheredidrealitygo on 2010-05-23
Servers should always be static so the IP never changes.

When you're behind a firewall and ports need to be forwarded then you don't want to have them be forwarded to an IP whose lease has expired and suddenly you find the server isn't responding because the port is forwarded to another machine or none at all.

Also useful in case internal DNS/WINS ever goes down and you can no longer ping them based on hostnames.

---

### Post by Iowan on 2010-05-23
You can (probably) set up your DHCP server to issue a "static lease" based on MAC address. *Sometimes* DHCP doesn't seem to play nice - a static address is a way to bypass the DHCP server (but the static address should be outside the DHCP range).

---

### Post by Detonate on 2010-05-23
Reasons I use static IP addresses on my home network.

NFS shares.  If you use DHCP and the the computer that has the share reboots to a new IP address, you can no longer access the shared folders.  Major PITA.

Network printers, much easier to set up with a static IP address, and if it is a shared printer on another machine, and the IP address changes, you have to reinstall the printer.

And, when I browse my network, I always know which computer I am looking at, because I know which IP address belongs to each computer.

Also, it improves boot time a little because the system does not have to wait while obtaining  a DHCP lease.

---

