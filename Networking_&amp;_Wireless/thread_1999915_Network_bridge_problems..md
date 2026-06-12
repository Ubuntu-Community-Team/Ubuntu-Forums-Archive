---
title: "Network bridge problems."
date: 2012-06-08
forum: Networking &amp; Wireless
---

### Post by sona1111 on 2012-06-08
Hello again, this is a follow up to my other post in the server forum, which went a bit off topic. Anyway the short story is i was hosting a website on a server, and whic works fine with a standard ethernet cable connected to a port which is assigned a static ip, i have tested it this way and it was fine. The problem is that i want to distribute this internet connection (and some server utilities) to other devices with the server via a network bridge. 

The hardware is a ibm xseries 366 rackmount which is running ubuntu server 11.10 . It has 10 gigabit connections. Basically most of these are linked together with a network bridge. All of the devices connected to the ethernet ports can use the internet correctly, aswell as connect to the server. (they can connect port 80, ftp, vbox headless, transmission-deamon, etc.) The server itself, though, can NOT connect to the internet. Running a simple "sudo apt-get update" fails. equally as important, the server can not serve web pages. 

IF anyone has some idea what i did wrong with the interfaces file, please tell me. Here it is:

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# List of Network interfaces (hot plug)

#Comcast Internet / Voip
auto eth9
iface eth9 inet manual
up ip link set eth9 up

#gigabit output
auto eth4
iface eth4 inet manual
up ip link set eth4 up

#main output
auto eth3
iface eth3 inet manual
up ip link set eth3 up

#RSAII
auto eth8
iface eth8 inet manual
up ip link set eth8 up

#AUX bridged connection 1
auto eth5
iface eth5 inet manual
up ip link set eth5 up

#main bridge
auto br0
iface br0 inet static
bridge_ports eth9 eth4 eth3 eth8 eth5
bridge_fd 0
bridge_hello 2
bridge_maxage 12
bridge_stp on
address 192.168.3.82
gateway 192.168.3.1
netmask 255.255.255.0

#torrent downloader
auto eth11
iface eth11 inet static
address 192.168.2.80
gateway 192.168.2.4
netmask 255.255.255.0
```

---

### Post by sona1111 on 2012-06-08
well i have finally got it to work, though it is still not satisfactory for setting up. I have to follow these exact steps after the server starts up:

1) unplug eth11, the secondary internet connection which is only used for large downloads or torrents

2) sudo ip route add default via 192.168.3.1

3) plug eth11 back in

unless i do all three of these things in that order, it wont work. I do not even understand why eth11 matters because its not in the bridge. is their some setting somewhere to set the primary network interface?

---

