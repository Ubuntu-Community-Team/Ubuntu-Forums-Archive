---
title: "Get the same IP always"
date: 2009-07-11
forum: Networking &amp; Wireless
---

### Post by tirengarfio on 2009-07-11
Hi,

i have a wireless router.

Each time i get start ubuntu i get a different IP (192.168.0.192, 192.168.0.193, 192.168.0.195, etc).

Any way to get always the same IP?

Ciao

Ubuntu 8.04

---

### Post by jonobr on 2009-07-11
Hello


Thats a function of your router, not the machine requesting the address.

IN a dhcp server you can define the IP address to be allocated based on your hardware address.

If you look around the menu of your routers there may be the option to assign based on mac, but it would probably be just easier to set your ubuntu machine to use a static IP that would be outside the scope of your DHCP allocation

---

### Post by tirengarfio on 2009-07-12
Thanks! I didnt know you can configure the router in that way...I thought it depends only on the os networking configuration..

---

### Post by Iowan on 2009-07-12
Some routers are not capable, but for those that are, it certainly simplifies some other setups. You don't need to manually set */etc/resolv.conf* (and try to keep Network Manager from changing it).

---

### Post by grappler on 2009-07-12
If you're using gnome-network-manager  (or pretty well any other network manager for that matter) you can set a static ip address in it. 

Right click on the icon and go to  "Edit Connections". Click on your current connection and then "Edit".

Under the Ipv4 settings tab enter 
 your choice of ip address - make sure that it's not one used by your router for dhcp. Then enter the netmask - usually 255.255.255.0 on a home network and the gateway - usually your router's lan ip address.  For example mine are

IP address : Netmask : Gateway

192.168.1.72 : 255.255.255.0 : 192.168.1.1

Then apply the changes and reconnect to the router. If your driver accepts static ip addresses - and most do - then you're in business.

---

