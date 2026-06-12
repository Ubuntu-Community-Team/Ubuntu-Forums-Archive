---
title: "Have to manually get IP on each boot"
date: 2011-08-11
forum: Networking &amp; Wireless
---

### Post by Overcast32 on 2011-08-11
Having a small, but annoying problem with Ubuntu 10.04. 

Each time I boot or reboot, I have to manually force a DHCP request (dhclient). It always gets an IP without problems at that point, but not sure why it isn't grabbing one automatically. I also noticed right when I hit the desktop, it usually shows the Ethernet is disconnected, but then appears to connect each time without problems as well. 

It's not annoying enough to start ripping the guts out, but if maybe someone has a clue what this might be, I'd be grateful!

---

### Post by papibe on 2011-08-11
Open 'Network Connections'. Select eth0, and press edit. On the new window make sure the option 'Connect automatically' is checked. Also in the IPv4 tab, check that the method is set to 'Automatic (DHCP)'.

I hope it helps.

---

### Post by Overcast32 on 2011-08-11
> **papibe said:**
> Open 'Network Connections'. Select eth0, and press edit. On the new window make sure the option 'Connect automatically' is checked. Also in the IPv4 tab, check that the method is set to 'Automatic (DHCP)'.

I hope it helps.

Yeah, checked all that - it looks good. All set to auto, including IPV6. 

I don't recall... but I may have had a different system board when I installed Ubuntu. Of course, it does work when I nudge it like above, so would that matter since the driver does load?

---

