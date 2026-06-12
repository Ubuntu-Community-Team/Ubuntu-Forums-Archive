---
title: "NetGear MA401RA Rev. D Access Point"
date: 2010-10-27
forum: Networking &amp; Wireless
---

### Post by mytinytown on 2010-10-27
I have an interesting setup here.

I am using an old SG20 server with Ubuntu 10.04 Server installed.

I am using an old NetGear card that is said to have issues (I have good reasons).

I would like the NetGear card to be an access point.

I have it set up as best as I can get it. I can see the card using a windows PCs, and I can connect to the card using auto DHCP I get limited connection and an odd IP address. If I set it up manual I have no connection either.

I a relative newbie with Linux especially command line style. I do not have the server as a DHCP server, I have a router for that and every time I try to set up the server as DHCP I loose the fixed IP it is and this is bad.

This is what is in my interfaces file.

```

# The loopback network interface
auto lo eth0 eth1 wlan0
    iface lo inet loopback


# Switch (LAN)
    iface eth0 inet static
    address 192.168.2.2
    netmask 255.255.255.0
    gateway 192.168.2.1


# WAN
#    auto eth1
#    eth1 inet dhcp


#Wireless Setup
    iface wlan0 inet static
    wireless-mode master
    wireless-essid Engineering_AP
    address 192.168.2.8
    netmask 255.255.255.0
    gateway 192.168.2.1

```Any more info or help would be appreciated!

---

### Post by mytinytown on 2010-11-03
I needed to set up a bridge connection.

My new interface looks like this:
```


 # The loopback network interface
     auto lo br0
     iface lo inet loopback
 
 
 # Switch (LAN)
     auto eth0
 iface eth0 inet manual
     post-up iptables-restore < /etc/iptables.up.rules
 
 
 # WAN
     auto eth1
     iface eth1 inet manual
 
 
 #Wireless Setup
     auto wlan0
     iface wlan0 inet manual
     wireless-mode master
     wireless-essid "Engineering_AP"
     wireless-channel 1
     wireless-key 1111111111
 
 
 #Bridge the above
     iface br0 inet static
     bridge_ports eth0 eth1 wlan0
     address 192.168.2.2
     netmask 255.255.255.0
     broadcast 192.168.2.255
     gateway 192.168.2.1

```

After I did:
```

brctl addbr br0

```

Works perfectly!

---

