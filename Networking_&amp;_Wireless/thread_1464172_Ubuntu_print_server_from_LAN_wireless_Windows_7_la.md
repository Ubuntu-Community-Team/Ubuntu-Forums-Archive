---
title: "Ubuntu print server from LAN wireless Windows 7 laptop"
date: 2010-04-27
forum: Networking &amp; Wireless
---

### Post by jackthechemist on 2010-04-27
PROBLEM:
I can't print from the laptop; I can print from the desktop.

PREAMBLE:
Hello again, Last time I posted the feedback was extremely helpful, so here I am once more.

SYNOPSIS:
I recently installed Ubuntu 9.10 Desktop (which I sort of regret; I'll be replacing it with server soon enough :P) to which an HP "Desktop-F4400-series" printer is connected. The desktop is hardwired to a Linksys wireless router from which an Acer laptop running Windows 7 is receiving it's Internet connection.


ADDITIONAL INFO:
The internal IPs for the  desktop and laptop are 192.168.1.100 and 192.168.1.102 respectively.
sudo ufw allow proto tcp to any port 631 from x.x.x.102
sudo ufw allow proto udp to any port 631 from x.x.x.100
sudo apt-get install cups cups-client
sudo apt-get install samba

Changed the following settings:
Sys>Admin>Printing:
Server>Settings: 
Checked "Show printers shared by other systems"
and "Publish shared printers connected to this system"
Server>Connect (after installing CUPS and samba)
Printer Properties:
Policies: Checked "enabled", "Accepting Jobs" and "shared"
Access Control: set to "Allow printing for everyone except these users" (none listed)
On the laptop I have windows FW turned off and McAffee set to allow all traffic to or from internal address range
something like 192.168.1.100 - 192.168.1.255
1)Control Panel>Devices and printers (lists a default XPS printer or something...)
2)Add a printer: from wireless local network etc..(windows can't find any)
3) tried to add a shared print by name: http:192.168.1.100:631/printers/Deskjet-F4400-series (get error)

SOMETHING CURIOUS
I noticed that on the desktop while I can 'see' the Windows PC in my
Places>Network(Windows Network) I get "Unable to mount location. Failed
to retrieve share list from server"
and on the laptop the existence of my desktop is well ... non-existent.
My gut tells me this latter problem is the true issue, but I am not a networking expert by any means.

Thanks for any suggestions/advice in advance.

Jack

---

