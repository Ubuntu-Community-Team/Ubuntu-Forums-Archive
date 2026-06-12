---
title: "static IP issue"
date: 2009-05-22
forum: Networking &amp; Wireless
---

### Post by b00mer on 2009-05-22
Hi,
I'm trying to have a static IP assigned to my server.  Right now everything works fine Using DHCP but when I try to set the static IP, it won't get assigned. 

If I open etc/network/interfaces, all I see is:

auto lo
iface lo inet loopback

I don't see eth0.

If I edit the inerface file like below, it doesn't get assigned.

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.1.10
gateway 192.168.1.1
netmask 255.255.255.0

I'm running a Linksys WRT54G2 Router (not wireless and DHCP ports beginning at 192.168.1.100)/ Ubuntu 9.04 Desktop with Apache, MySQL, PHP, installed / Dell Optiplex 260 Desktop 

I've removed Network Manager from the applications. 

Any advice on how to fix this would be welcomed.

Thanks

---

### Post by superprash2003 on 2009-05-22
what error do you get when you type **sudo /etc/init.d/networking restart** .also post output of ifconfig

---

### Post by b00mer on 2009-05-22
sudo /etc/init.d/networking restart gives me "command not found"

output of ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0b:db:3d:18:95
          inet addr:192.168.1.104  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20b:dbff:fe3d:1895/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1070902 errors:0 dropped:0 overruns:0 frame:0
          TX packets:941315 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100
          RX bytes:101609394 (101.6 MB)  TX bytes:164331513 (164.3 MB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4574 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4574 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:7715610 (7.7 MB)  TX bytes:7715610 (7.7 MB)

---

### Post by Iowan on 2009-05-22
You can check /etc/init.d for the "networking" file - it *should* be there...
Another option is to set up a static lease (based on MAC address) in your DHCP server.

---

### Post by superprash2003 on 2009-05-23
as mentioned by Iown , i think thats your problem..

---

