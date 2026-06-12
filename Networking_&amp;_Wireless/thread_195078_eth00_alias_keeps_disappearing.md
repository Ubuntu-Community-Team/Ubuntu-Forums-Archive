---
title: "eth0:0 alias keeps disappearing"
date: 2006-06-12
forum: Networking &amp; Wireless
---

### Post by Robb Kidd on 2006-06-12
How the heck do I keep an alias up on an interface?

I have configured the alias eth0:0 to have a static IP in the subnet (but outside of the DHCP range, of course) that interface eth0 receives via DHCP.  This is, essentially, to let the host continue to receive DNS by DHCP in the event of a change from my ISP and still allow me to NAT in to an internal static IP.  My router's firmware (Linksys' for their WRT54G) does not provide static MAC-to-IP addressing for DHCP, so my solution was to create a statically addressed alias on the DHCP'd interface.  I am considering a third-party firmware to get around this.

Originally, this alias was created with ifconfig called from ifup by an up script placed in the eth0 stanza in /etc/network/interfaces.  I had hoped that this would mean that eth0:0 would only be up while eth0 was up and down with eth0 was down.  eth0:0 never seemed to survive more than a day or two, while eth0 was up, apparently continuously.  My second attempt, giving up on tying eth0:0 up/down status to eth0, was to make a separate eth0:0 stanza in /etc/network/interfaces.  It still does not survive more than a day or two. 

I'm thinking this has something to do with eth0 receiving its DHCP renewal, but have not been able to determine what to look for on the system to verify this.

---

