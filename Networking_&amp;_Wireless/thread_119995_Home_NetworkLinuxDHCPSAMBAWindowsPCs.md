---
title: "Home Network/Linux/DHCP/SAMBA/WindowsPCs"
date: 2006-01-20
forum: Networking &amp; Wireless
---

### Post by Rajan Varadarajan on 2006-01-20
I set up a home network like the following:

4-Port DSL Modem/Router 
--> WinXPPro PC
--> Netgear Home Powerline Adapter
--> Netgear Wireless Broadcaster
--> 5-Port Ethernet Switch 
The 5-Port Ethernet Switch is connected to:
--> Win2003Server
--> WinXPProPC2
--> ubuntuDesktop
--> Suse10LinuxServer

Since I don't have all the machines powered on at the same time, the IP addresses need to be dynamic. So I have DHCP enabled on all the machines. All the machines except WinXPPro2 have two hard drives. I am using the second hard drive for data and have set them up for file sharing. All machines except the Win2003Server are able to connect to the Internet.

But I have a hard time configuring the network. Samba in the ubuntu machine recognized the Windows machines once but later stopped working. The Suse machine doesn't recognize anything.

I want to be able to set up the machines so that I can access them by machine name and not by a static IP address (which I suppose I can do).

Would appreciate any suggestions/how to's/ etc.

Thanks.
Rajan

---

### Post by souki on 2006-01-20
what is the question? ping windows machine from linux?

for this, there is several solutions:

1- have your linux computer to resolve with wins (/etc/nsswitch.conf)
2- set up the dhcp server to update dns records dynamically

a good documentation here: [http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/](http://www.samba.org/samba/docs/man/Samba-HOWTO-Collection/)

---

