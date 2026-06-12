---
title: "Xbox 360 connection sharing - DHCP setup but fails on DNS"
date: 2009-01-02
forum: Networking &amp; Wireless
---

### Post by kev1926 on 2009-01-02
Hello there,

I've been hacking away on trying to get my 360 sharing my wireless connection to my PC for a little while now, but it keeps failing on DNS!

I have a dhcpd3-server running, which makes the 360 connect to my Ethernet card which is connected to the 360 via a network switch.  My setup currently goes like this:

eth0: (static IP)  192.168.0.1/255.255.255.0/0.0.0.0
ath0: (DHCP from router)  192.168.2.2/255.255.255.0/192.168.2.1

There is also a wifi0 and a pam0, but I don't think either of those are used.

The 360 tries to connect to me, and with Automatic IP Settings it brings up:  192.168.0.2/255.255.255.0/192.168.0.1  This seems to work OK, but I'm not sure about the gateway.

The DNS is the part that I'm having trouble with:  I have it set to my ISP's DNS addresses currently, which doesn't work.  I have also tried my router address as said in other guides, as well as my eth0 address, my ath0 address, and the 360 itself - all to no avail.

I also have bind running to see if that helps, but I'm not really sure what I'm doing and that isn't working either.

What am I doing wrong?  All help greatly appreciated!

Kevin.

---

