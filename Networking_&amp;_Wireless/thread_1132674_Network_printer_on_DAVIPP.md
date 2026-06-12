---
title: "Network printer on DAV/IPP"
date: 2009-04-22
forum: Networking &amp; Wireless
---

### Post by Joushou on 2009-04-22
Hi!

I've been looking at my schools network printer configuration for quite some time...
I've been told that the URI for the printer i need access to is "https://eprint.tec.dk/printers/sjv-5-232-printer1/.printer", and i've been told it's DAV _AND_ IPP...
So, i tried to add the printer as IPP... but it told me it couldn't get the queue, because "network printers do not support it"...
Then i tried throwing the URI into "others", but that gives me a "client-error-not-possible".
Also, trying through the cups interface fails, saying it's a bad device URI... i've tried without the https, with port number, and with user/pass in the uri...
Any ideas?

The print-server seems to be ISA, and the printer is a HP Laserjet p4015x.
I can print to the printer directly on wired network, but the problem is that i have to get through their VPN on wi-fi, which separates me from the wired network, leaving their isa server as the only connection between the two...

I hope someone is willing/able to help, because i'm clueless (So are the sysadmins)...

---

