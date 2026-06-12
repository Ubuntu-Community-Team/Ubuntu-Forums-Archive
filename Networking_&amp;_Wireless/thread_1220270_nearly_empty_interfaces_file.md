---
title: "nearly empty interfaces file?"
date: 2009-07-22
forum: Networking &amp; Wireless
---

### Post by tahnok on 2009-07-22
Hello

I was trying to setup an openVPN server on an Ubuntu 9.04 box and the tutorial asked me to mess with my /etc/network/interfaces file and so I opened it up only to find it was almost empty! There's an entry for the loopback interface, but my eth0 interface isn't there. Is this normal?

---

### Post by superprash2003 on 2009-07-23
yes , if your network manager is handling those interfaces

---

### Post by jamest09 on 2009-07-23
Are you using NetworkManager to manage your network interfaces, if so, then that file will be mostly empty.

What does the openvpn instructions tell you to put in there?

---

### Post by tahnok on 2009-07-23
Yes I am using network manager to manage my connections.

Well it's asking me to create a bridged interface. The instructions are [help.ubuntu.com/community/OpenVPN ]("https://help.ubuntu.com/community/OpenVPN")

They suggest having the file look like this
```
## This is the network bridge declaration
auto lo br0  ## start on boot

iface lo inet loopback

iface br0 inet static 
  address 192.168.1.10 
  netmask 255.255.255.0
  gateway 192.168.1.1
  bridge_ports eth0

iface eth0 inet manual
  up ifconfig $IFACE 0.0.0.0 up
  up ip link set $IFACE promisc on
  down ip link set $IFACE promisc off
  down ifconfig $IFACE down 
```

---

