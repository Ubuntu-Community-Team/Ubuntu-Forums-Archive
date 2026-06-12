---
title: "Connecting with VPN"
date: 2009-11-24
forum: Networking &amp; Wireless
---

### Post by chemjeff on 2009-11-24
Hi all, I'm having difficulty connecting to a VPN server.  I'm using Ubuntu version 9.10 and I'm using the NetworkManager applet.  I've tried all three of the NetworkManager VPN clients and none of them are able to connect.  I either get the "no valid secrets" error or I simply get no response at all.  Any thoughts?  I'm able to connect using a Cisco VPN client on my Windows laptop that is connected to the same DSL modem as my Linux computer, so I don't think the issue is with the VPN server.  Any help would be greatly appreciated!

---

### Post by Steven_B on 2009-11-24
I've got the same problem.
Maybe it's related to this bug? [https://bugs.launchpad.net/ubuntu/+source/network-manager-vpnc/+bug/360818]("https://bugs.launchpad.net/ubuntu/+source/network-manager-vpnc/+bug/360818")

EDIT:
I've gotten it working by following the directions for pptp here:
[http://ubuntuforums.org/showpost.php?p=8261958&postcount=6](http://ubuntuforums.org/showpost.php?p=8261958&postcount=6)

I think the important part is not typing in your password/domain in the setup dialog, but instead putting it in when you try to connect.

---

