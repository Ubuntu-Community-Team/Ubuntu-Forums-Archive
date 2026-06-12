---
title: "share internet connection to a switch.."
date: 2009-02-05
forum: Networking &amp; Wireless
---

### Post by tednumber8 on 2009-02-05
i want to share my internet connection from ubuntu server to a sqitch.

Is this possible for me to do this?

---

### Post by Iowan on 2009-02-05
You mean the Ubuntu box connects to internet on one card, and has another card connected to switch?  It *should* work... Do you have the link for [ICS]("https://help.ubuntu.com/community/Internet/ConnectionSharing") help page?

---

### Post by tednumber8 on 2009-02-07
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp











Thats the ouptut

---

### Post by qman_txun on 2009-02-10
Yes, I can't share my Internet conection with other PCs and here's my interface setup

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth1
iface eth1 inet static
    address 67.46.66.1x
    netmask 255.255.255.2xx
    gateway 67.46.66.1x
    
# iface eth1 inet dhcp

auto eth0
iface eth0 inet static
    address 192.168.0.254
    netmask 255.255.255.0
    network 192.168.0.0
    broadcast 192.168.0.255

I just want to know what to do to get the Internet to the other PCs, I looked here [http://ubuntuforums.org/showthread.php?p=3713684](http://ubuntuforums.org/showthread.php?p=3713684) but to complicated to understand

Thanks

---

