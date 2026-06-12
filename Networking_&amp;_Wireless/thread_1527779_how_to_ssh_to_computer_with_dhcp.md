---
title: "how to ssh to computer with dhcp"
date: 2010-07-09
forum: Networking &amp; Wireless
---

### Post by skrite on 2010-07-09
Hey all,
I have a small server that will collect industry machine info and report it to our main server here. Now, we plan to make a few of these units but we will need to be able to remote into them (ssh) to kick off the operations when they are delivered. Problem is, how can i ssh into a machine that has an ip given by dhcp?     I could have the server send me it's internal and external ip, but that still does not open port 22 (or whatever i need) on the router so i can get to it from an outside line.

i would greatly welcome and and all ideas to help me out with a solution suggestion

thanks

---

### Post by jonobr on 2010-07-09
IMHO servers should not have dynamic ip addresses assigned for reason such as these.

What you could do is if it is set to DHCP though is to associate in your DHCP machine the mac address of the server so it always gets the same address.
That way if your doing port forwarding on your access device to the network, then you will always get to that Ip address.

---

### Post by Iowan on 2010-07-09
I have a server set up that way. Since I'm using DNSMasq for my DHCP/DNS server, I can **ssh hostname** successfully.

---

### Post by Boondoklife on 2010-07-09
Ditto to the dnsmasq, I do the same with a cheap linksys router with dd-wrt installed on it.

---

