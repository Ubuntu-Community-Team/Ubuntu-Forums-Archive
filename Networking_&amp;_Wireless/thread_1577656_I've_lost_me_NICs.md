---
title: "I've lost me NICs"
date: 2010-09-19
forum: Networking &amp; Wireless
---

### Post by LiLoather on 2010-09-19
Just installed Ubuntu 10.4 LTS server.

Installer recognised my three NICs, two of which are cabled, and when I pointed it at the right one it received an address from DHCP and was able to connect to the Internet to complete the installation.

Now the OS loads and presents me with one ethernet interface, eth2, which is connected.  The other two have disappeared.  They aren't listed in /etc/network/interfaces, ifconfig doesn't mention them and ethertool only reports on two - eth1 and eth2. But when I configure an eth1 to talk to the network it's connected to - nothing.  The link is up but there's no-one there.

I've Googled the problem at length to no avail.

Anyone help?

---

