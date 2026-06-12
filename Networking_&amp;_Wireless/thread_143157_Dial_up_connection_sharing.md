---
title: "Dial up connection sharing"
date: 2006-03-11
forum: Networking &amp; Wireless
---

### Post by eriefisher on 2006-03-11
I have serial modem that works perfectly and want to share the connection on my LAN. The problem is that as soon as I activate eth0 I can no longer communicate with the modem. There must be a way of forwarding this connection to my LAN. This is also preventing me from creating the local network to start with since I can't use it anyway. I realize that use will limited due to speed but it would be nice to switch back and forth from different computers without disconnecting and reconnecting.

Also is there someway of controling this connection from another computer on the LAN(connect and disconnect)?

eriefisher

---

### Post by Sendervictorius on 2006-03-12
Use System>Administration>Networking; and make sure the default gateway setting is ppp0 - not eth0. I suspect when you boot it is selecting eth0 by default.

To use your PC to allow others on your network to access your modem connection, you will have to set up your PC to provide connection sharing.

The easiest way is to install firestarter from synaptic.
In Firestarter: Edit>Preferences            then   Firewall>Network Settings 
- set ppp0 as your internet device
- set eth0 as your local network connect device
- and enable internet connection sharing
- enable DHCP if you want to use it to allocate ip addresses to your other connected PCs.

---

### Post by Sendervictorius on 2006-03-13
[QUOTE=eriefisher]

Also is there someway of controling this connection from another computer on the LAN(connect and disconnect)?

eriefisher[/QUOTE]

Yes, you can do this with diald - dial on demand daemon - running on your main PC.  diald monitors out-going IP packets and can stop ppp after an idle period and start it up again when activity resumes. When any other computer wants to connect, diald should automatically bring up the ppp interface.

diald is on synaptic. I haven't used it, so can't be much help.

---

### Post by eriefisher on 2006-03-13
Thanks for the info. I just downloaded the Firestarter pdf and it looks like it will do the trick. I will have to look into Diald, sounds interesting.

eriefisher

---

