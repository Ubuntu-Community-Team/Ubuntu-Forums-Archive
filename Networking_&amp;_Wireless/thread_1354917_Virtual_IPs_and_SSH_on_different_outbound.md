---
title: "Virtual IPs and SSH on different outbound"
date: 2009-12-14
forum: Networking &amp; Wireless
---

### Post by OnsiteOnly on 2009-12-14
I am having a problem getting something I believe to be possible to work.

I have a machine that has 2 public IPs: eth0=100.100.100.1 and eth0:1=100.100.100.2 
(IPs changed to protect the guilty)

I have the aliases setup correctly so that I can ping and SSh to both IPs.

However, if I check my IPs on a site like ip-adress.com it always shows the eth0:1 address no matter which address i SSh to.

How can I get it so that if I SSH to .1 it shows .1 to the world and if I SSH to .2 it shows .2?

---

### Post by diablo75 on 2009-12-15
What kind of networking hardware are you using to get two public IP addresses?  Normally an ISP will only allow you to have one, which they assign to your cable or DSL modem.  Typically, in a LAN, that IP is passed on to the uplink port of a router, and then Network Address Translation splits it into a seperate class of addresses for the down-link ports.

In short:  What does the topology of your network look like?

---

### Post by Lars Noodén on 2009-12-15
They sound more like real IPs than virtual ones.  ;)

You can have the ssh daemon listen to one particular address using the [ListenAddress](http://manpages.ubuntu.com/manpages/karmic/en/man5/sshd_config.5.html) directive.  You can specify multiple listen addresses in the same configuration file. 

If that doesn't do it, then you can have two copies of the configuration files, each with a different ListenAddress, and then run two separate instances of sshd.  

Just two guesses.

---

### Post by OnsiteOnly on 2009-12-15
I have 2 real IPs. One asigned to eth0 the other to eth0:1. What i need is when I SSH to eth0 address that the internet sees me one eth0 and same scenario on eth0:1

---

