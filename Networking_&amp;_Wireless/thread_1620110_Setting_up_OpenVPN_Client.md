---
title: "Setting up OpenVPN Client"
date: 2010-11-12
forum: Networking &amp; Wireless
---

### Post by faulknerm on 2010-11-12
Evening,

I'm running Ubuntu Netbook 10.10 and am wanting to connect to my companies VPN.

Our IT support guys have provided me with the following - 

[B]Username and password
[/B]**Office.ovpn file** (which when opened in a text editor appears to be a config file - lists server addresses and settings etc.)
**OpenVPN-Keys.zip file** (which when extracted contains ca.crt, client.crt, client.csr and client key).

I have installed the Gadmin OpenVPN client from the Ubuntu software centre, however I'm struggling with how to set it up using the resources IT have given me - the import option (to import a config file) says the file I have is an incorrect format and if I try to enter everything manually into the boxes and then add the connection it tells me that I need to import first?


Can anybody please help me out? Or is there a How-To somewhere online?

Cheers,

---

### Post by faulknerm on 2010-11-12
Scratch that...just discovered network-manager-openvpn.

All settings now in, however when I try to connect to the VPN I get a timeout error every time. Can't rule out a connectivity issue at work, however seems unlikely as other services are still working OK.

Any thoughts on the cause of a timeout error?

---

### Post by faulknerm on 2010-11-15
Anybody any thoughts on this? I'm still getting the timeout error message when I try to connect :(

Edit: Seems to not be connectivity at the other end, as I can ping the VPN server addresses fine.

---

### Post by faulknerm on 2010-11-17
Have also confirmed that this isn't a local connectivity (firewall) issue as I can't connect from other locations either or using my mobile internet dongle.

---

