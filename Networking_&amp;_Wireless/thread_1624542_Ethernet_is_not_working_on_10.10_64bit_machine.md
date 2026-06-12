---
title: "Ethernet is not working on 10.10 64bit machine"
date: 2010-11-17
forum: Networking &amp; Wireless
---

### Post by nsisodiya on 2010-11-17
I was having 9.10 Ubuntu on my Desktop machine. Ethernet was working fine. I have installed Maverick 10.10 on it. Ethernet is not working.

$ lspci | grep -i ethernet
00.07.0 Bridge : nVidea Corporation MPC61 Ethernet (rev a2)

ifconfig do  not mention about eth0 etc..it just display "lo"

---

### Post by nsisodiya on 2010-11-17
I just run 

sudo dhclient

and Internet is now working, network-manager icon is not showing.
I did


sudo service network-manager restart

then icon comes but it says "device is not managed"
?

---

### Post by uncaspi on 2010-11-17
You must look in /etc/network/interfaces file and make a backup of it.

Delete all lines except

auto lo
iface lo inet loopback


Restart network-manager
sudo service network-manager restart

and you should be able to connect via network icon in upper right panel.

---

### Post by dineshs on 2010-11-18
> ifconfig do not mention about eth0 etc..it just display "lo"
```
ifconfig -a
``` will display  all  interfaces  which are currently available, even if down 
You may also try ```
sudo lshw -C network
```
Also ensure that the interface is enabled in BIOS

---

### Post by rabbitfoot on 2010-12-17
delet previous configured connection,then go to network tool,change network device loopback to ethernet (eth0),configure new connection as previous one.hope so it will work for u

---

