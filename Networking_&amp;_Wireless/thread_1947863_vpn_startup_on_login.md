---
title: "vpn startup on login"
date: 2012-03-27
forum: Networking &amp; Wireless
---

### Post by AnotherBrian on 2012-03-27
On natty (11.04) I have a vpn that i want to start on login.  The vpn has been configured through networkmanager.  It works fine  when manually started through networkmanager after login.   

Instructions exist for edgy 6.10 at [https://help.ubuntu.com/community/VPNClient](https://help.ubuntu.com/community/VPNClient) to have the vpn startup on login but they are outdated.  Those instructions state:
[INDENT]You can easily make the network manager applet start on log-in by adding the command *nm-applet*  to your sessions. (Under System->Preferences->Session by default)  However, this doesn't mean your configured connection fires up too. To make this happen you can add another command to your session startup programs: 
/usr/lib/network-manager-vpnc/nm-vpnc-auth-dialog -s <service_name> -n <connection_name> 
Connection name is the name of your connection and service_name can be one of the following: 

[LIST]
[*]the PPTP plugin, 'org.freedesktop.[NetworkManager]("https://help.ubuntu.com/community/NetworkManager").pptp'
[*]the Cisco VPNC plugin, 'org.freedesktop.[NetworkManager]("https://help.ubuntu.com/community/NetworkManager").vpnc'
[*]the OpenVPN plugin, 'org.freedesktop.[NetworkManager]("https://help.ubuntu.com/community/NetworkManager").openvpn'
[/LIST]
[/INDENT]Natty has no System->Preferences->Session.  For natty, should this be System->Preferences->Startup Applications? 

Also, there is no nm-vpnc-auth-dialog command but there is a /usr/lib/network-manager-openvpn/nm-openvnp-auth-dialog command.  There is no man page for the command.  The parameters suggested for edgy above do not work here. 

Suggestions?

---

### Post by AnotherBrian on 2012-03-27
although others may be interested for other releases

---

