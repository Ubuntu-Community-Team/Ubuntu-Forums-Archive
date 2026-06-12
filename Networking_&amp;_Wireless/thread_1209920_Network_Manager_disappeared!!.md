---
title: "Network Manager disappeared!!"
date: 2009-07-10
forum: Networking &amp; Wireless
---

### Post by mj07h on 2009-07-10
Hi.  I'm new to Ubuntu.  I was attempting to get my wireless USB adapter to work when I believe that the Network Manager application stopped working and then disappeared.  I had used the X window to download and install another application for my wireless USB adapter right before this happened.  An error message came up that said something conflicted with the Network Manager application and after clicking this window NM disappeared.  Now I can't even get connected through ethernet!?!  Can anyone help?  I've since learned that I need to use "netdiswrapper" or something like that to get my Wireless USB adapter to work properly but I can't even get the ethernet to work.  Any help would be greatly appreciated.  Thanks!

---

### Post by The Cog on 2009-07-11
I think you will need to configure your ethernet by editing the file /etc/network/interfaces and /etc/resolv.conf by hand, to get static IP addresses and DNS working. Then you will be able to downlad the other software you need. Here are examples from my PC:
/etc/network/interfaces:
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
address 192.168.1.101
netmask 255.255.255.0
gateway 192.168.1.1

```
and /etc/resolv/conf:
```
nameserver 192.168.1.1
```
After editing these, **sudo /etc/init.d/networking restart** should make the settings active. If not, reboot.

I recommend removing gnome-network-manager and using wicd instead. Its one of the first things I do after installing.

You must remove the settings for eth0 from /etc/network/interfaces again before wicd will manage the interface.

P.S.
To edit these files, press Ctrl-Alt-F2 and enter the command **gksu gedit /etc/network/interfaces** .

---

