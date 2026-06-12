---
title: "Getting Network Manager VPNC to work (new 9.04 laptop)"
date: 2009-07-30
forum: Networking &amp; Wireless
---

### Post by mja2009 on 2009-07-30
Hi,

I'm new to Linux so please forgive me if I've missed something obvious but I've searched this forum and cannot find a solution.

I've installed 9.04 (and all updates) on a HP laptop along with the Network Manager VPNC plugin as I need to be able to connect to my office system from home.  I've configured the VPN connection with the same information I used on my XP installation for connecting to the PIX at the office (which I originally set up).

When I try to connect, however, the plugin almost immediately reports that the connection failed.  No other details, just connection failed.  I had a brief browse of the logs (all new to me) and in the syslog I found a few entries that indicated that the VPNC received a reply from the connection but the next messages indicate that the plugin itself failed.

VPN connection to the Cisco PIX at my office is essential for me (everything else I can adapt to) and I'm really liking what I see in the Ubuntu 9.04 installation but if I can't get VPNC working then I'm going to have to say goodbye to Linux and revert to XP.  I don't want to do a dual boot.

Does anyone have any ideas, where I could look for more detailed information for what's going wrong, or anything essential that I've missed.

All replies appreciated,

Thanks...


mja2009

---

### Post by bsntech on 2009-07-30
Do you have a PCF file for your Cisco VPN?  If so, I would maybe try Kvpnc and you can then import the PCF file directly into the client.

I've seen before where the Cisco VPNs will disallow connections from clients not using an up-to-date Cisco VPN package.  I can't recall how to change the header of what the application sends, but I know this is also an option in Kvpnc to "trick" the Cisco VPN into allowing the connection.

You can download the newest Kvpnc with a few bug-fixes here.  It may say Intrepid, but it also works with Jaunty.

[http://download.gna.org/kvpnc/kvpnc_0.9.1_intrepid-1_i386.deb](http://download.gna.org/kvpnc/kvpnc_0.9.1_intrepid-1_i386.deb)

---

