---
title: "DHCP Server no longer respones to DHCP Requests, can't ping gateway"
date: 2010-10-22
forum: Networking &amp; Wireless
---

### Post by KLStringer on 2010-10-22
Back in April I set up a Ubuntu DHCP server and a multiple VLAN network ([http://ubuntuforums.org/showthread.php?t=1465860&page=3](http://ubuntuforums.org/showthread.php?t=1465860&page=3)) to migrate our various servers, workstations, etc off the 192.168.1.1 /24 network that everything was on because we where running out of address space. I built out the new network and everything worked great except our AD server would never get an IP address from the DHCP server (static reservation) and even if I set the IP statically on the AD server it couldn't ping the gateway and noone could log in. After several attempts to resolve this, including bringing in outside help, we where never able to figure out what the problem was.

Now 6 months later I have time to revisit the issue without effecting the live network. I used Acronis and imaged the AD server last Friday, cloned it on to another box with the same hardware, and put it up on the new network that's been sitting unused for the last 6 months. 

Today when I statically set the IP on the AD server (which is what I want) it connects and I can ping it's gateway 192.168.1.1 and all the way across vlans to a test sales agent workstation at 192.168.8.xxx on vlan 800 but only if I statically assign the agents station an IP address. 

When I try to get an IP address via DHCP it fails as destination unreachable. Nothing has changed in the last 6 months on the DHCP server but now it for some reason can't ping its default gateway 192.168.1.1. All of the config files are the same as they where left from the post linked above aside from the vlan id's used where changed from 1's to 100's (i.e. vlan 3 is now vlan 300)

/etc/network/interfaces

```

auto lo
iface lo inet loopback

auto vlan100
iface vlan100 inet static

address           192.168.1.35
netmask           255.255.255.0
network           192.168.1.0
broadcast         192.168.1.255
gateway           192.168.1.1
hostname          valhalla
vlan_raw_device   eth0

```/etc/default/dhcp3-server    

 ```
INTERFACES="vlan100"
```Could really use some help figuring out why it can't reach the gateway, when I do a tcpdump I can see the DHCP requests come in on eth0 but the server never responds and I'm pretty sure its because it isn't "seeing" them since it thinks there isn't a network connection but I don't know how to trouble shoot to find out where the problem lies.

Thanks in advance for any help given it's very much appreciated. If there's anything someone may need to help out just ask me and I'll post the information a.s.a.p.

---

### Post by KLStringer on 2010-10-22
Still looking...

---

### Post by Iowan on 2010-10-22
Virtualization is still outside my realm, but if the machine was "cloned", it's possible that the information in */etc/udev/rules.d/70-persistent-net.rules* may need some tweaking. Often, a new interface gets created.

---

### Post by KLStringer on 2010-10-25
Sorry it took me so long to reply.

The Ubuntu DHCP server hasn't been cloned, only the windows AD server. The DHCP server hasn't been touched since it was configured back in April/May.

---

### Post by KLStringer on 2010-10-25
:-\"

---

### Post by KLStringer on 2010-10-26
I went through the steps here, [https://wiki.ubuntu.com/vlan](https://wiki.ubuntu.com/vlan) ,even though its not how everything was originally set-up and now when I try to restart the dhcp3-server service it fails and in syslogs it says that there's nothing defined for vlan100 in dhcpd.conf but vlan 100 is defined in dhcpd.conf.

None of this makes any sense, everything worked perfectly for the last 4 months and now nothing works without any rhyme or reason.

](*,)

---

### Post by KLStringer on 2010-10-27
dhcpd.conf 

```

authoritative;
 
ddns-update-style none;
default-lease-time 86400;
max-lease-time 86400;
log-facility local7;
option domain-name-servers 192.168.1.10, 192.168.1.11;

#
#
#

#### VLAN 100 Server's ####
    subnet 192.168.1.0 netmask 255.255.255.0 {
    range 192.168.1.56 192.168.1.230;
    range 192.168.1.236 192.168.1.250;
    option routers 192.168.1.1;
    option subnet-mask 255.255.255.0;
    option broadcast-address 192.168.1.255;
    option domain-name "harp.local";
}

##
##

#### VLAN 200 Reserved Not Used ####
#    subnet 192.168.2.0 netmask 255.255.255.0 {
#    range 192.168.2.2 192.168.2.254;
#    option routers 192.168.2.1;
#    option subnet-mask 255.255.255.0;
#    option broadcast-address 192.168.2.255;
#    option domain-name "harp.local";
#}

##
##

#### VLAN 300 I.T. ####
    subnet 192.168.3.0 netmask 255.255.255.0 {
    range 192.168.3.2 192.168.3.254;
    option routers 192.168.3.1;
    option subnet-mask 255.255.255.0;
    option broadcast-address 192.168.3.255;
    option domain-name "harp.local";
}

##
##

#### Vlan 500 Hardware ####
    subnet 192.168.5.0 netmask 255.255.255.0 {
    range 192.168.5.2 192.168.5.254;
    option routers 192.168.5.1;
    option subnet-mask 255.255.255.0;
    option broadcast-address 192.168.5.255;
    option domain-name "harp.local";
}

##
##

#### VLAN 600 Admin ####
    subnet 192.168.6.0 netmask 255.255.255.0 {
    range 192.168.6.2 192.168.6.254;
    option routers 192.168.6.1;
    option subnet-mask 255.255.255.0;
    option broadcast-address 192.168.6.255;
    option domain-name "harp.local";
}

##
##

#### VLAN 700 Reserved for Harp North ####
#    subnet 192.168.7.0 netmask 255.255.255.0 {
#    range 192.168.7.2 192.168.7.254;
#    option routers 192.168.7.1;
#    option subnet-mask 255.255.255.0;
#    option broadcast-address 192.168.7.255;
#    option domain-name "harp.local";
#}

##
##

#### VLAN 800 Agent Stations ####
    subnet 192.168.8.0 netmask 255.255.255.0 {
    range 192.168.8.2 192.168.8.254;
    option routers 192.168.8.1;
    option subnet-mask 255.255.255.0;
    option broadcast-address 192.168.8.255;
    option domain-name "harp.local";
}

##
##

###### Static IP Address Assignments ########

%CENSORED%


```

---

