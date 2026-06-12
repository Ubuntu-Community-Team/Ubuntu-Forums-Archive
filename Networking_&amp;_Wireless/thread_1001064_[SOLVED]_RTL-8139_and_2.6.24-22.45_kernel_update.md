---
title: "[SOLVED] RTL-8139 and 2.6.24-22.45 kernel update"
date: 2008-12-03
forum: Networking &amp; Wireless
---

### Post by mikejaegerster on 2008-12-03
Pardon the interruption - this is no longer an issue and actually is not related to the kernel update at all.

Mike

Last week, I allowed the update manager to update my kernel from 2.6.24-22.36 to 2.6.24-22.45 (Hardy 8.04.1) for some security updates.  After I rebooted, I noticed that the network icon in the toolbar was spinning.  It reported it was trying to acquire an address.  This can go on for more than a few minutes everytime I reboot the computer.

I have an RTL-8139 NIC and am using a wired lan connection with DHCP.  I can get the same behavior by disabling, then enabling the interface.

I tried an experiment today where I start a ping to an external IP ([www.google.com](www.google.com)) and watch what happens as dhcp attempts to complete.  Successful pings show for many seconds but at least two times during the dhcp process, I received many seconds of Network is unreachable.

I see that both the 8139cp and 8139too drivers are loaded but I can rmmod 8139cp without changing anything.  If I rmmod 8139too, the interface is permanently down.

The interface has always come up completely if I wait long enough.  I'm just trying to get to the bottom of what takes so long for it to start up.

Let me know what information I may need to post if I can help.

Mike

---

