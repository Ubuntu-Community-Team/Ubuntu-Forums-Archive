---
title: "Wired LAN not connecting with RTL8100C"
date: 2012-09-20
forum: Networking &amp; Wireless
---

### Post by davesbrain on 2012-09-20
The mobo is a 945GCT-M3 with onboard RTL8100C lan.  Tried other live cd's with no luck.  Even tried other nic cards,a D-Link and Linksys, no luck.  I've connected other computers and laptops running Ubuntu to same modem without any issue.

---

### Post by davesbrain on 2012-09-20
When trying an LNE100tx Linksys card(onboard RTL8100c disabled), I get Auto eth0 and Auto eth1.  Auto eth1 shows connected at the network manager icon and gives full info under connection information.   However, still nothing through firefox and software center.  They just hang

---

### Post by jrog on 2012-09-20
> **davesbrain said:**
> When trying an LNE100tx Linksys card(onboard RTL8100c disabled), I get Auto eth0 and Auto eth1.  Auto eth1 shows connected at the network manager icon and gives full info under connection information.   However, still nothing through firefox and software center.  They just hang
Are you able to ping 127.0.0.1 successfully? If so, are you able to ping your router/modem (whatever is giving you an IP address when you connect to the network) successfully? If so, are you able to ping, say, 208.67.222.222 successfully? (If you don't know, you can do all of this by opening a terminal and typing "ping -c 3 <ip address>" without the quotes, inserting the IP address for <ip address>.)

And what version of Ubuntu is this?

---

### Post by davesbrain on 2012-09-21
I'm sorry I should have specified, it's 10.10.  And the onboard RTL8100C is disabled in the bios.

Test results are all negative, got nothing with all of your suggestions.  And I tried Auto eth0 and Auto eth1.  I was using the 'Network Tools' app under System/Admin menu to try the pinging.

---

