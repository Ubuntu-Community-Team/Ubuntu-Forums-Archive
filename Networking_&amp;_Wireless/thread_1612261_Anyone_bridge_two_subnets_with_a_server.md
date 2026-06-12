---
title: "Anyone bridge two subnets with a server?"
date: 2010-11-02
forum: Networking &amp; Wireless
---

### Post by wesg on 2010-11-02
I have a Ubuntu server with multiple NICs and I'm just thinking about a potential scenario that might come up soon. 

Imagine I have a network on floor 1 with an independent cable connection to my Ubuntu server -> switch -> assorted devices, on the subnet 192.168.0.x
Now imagine friends upstairs have another independent network with cable -> router -> assorted devices, on subnet 192.168.1.x. 

How can I set up my server to provide access for the 1.x subnet to the 0.x and vice versa. Ideally the devices all access internet from their appropriate subnet. I've read something about bridging, is this what I need?

---

### Post by SeijiSensei on 2010-11-03
You should set up the server as a router.

1) You need to set net.ipv4.ip_forward to one in /etc/sysctl.conf on the server.

2) You need to tell the machines on 192.168.1.0/24 to use the server as their default gateway.  How do they obtain their IP addresses and associated information now?  DHCP?  Static IP asssignments?  Whatever the method, make sure the server's address in 192.168.1.0/24 is the default gateway for this network.

3) If you have firewalling enabled on the server, you'll need to have an iptables INPUT rule that permits traffic from the 192.168.1.0/24 network and a FORWARD rule to enable traffic to pass between the interfaces.

---

