---
title: "Via-RhineII VT6102 rel 78 not working"
date: 2006-03-10
forum: Networking &amp; Wireless
---

### Post by meushi on 2006-03-10
Hello,

Short description: Fresh install of Breezy on a new machine, eth0 sends packets but receives nothing.

Hardware description:
Motherboard: AsRock 775V88+
CPU: Pentium 4 630
Memory: 1GB DDR400
Ethernet: Built-in VT6102 rel 78

The problem:
The card is detected all right and the autonegociation worked (100TX-FD). When I try to request an IP with 'dhclient eth0' I never receive an answer.

Checking on the DHCP server, I see that the request was received and a lease sent back immediately. An 'ifconfig eth0' shows several transmits but no receives. If I setup a static IP for testing, I can't ping any device on the network.

I checked the cable to be sure, another machine plugged on the same cable works fine.

I tried with the kernel driver (via_rhine) and with the 4.39 rhinefet from Via. No success with rhinefet either.

While googling, I saw references to IRQ sharing problems for some chipsets and this card when ACPI was on. So I tried with ACPI turned off, still no joy.

I still had an old debian R3.0 cd lying around so I popped it in to try. The via-rhine driver of BF2.4 (2.4.18) is known to be buggy, but I am eventually able to get an IP address and see a 94% packet loss. Once again, that is expected for this revision of the card with 2.4 kernels not between .21 and .24 so it isn't such an issue.

Any idea?

---

### Post by meushi on 2006-03-11
Extra information which might be useful...

When doing a dhcp request, I get exactly 1 "frame" and 0 "error" in ifconfig. That only happens the first time the driver is loaded, if I rmmod and modprobe back in I won't get any "frame" for further requests.

The northbridge is a Via PT880 and the southbridge is a Via 8237R. According to the Via schematics of the chipsets, the ethernet controller should be a 6103. However, lspci sees it as a 6102 rev 78.

---

### Post by meushi on 2006-03-12
"solved"

If I force the card to 10FD, it sends and receives. If I force it back to 100FD, it doesn't receive any packet. I'll live with 10FD, use that port for the DSL side and slap another card for the LAN side.

---

### Post by xdefconx on 2008-02-24
> **meushi said:**
> "solved"

If I force the card to 10FD, it sends and receives. If I force it back to 100FD, it doesn't receive any packet. I'll live with 10FD, use that port for the DSL side and slap another card for the LAN side.

Hye! I got some problem like u. Can u explain how u force the card to 10FD?

*linux newbies here

Thanxs

---

