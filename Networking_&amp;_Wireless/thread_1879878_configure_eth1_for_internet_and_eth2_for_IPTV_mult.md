---
title: "configure eth1 for internet and eth2 for IPTV multicast"
date: 2011-11-12
forum: Networking &amp; Wireless
---

### Post by its_johan on 2011-11-12
Hello,
I am trying for weeks to get my multicast stream going.
I have 100mbps fibre connection and the 'modem' has 2 outputs, 1 for internet, 1 for udp IPTV.
I would like to configure the following:
eth1 to see the internet via my router (192.168.1.1)
eth2 to see the multicast TV stream via my modem IPTV output (UDP\\@225.1.1.xxx:1111, xxx is the TV channel number)
 
I always have tried a lot of settings, but OR eth1 working but no IPTV, OR eth2 works but no internet.
 
current settings (not working since the modem IPTV port does not have dhcp):
/etc/network/interfaces
 
```

auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0
 
auto eth0
iface eth0 inet manual
up ifconfig eth0 up
 
auto eth1
iface eth1 inet static
address 192.168.1.118
netmask 255.255.255.0
gateway 192.168.1.1
 
auto eth2
iface eth2 inet dhcp
 
up route add -net 224.0.0.0 netmask 240.0.0.0 dev eth2
```[IMG]http://reelbox-forum.com/attachment.php?attachmentid=1248&d=1316098151[/IMG]

---

