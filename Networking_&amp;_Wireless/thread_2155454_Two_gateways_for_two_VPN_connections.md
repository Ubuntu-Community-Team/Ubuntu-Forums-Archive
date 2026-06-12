---
title: "Two gateways for two VPN connections"
date: 2013-06-18
forum: Networking &amp; Wireless
---

### Post by erzich on 2013-06-18
Hi,

I have two DSL lines and need one VPN connetion on each of them. It was no problem to configure the server and clients, both connections are working fine, but only separatley. How can I force the openVPN Client
to use a second connection/gateway, e.g. eth0 192.168.0.x --> 10.8.0.x --> server / eth1 192.168.179.x --> 10.8.1.x --> server ? Gateways are 192.168.0.1 and192.168.179.1 .

Best regards

---

### Post by SeijiSensei on 2013-06-18
In general, the host can only have one "default gateway," the address to which traffic not intended for locally-routed subnets is forwarded.  You can have multiple gateways if you use routing "metrics," but still only one of them will be active at a time.

That said, I don't really understand your question.  Are there certain kinds of traffic you want to send over one VPN and leave the rest to the other? Is there a way to discriminate between the two classes of traffic based on destination IP addresses?  Perhaps you want to combine the two interfaces into a single pipe?  That requires the use of "[bonding]("https://www.kernel.org/doc/Documentation/networking/bonding.txt")."

You need to be more specific about the problem you are trying to solve.

---

### Post by erzich on 2013-06-18
Thank you for your answer SeijiSensei, I will try to explain my idea a little bit more precise.

The goal is to connect to a server via two separate VPN connections. There are two
DSL lines and two networks/router (gateway 192.168.0.1 and 192.168.179.1) and also
NIC's eth0 and eth1.

First I have to establish a connection from line #1 and one from line #2 to the Server over 
VPN, if these connetions work stable and fast simultaniously then the fun has just begun :)

I will bond the devices tap0 and tap1 into a single one on each side, I hope to increase the 
upload data rate. At the moment they are at 5000kbit/s and 10000kbit/s, possibly this ist the 
next problem, without any more modifications only 10000kbit/s will be available (2*5000kbit/s)
 I think, because the slower line rules the bonded connection. Due to the difference the 
packages ought to be devided into two streams (66%/33%) but I have no clue how to do this.

---

### Post by SeijiSensei on 2013-06-19
Perhaps the solution is to bond the Ethernet NICs first, then set up the tunnel over the bonded interface?

---

