---
title: "Can't connect to Broadband Ubuntu 9.10"
date: 2009-11-17
forum: Networking &amp; Wireless
---

### Post by priyaaank on 2009-11-17
Hi all.

I have recently installed ubuntu 9.10. I have been trying to configure my laptop to use a broadband connection with a static ip. However even after repeated tries I have been graa vely unsuccessful. 

I have following details with me:
Ip address
Gateway address and
Subnet mask.

I also have two DNS server addresses.

Using the network configuration utility; I tried to set a "wired" connection of type "Manual". I set the respective values and tried; however it doesn't connect.

In windows same settings works just fine. I also tried to do a 
sudo ifconfig eth0 down 
sudo ifconfig eth0 up

just to ensure that I refreshed the connection. But again no luck.

also tried, making changes to the interfaces file directly and restarting networking service. But again no use.

I have resorted to every possible solution I could find over net. Could someone please guide me as to how I should configure the internet?

It's a wired static ip connection. I use a DHCP auto eth0 in office and it works just great; however at home the static one doesn't work.

Thanks for all the help in advance.

---

### Post by esteban- on 2009-12-25
[SIZE=2][COLOR=Blue]Solved for me!!  –  for wired network card…with auto DHCP
[/COLOR][/SIZE]
[SIZE=2][COLOR=Blue]
[/COLOR][/SIZE]
 [SIZE=2][COLOR=Blue]installed file –  [COLOR=Green]/etc/network/interfaces[/COLOR]  –    looks like this….[/COLOR][/SIZE]
[SIZE=2][COLOR=Blue]
[/COLOR][/SIZE]
 [SIZE=2][COLOR=Blue]auto lo
iface lo inet loopback[/COLOR][/SIZE]
[SIZE=2][COLOR=Blue]
[/COLOR][/SIZE]
 [SIZE=2][COLOR=Blue]_[COLOR=Blue]edit[/COLOR]_ – [COLOR=Lime]  [COLOR=Green]/etc/network/interfaces[/COLOR][/COLOR]  –  to look like this…[/COLOR][/SIZE]
[SIZE=2][COLOR=Blue]
[/COLOR][/SIZE]
 [SIZE=2][COLOR=Blue]auto eth0
iface eth0 inet dhcp[/COLOR][/SIZE]
[SIZE=2]
[/SIZE]
[SIZE=2]save that and connect; you may have to reboot[/SIZE]

---

