---
title: "speedstream6520 &amp; small server, help"
date: 2010-01-20
forum: Networking &amp; Wireless
---

### Post by SirJ77 on 2010-01-20
Ok, my story is, my church has dsl through the local phone co, about a half dozen computers, plus visiting wireless computers.
DSL modem is a Speedstream 6520 router.  All computers work fine via dhcp.
I'm trying to setup a small server (print server, ssh & ftp servers).  I understand enough of the software part of things to get it going, my problem is setting a static IP on the server box.
Every time I set the IP in the /etc/network/interfaces file and reboot, I have no network connection.  I can talk to the modem through the browser, but nothing beyond that, not even local computers.

/etc/network/interfaces
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.254.202
network 192.168.254.0
netmask 255.255.255.0
gateway 192.168.254.254

ifconfig shows the .202 address, but box can't get to the outside world, and can't ssh into the box from a computer sitting next to it.  If I let it dhcp, then I can ssh into it, and have access to the internet.  In the modem, I have dmz set for that address.  Wan address is static.  I can ssh into it if I let it do dhcp, so I know it can work that far.  But if I set static ip, I might as well pull the network cable.
I've been beating my head on this for over a week, and I'm lost why I can't get it to work.
I even changed the dhcp range on the modem, so the .202 is not in that range.  There is no dhcp client installed that I can find.  
I'm using WattOS beta3, which is a light distro based on 9.04.  The computer is an old Dell GX150, integrated nic.
I have done ifdown and ifup eth0, still no happiness.
Doesn't seem like it should be that hard, but I'm stumped. DMZ should let everything pass, so don't need to mess with port forwarding and such.  I know it works using dhcp.

---

### Post by kitserve on 2010-01-21
Hi SirJ77, 

A lot of routers these days will let you reserve an IP address for a particular machine by MAC address. If it's at all possible I would definitely recommend you go down this route as it's much easier than messing around with the network config on the server. 

If that's not an option, are you 100% sure that the other settings are exactly the same as you get from dhcp? I know it's an obvious question, but I just want to check that the obvious hasn't been overlooked, that sort of thing always catches me out!

---

### Post by SirJ77 on 2010-01-21
I have the same modem as my church, and the only provision I can find for mac address is wireless security.  Sounded like a good idea though.
Having the same modem to home, I tried changing the IP on my windows machine... guess what, it don't work either.  It needs to be left dhcp.  That doesn't make much sense.

Still seems like it should work as is, but maybe this modem just isn't smart enough to let me do it.

My modem and the church modem are pretty much using defaults, so everything is pretty much equal.  My laptop is running WattOS as well, and it got 192.168.254.3 via wireless.  I've tried the same experiment (static ip) with the laptop with no luck.

ifconfig info off the laptop.
inet addr:192.168.254.3  Bcast:192.168.254.255  Mask:255.255.255.0

ipconfig of windows box...
Dhcp Enabled. . . . . . . . . . . : Yes
Autoconfiguration Enabled . . . . : Yes
IP Address. . . . . . . . . . . . : 192.168.254.1
Subnet Mask . . . . . . . . . . . : 255.255.255.0
Default Gateway . . . . . . . . . : 192.168.254.254
DHCP Server . . . . . . . . . . . : 192.168.254.254
DNS Servers . . . . . . . . . . . : 192.168.254.254
                                    192.168.254.254
Neither work being static ip.

---

