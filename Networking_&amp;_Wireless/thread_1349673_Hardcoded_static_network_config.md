---
title: "Hardcoded static network config?"
date: 2009-12-08
forum: Networking &amp; Wireless
---

### Post by symbiat on 2009-12-08
When I look in Network Manager it seems I dont have any options to set up static configuration for eth0 - all I see is 'Auto eth0'. I remember seeing a static option before - dont know why it disappeared.

Is there a way to disable Network Manager and set up my network cofiguration hardcoded into config files? Would prefer to have it done that way.

---

### Post by chili555 on 2009-12-08
The most reliable way to disable Network Manager is to remove it in Synaptic. Then you will need to amend two files. First, */etc/network/interfaces*:```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.1.105
netmask 255.255.255.0
gateway 192.168.1.1
```Now, */etc/resolv.conf*:```
nameserver 192.168.1.1
```Adjust these numbers to suit your network. The static IP address you want must be outside the IP address range of the DHCP server in your router.

Restart the interface:```
sudo ifdown eth0 && sudo ifup eth0
```Please post back if you need additional guidance.

---

### Post by doas777 on 2009-12-08
I agree that the best method is to config your interfaces file, but if you highlight "Auto Eth0" and click edit, you should be able to find the specific settings. "auto" in this case, does not mean DHCP vs Static, it just means that the interface is automatically brought online by the OS. 

there was a bug in Intrepid, where it would always lose static settings applied to the "Auto Eth0" interface, so I always deleted it, and created a new one called "eth0". you can find your mac address for creating a new connection, with 'ifconfig'.

one of the primary reasons I like configuring the interfaces file, is that when you use network manager, you have to be logged for the network to be online. if you have samba shares, or other network services, they will fail unless you are first logged in, and the service is restarted. a major pain when trying to run a fileserver.

so not sure if that helps, but good luck.

---

### Post by Iowan on 2009-12-08
Dunno about Karmic, but Jaunty's NM had an IPv4 tab that let you do manual configuration (even on Auto eth0).

---

### Post by symbiat on 2009-12-22
@chili555: Sorry for the slow response. Your instructions worked just fine but my netmask was wrong (which left me scratching my head for awhile).

Thanks.

Now on to the firewall config... ;-)

---

### Post by chili555 on 2009-12-23
Glad it's working! Enjoy!

---

