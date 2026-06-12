---
title: "GUI NETWORK Failure"
date: 2012-06-02
forum: Networking &amp; Wireless
---

### Post by phoenixcomm on 2012-06-02
I have loaded the current version of XMBCbuntu (11) and I have had problems with the network GUI - It claims that my nic is not connected. 
So just to test my nic I ran "ifconfig" and then could ping my gateway 
I wanted the XMBC to live at 192.168.1.150, as my network used fixed IP addresses.
Then I rebooted and did the following:

I have brought up a xterminal session from the main menu (not part of the GUI. 
I did "sudo sh" (that gave me root privliges)
Then I modified the /etc/networks/interface file 
Then I modified /etc/resolv.conf file (for my name server)
Then I rebooted, and then I was up on the Internet. :)

==> But when I launch the XMBC GUI (I added the weather plug-in and it works) my network GUI still claims that my nic is still not connected!!!  :rolleyes:

---

### Post by steeldriver on 2012-06-02
the way I understand it, the network manager GUI on the taskbar is an interface to the network-manager service - this is a relatively new way of doing things and is separate from the old networking service that is configured via /etc/network/interfaces

if you want to set a static IP via the network-manager interface, you can go via the Edit Connections menu item then select the connection and Edit -> choose the IPv4 settings tab and set everything up there (IP, DNS etc.)

or (better imo) you can leave everything auto on the client side and use address reservation on your router to tell its DHCP server to always supply the same IP to that device (by its MAC address) - doing it that way means all your static IPs are defined in one place and there's no risk of address conflicts

you can then delete your modified entry from /etc/network/interfaces and in fact stop the old networking service altogether (in the new way of doing things, /etc/network/interfaces *only* defines the loopback interface 'lo')

hope this helps

---

### Post by phoenixcomm on 2012-06-03
I have loaded the current version of XMBCbuntu (11) and I have had problems with the network GUI - It claims that my nic is not connected. 
So just to test my nic I ran "ifconfig" and then could ping my gateway :KS
I wanted the XMBC to live at 192.168.1.150, as my network used fixed IP addresses.
Then I rebooted and did the following:

I have brought up a xterminal session from the main menu (not part of the GUI. 
I did "sudo sh" (that gave me root privliges)
Then I modified the /etc/networks/interface file 
Then I modified /etc/resolv.conf file (for my name server)
Then I rebooted, and then I was up on the Internet. :KS

==> But when I launch the XMBC GUI (I added the weather plug-in and it works) my network GUI still claims that my nic is still not connected!!!  :rolleyes:

---

### Post by praseodym on 2012-06-03
Change "false" to "true" in the file **/etc/NetworkManager/NetworkManager.conf**, otherwise the manual "interfaces"-settings are ignored.

---

### Post by Iowan on 2012-06-03
Threads merged.
From the Code of Conduct:
> Do not cross post, or post the same thing in multiple locations.

---

