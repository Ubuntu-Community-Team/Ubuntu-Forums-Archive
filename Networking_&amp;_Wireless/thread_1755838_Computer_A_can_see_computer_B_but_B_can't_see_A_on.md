---
title: "Computer A can see computer B but B can't see A on internal LAN"
date: 2011-05-11
forum: Networking &amp; Wireless
---

### Post by tomneff0 on 2011-05-11
I have 5 computers set up, 4 with Ubuntu 11.04.
- "ABP" (desktop) is ethernet only and using Networking Tools, Trace Route, I can find all the other computers (CHE, MMC, CHI, & MIC).  This was set up under 10.10, then upgraded to 11.04.  I rebooted after upgrade.
- "CHE" (laptop) with ethernet and wireless card.  I can access the internet over both connections but using Trace Route, can't see ABP via ethernet or wireless.
- "MMC" (laptop) with broken wireless card but ethernet works fine.  I can access internet but using Trace Route, can't see ABP.
- "CHI" (laptop) same as CHE, above.
- "MIC" (file server) running Ubuntu 10.04.  Ethernet only.  I can find MIC using Trace Route from ABP but not the other way around.  However, I CAN find laptops from MIC and vice versa.

I tried Trace Route to both IP address and local host name.  Both work FROM ABP but neither works TO ABP.  From MIC to CHE, only IP address works.  Local host name does not get found.

I can connect via SSH using PuTTY from ABP to all other computers.  Cannot connect from laptops to ABP.  CAN connect from laptops to MIC.

All ethernet connections come out of a 5 port Linksys Network Everywhere hub.  Wireless router is Linksys WRT54GS.

I have CUPS installed on all machines but only have a printer on ABP.  I can print fine from ABP to attached printer.  However, I can't find printer from any of the laptops.  Suspect it's because the other computers can't find ABP.

It's beginning to sound like a configuration problem with ABP but I haven't a clue as to where to begin looking.

Thanks,
Tom

---

### Post by Iowan on 2011-05-11
Is it a DHCP network or do some/all the machines all have static address(es)?

---

### Post by tomneff0 on 2011-05-11
All IP addresses are static.

---

### Post by Iowan on 2011-05-11
Just double-checking some of the basics...
All machines are in same subnet?
**ping** yields same result as **traceroute**?
Any firewall installed on "ABP"? (**iptables** rules?)

---

### Post by tomneff0 on 2011-05-11
All pings are successful.  I tried each combination, both directions.

All IP addresses are 192.168.1.100 to 192.168.1.104

I never enabled any firewalls.  I just ran "sudo ufw disable" just to ensure.  I'll now reboot.  If anything changes, I'll reply again.

---

### Post by tomneff0 on 2011-05-11
Iowan,

Well, I didn't RECALL enabling any firewalls.  Apparently I had.  Now all computers can see all computers.

Thanks for the help.  This is more of a learning curve than expected.

Mission complete.

Tom

---

