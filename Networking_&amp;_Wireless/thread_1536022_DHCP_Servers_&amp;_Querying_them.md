---
title: "DHCP Servers &amp; Querying them"
date: 2010-07-21
forum: Networking &amp; Wireless
---

### Post by Kerubu on 2010-07-21
This question is not really related to Ubuntu directly as it's about networking and a little problem I'm having at the moment.

I have a laptop running Ubuntu 10.04 and have a wireless network which is provided by a wireless router and combined ADSL modem, so a single box provides my wireless network and connection to the internet. I use DHCP IP addressing and the DHCP server is running on the **wireless modem**.

Now I occasionally use another laptop at the same time on the network and I've looked on the internet in vain for instructions on how to discover the (local) IP or one laptop from the other, seeing as I know both of their hostnames. 

It seems impossible to do such a simple task without resorting to DNS name servers. Surely there must be someway of querying the DHCP server for the IP of host on the local network.

Can any help?

---

### Post by Iowan on 2010-07-21
I use **DNSMasq** for DHCP/DNS which makes ping by name pretty easy. However, I had to edit the "send host-name" line in  */etc/dhcp3/dhclient.conf* (on client machines) to make it work.

---

