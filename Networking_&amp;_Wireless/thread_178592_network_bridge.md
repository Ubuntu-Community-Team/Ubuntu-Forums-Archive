---
title: "network bridge"
date: 2006-05-18
forum: Networking &amp; Wireless
---

### Post by dmizer on 2006-05-18
i'm trying to create a network bridge in order to allow my vm to have a local ip (primarily so i can print).

i've installed the bridge-utils package via synaptic.

when i do ifconfig, my br0 shows a network ip but i'm unable to browse on my host, and when i try to bridge in my vm, i only get 'could not open /dev/net/tun'

i do have a /dev/net/tun, but nano shows nothing in it.
i understand that this error can occur if my kernel does not have bridging built into it, so i checked that too:
$ grep CONFIG_TUN= /boot/config-2.6.12-10-686
CONFIG_TUN=m

i'm quite sure that i'm missing something pretty basic here, but i'm not sure what it is.

i edited etc/network/interfaces as follows:
```
 # /etc/network/interface
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The bridge network interface(s)
auto br0
iface br0 inet dhcp
bridge_ports eth0
bridge_fd 1
bridge_hello 1
bridge_stp off

#auto eth0
#iface eth0 inet dhcp
```

---

### Post by mips on 2006-05-18
What VM are you using ? I use vmware server. Connections are bridged in vmware. I have NO bridged configurations in my interfaces file and is not required.

---

### Post by dmizer on 2006-05-18
i'm using qemu.  isn't vmware a pay-for-it package?  i understand vmware is significantly better, but i don't want to be paying for my virtual machine so it can be a print server for my linux box.

but auto bridging does sound nice.  your vm has a local ip?

---

### Post by mips on 2006-05-20
[QUOTE=dmizer]i'm using qemu.  isn't vmware a pay-for-it package?  i understand vmware is significantly better, but i don't want to be paying for my virtual machine so it can be a print server for my linux box.

but auto bridging does sound nice.  your vm has a local ip?[/QUOTE]


Depends on which vmware product you are talking about. The vmware **player** & **server** are made available for free. Just download the server version and install.

Dapper guide: [http://doc.gwos.org/index.php/Vmware_server](http://doc.gwos.org/index.php/Vmware_server)
Breezy guide: Have a look in the HOWTOs, Tips & Tricks section

Yes, it gets an ip from my router/dhcp server so my pc & vm are in the same network.

---

### Post by dmizer on 2006-05-22
sorry, but on my machine (1ghz pIII with 256m of memory), vmware is unusably slow.  with kqemu/qemu, i had a vm up and running usably in about 5 minutes.

vmware takes over 20 minutes to boot windows, and then my machine lags so bad that i can't do anything with it.

so i'm back to square one.  how to create a bridge.

---

