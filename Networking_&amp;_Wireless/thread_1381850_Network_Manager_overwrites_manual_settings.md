---
title: "Network Manager overwrites manual settings"
date: 2010-01-15
forum: Networking &amp; Wireless
---

### Post by moforilla on 2010-01-15
I originally setup my network configuration without the Network-Manager tool. I use fluxbox and wanted to avoid having an extra application running for no reason.

The other day I accidentally plugged my Ethernet cable into the wrong port. I think this must have caused the Network-Manager to configure it and overwrite my manual settings.

I have restored my original settings to what they were but I still have problems. When I first login my eth0 does no have an IP assigned to it. I have to do a ifup eth0 to get an IP. I also noticed that after leaving the computer for a bit I had lost this assigned IP. I noticed this when looking at

```

nraic@localhost:~$ tail /var/log/messages
Jan 15 22:56:21 ricebox kernel: [ 7073.601753] eth0: link down.
Jan 15 22:56:23 ricebox kernel: [ 7075.401987] eth0: link up.
Jan 15 22:56:58 ricebox kernel: [ 7110.365951] eth0: link down.
Jan 15 22:57:02 ricebox kernel: [ 7113.914745] eth0: link up.
Jan 15 23:48:39 ricebox kernel: [10211.261430] eth0: link down.
Jan 15 23:48:41 ricebox kernel: [10213.040153] eth0: link up.
Jan 15 23:48:55 ricebox kernel: [10226.930781] eth0: link down.
Jan 15 23:48:56 ricebox kernel: [10228.615724] eth0: link up.
Jan 15 23:49:32 ricebox kernel: [10263.823173] eth0: link down.
Jan 15 23:49:35 ricebox kernel: [10267.403801] eth0: link up.
```

How do I get an IP for eth0 at startup and keep it?

---

### Post by chili555 on 2010-01-15
> How do I get an IP for eth0 at startup and keep it?You can certainly remove Network Manager completely and set up your details in */etc/network/interfaces.* If you decide to do this, we will be glad to assist.

---

### Post by moforilla on 2010-01-15
Yes, please that would be great.

The manual entries I have in my /etc/network/interfaces, resolv.conf and hosts are as follows.

```

nraic@localhost:~$ cat /etc/network/interfaces 
auto lo
iface lo inet loopback
iface eth0 inet static
address 192.168.1.104
network 192.168.1.0
netmask 255.255.255.0
broadcast 192.168.1.255
gateway 192.168.1.254

nraic@localhost:~$ cat /etc/resolv.conf 
nameserver 192.168.1.254

nraic@localhost:~$ cat /etc/hosts
127.0.0.1       localhost.localdomain   localhost
127.0.1.1       ricebox

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

I also noticed this in my /var/log/messages, note eth1 is not the interface I want to use. My settings are for eth0. It seems like something is forcing me to use eth1.

```

Jan 16 08:56:42 ricebox kernel: [   36.772434] skge eth1: enabling interface
Jan 16 08:56:42 ricebox kernel: [   36.775651] ADDRCONF(NETDEV_UP): eth1: link is not ready

```

These settings are working for me but I have to do a "sudo ifup eth0" after login. How do we remove Network Manager and make this automatic?

---

### Post by chili555 on 2010-01-16
> How do we remove Network Manager and make this automatic?Please go to System -> Administration -> Synaptic and, after entering your password, search for network. Mark *network-manager* for complete removal. If you have it installed, it will also remove *network-manager-gnome.* Next, let's edit /etc/network/interfaces to look like this:```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.1.104
netmask 255.255.255.0
gateway 192.168.1.254

#auto eth1
iface eth1 inet dhcp
```Proofread twice, save and close your text editor.

Your *hosts* and *resolv* look just fine. Restart networking:```
sudo /etc/init.d/networking restart
```Check to see if you are actually connected and have the correct IP address:```
ifconfig
ping -c3 www.google.com
```Please post back so the searchers will learn from your experience.

---

### Post by moforilla on 2010-01-17
Thank you chili555, that seems to have fixed it. I did originally have auto eth0 in my /etc/network/interfaces but I forgot what it meant. I removed it thinking it meant auto assign an IP like dhcp instead of using the static settings below.

I think it would be a good idea if the network-manager had to prompt the user before changing settings.

---

