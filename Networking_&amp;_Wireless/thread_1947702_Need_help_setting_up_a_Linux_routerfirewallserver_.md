---
title: "Need help setting up a Linux router/firewall/server - how do I setup NIC's?"
date: 2012-03-27
forum: Networking &amp; Wireless
---

### Post by cilbuper on 2012-03-27
My current setup is a modem address of 192.168.254.254, a Linksys router with WAN IP (dhcp) of 192.168.254.1 and internal LAN IP 192.168.1.1.  I would like to set my linux box up with the same IP's if possible.  My computers on the network are using DHCP but I would like to be able to use the linux router as my DNS, gateway, etc.  

So my question is this.  can I leave the WAN NIC on the Linux router as DHCP since that is what the Linksys is set up to?  I am using eth0 for this NIC.

Now should I set the LAN NIC to static?  I would think this would be what I have to do so I can point all the rest of the computers to the static IP that I set.  If I set it to static what are the entries that I need to set?  I have seen places where I need 3 entries (address, netmask, gateway) or (address, network, netmask, broadcast, gateway).  I don't know what I need to put in the interfaces file.  

Also, do I need to setup some kind of bridge to bridge the two network cards or is this taken care of with other software? 

Oh, I have Webmin, LAMP and EHCP installed on this system and I think it is already all setup with DHCP, BIND, BIND DNS, and a lot of other packages - I think all are installed and ready to go.  

So what do I do with these NIC addesses?

---

