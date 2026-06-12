---
title: "/etc/network/interfaces file is near blank?"
date: 2009-11-14
forum: Networking &amp; Wireless
---

### Post by Tsquad on 2009-11-14
Hello, im new to ubuntu and linux, im using 9.10 and am trying to set a static ip. Iv been doing some reading and it seems like my /etc/network/interfaces file should look something like below

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).
# The loopback network interface
auto lo
iface lo inet loopback
#
# The primary network interface
auto eth0
iface eth0 inet static
address 10.0.0.1
netmask 255.255.255.0
network 10.0.0.0
broadcast 10.0.0.255
gateway 10.0.0.1
#
auto eth1
iface eth1 inet dhcp




BUT!!! it really only looks like this....


auto lo
iface lo inet loopback



whats the deal here? anyone know?

---

### Post by JBAlaska on 2009-11-14
Have you tried right clicking on network manager and selecting "edit connections", click on your network interface and click "edit" then select the ipv4 tab, select "method manual" and enter your static ip, netmask, gateway and dns server ip's. you can also click on the ipv6 tab and select "ignore".

---

### Post by Iowan on 2009-11-14
Your */etc/network/interfaces* looks pretty normal for a Network Manager controlled machine. Your sample looks like pre-Hardy (which is when NM started being used) although it will still work. Try the Manual setup via NM first...

---

