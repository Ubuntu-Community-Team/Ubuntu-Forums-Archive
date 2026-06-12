---
title: "using wired connection and DSL concurrently"
date: 2012-01-17
forum: Networking &amp; Wireless
---

### Post by swamprat222 on 2012-01-17
Upgraded to Ocelot 11.10.

Have one problem I can't find an answer for. I have a wired network, one file server, one Ubuntu PC, One windows PC. All are on the same workgroup. Internet is DSL and works fine. The problem is if I want to use the network, I have to disable DSL in network manager, and if I want to use the internet I have to disable wired connection in network manager. Previously using a manual PPPoE setup and Ubuntu 10.04 (?) I was able to do both at the same time.

I have rudimentary Ubuntu/Linux skill, I'm really an i/OS person. But can provide more detail as needed. I'm hoping this is a common issue, I just can find any forum references or documentation to this problem. 

Basically I need to use a manual, and DHCP connection on eth0 at the same time.

---

### Post by swamprat222 on 2012-01-20
solved: using directions found at this URL.

[http://www.techotopia.com/index.php/Connecting_an_Ubuntu_Linux_System_to_a_DSL_Modem](http://www.techotopia.com/index.php/Connecting_an_Ubuntu_Linux_System_to_a_DSL_Modem)

Need to manually configure DSL using pppoeconf on the command line. Ignore the network connection leave wired connection # enabled, don't configure DSL, or ignore the configuration.

---

### Post by swamprat222 on 2012-01-21
Okay so it wasn't fixed.
I have a very simple network. 4 PC's on the same internal network. So have both DSL and Samba on the same network interface you need the link in the previous post and this one.

[http://www.ubuntugeek.com/ubuntu-networking-configuration-using-command-line.html](http://www.ubuntugeek.com/ubuntu-networking-configuration-using-command-line.html)

/etc/network/interfaces look like this - notice no gateway was added since it is a private network. Now I have both on one ethernet adapter.

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 210.1.21.2
netmask 255.255.255.0
network 210.1.21.0
broadcast 210.1.21.255

auto dsl-provider
iface dsl-provider inet ppp
pre-up /sbin/ifconfig eth0 up # line maintained by pppoeconf
provider dsl-provider

---

