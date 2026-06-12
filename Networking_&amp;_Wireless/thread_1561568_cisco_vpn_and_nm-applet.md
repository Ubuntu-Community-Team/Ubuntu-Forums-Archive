---
title: "cisco vpn and nm-applet"
date: 2010-08-26
forum: Networking &amp; Wireless
---

### Post by kswenson on 2010-08-26
I'm trying to use my university's VPN service (Uottawa) and am running into issues.
Starting nm-applet from the command-line I get the following warning when I try to import the .pcf file (attached):

** (nm-connection-editor:28285): WARNING **: Invalid setting VPN: IPSec gateway

This doesn't seem to bother nm-applet, however, as it seems to import the .pcf just fine.

I then choose "VPN Connections" -> "Off-Campus Connection" on the nm-applet and nothing happens.
The terminal gives the following warning, however:

** (nm-applet:28229): WARNING **: handle_property_changed: property 'vpn-state' changed but wasn't defined by object type NMVPNConnection.

Could anyone tell me what I'm doing wrong?
Thanks for the help.

---

