---
title: "Network printer blocked by Firestarter"
date: 2011-04-25
forum: Networking &amp; Wireless
---

### Post by irw on 2011-04-25
I have spent hours searching for the solution here, but have not found any answers that work yet.

I have Ubuntu 10.4, connected to an office network.
We have two HP Laserjet printers on the network (network, not attached directly to a PC).

When I disable the firewall using Firestarter, I can print without problems.
If the firewall is enabled, I cannot print. I can scan (one printer is multifunction), but neither printer will print for me.

If I try to print, I get an OSD to say print job started, then a second to say print job is finished. Nothing comes out of the printer

Looking at CUPS, there is a message> 
held since
Mon 25 Apr 2011 04:17:14 PM GMT 
"/usr/lib/cups/backend/hp failed"
If I disable the firewall, then click on "release job" then the file is printed.

In Firestarter there is no record in 'Active Connections' or 'Events' of the computer trying to connect to the printer.
I have tried to set policy to allow connections to the IP address of the printers, but nothing seems to help.

I found some threads relating to this in 2005, but they have not helped.

What is frustrating is that I have had no problems before, and this has only come up since a reformat and re-install of 10.4 on this computer.

Any suggestions?

---

### Post by yellowpike on 2011-04-25
**Hardly **an expert my friend but perhaps a reinstall of the printer/drivers ?
Hope it's helpful !

yellowpike

---

### Post by irw on 2011-04-26
Why would that work - the printers work fine, without the firewall.
(But I had tried that anyway!)

---

### Post by irw on 2011-04-28
So no-one has any other ideas?

---

### Post by yellowpike on 2011-04-28
With the firewall active are you able to ping the network printer?
As for the driver reinstall it was but a suggestion my friend.

Regards
yellowpike

---

