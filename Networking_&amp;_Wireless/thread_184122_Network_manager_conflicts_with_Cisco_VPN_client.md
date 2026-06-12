---
title: "Network manager conflicts with Cisco VPN client"
date: 2006-05-29
forum: Networking &amp; Wireless
---

### Post by Benjamin_Lebsanft on 2006-05-29
When using the Cisco VPN client to get access to my university's network my wireless network adapter alays gets disabled what results in no connection at all. After deleting network-manager it works without any problems but I need it to access my home network and some other WPA protected networks. What can I do?

---

### Post by [myrddin] on 2006-05-29
Hi,

Use vpnc and the vpnc plugin for network-manager. You'll love this combination :-)

You can get the plugin from [http://librarian.launchpad.net/2428420/network-manager-vpnc_0.5.99%2Bsvn20060403-0ubuntu1_i386.deb](http://librarian.launchpad.net/2428420/network-manager-vpnc_0.5.99%2Bsvn20060403-0ubuntu1_i386.deb)

hf

---

### Post by Benjamin_Lebsanft on 2006-05-29
I set up the vpn connection using the information in the profiles I use for the cisco client but I can't connect because "the program could not connect to the VPN server". I'm sure I filled in everything correctly.

---

### Post by [myrddin] on 2006-05-31
Did you try to connect to your university network using commandline vpnc with you dsl/isdn or whatever you have ( if your university supports this ) ?

---

### Post by Benjamin_Lebsanft on 2006-06-01
yes, vpnc doesn't tell me anything so I suppose it doesn't work. Cisco client works but only when uninstalling network-manager.

---

### Post by nedkelly on 2006-09-24
Thanx for the link to the networkmanger vpn package myrddin

---

