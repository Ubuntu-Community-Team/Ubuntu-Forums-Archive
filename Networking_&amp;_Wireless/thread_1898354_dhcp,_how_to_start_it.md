---
title: "dhcp, how to start it"
date: 2011-12-21
forum: Networking &amp; Wireless
---

### Post by granaet on 2011-12-21
LS

Lets start with the 'confession'  that my knowledge of linux/ubuntu is minimal. But I' am eager to learn.


- My hardware: motherboard asus p8h67-m pro, sandy bridge chipset, with I3-2100T CPU and 8 GBit of memory;
- the second NIC, a 3com type 3c905c-TX/TX-M, placed before the installation of
- Ubuntu 11.10 64-bit version.

My Fritzbox has a DHCP server which is used to give the eth0 its IP number. See also the attached network layout.

Plan is that this Ubuntu server replaces my old Compaq Proliant with windows 2003 which has also the router function.

The idea is that first I make DHCP working and than things like SAMBA, print server etc.

I' ve done the following:

sudo apt-get install dhcp3-server

/etc/default/dhcp3-server
INTERFACES="eth1"

/etc/network/interfaces
iface eth1 inet static
address 192.168.1.100
netmask 255.255.255.0
network 192.168.1.0
gateway 192.168.1.100

/etc/dhcpd.conf
default-lease-time 600;
max-lease-time 7200;
option subnet-mask 255.255.255.0;
option broadcast-address 192.158,1,255;
option routers 192.168.1.100;
option domain-name "ubuntu.local";
subnet 192.168.1.0 netmask 255.255.255.0 {
range 192.168.1.10 192.168.1.99
}


sudo service networking start


ifconfig eth1
learns that indeed eth1 has IP number 192.168.1.100 and that there is RS/TX activity

A windows PC connected to eth1 via a plain switch gets no IP number and can not ping the eth1 (when the switch is connected tot my win2k3 server it gets a IP number from the dhcp service of the win2k3 server)

Whats going wrong here?





greetings
from the Netherlands

---

### Post by Lars Noodén on 2011-12-21
I find [dnsmasq](http://manpages.ubuntu.com/manpages/oneiric/en/man8/dnsmasq.8.html) much easier to set up for DHCP.  Usually only one line needs to be changed in the configuration file.  Try that and see if it works for you.

---

### Post by jonobr on 2011-12-21
Hello

Im a bit confused about the config,

Your eth1 config seems to have a static Ip address defined, which is OK,
however, your defining the IP address of the Ethernet interface as  192.168.1.100 but your gateway is also defined as 192.168.1.100 also which seems incorrect

Also,

I dont know if this is a typo, but in your dhcp config, you define 
```
option broadcast-address 192.158,1,255;
```

There are two problems here, one is the subnet is incorrect, you have 192.158 that should be 192.168.1.255
also you have , (commas) instead of . (periods)

So instead of 192.158,1,255 put 192.168.1.255

So I would recommend you change the gateway in your interfaces file,
modify the dhcpd.conf file as above ,
start the dhcp service and post any errors.

If you dont see any and its not running
then try

```
cat /var/log/messages |grep dhcp
```

One other thing I should also add, 
The design you attached, is one entire network inside the same subnet.
This there is no routing in this area.

If you turn one of these machines into a router, then DHCP request will not be forwarded through that device unless it has a rule to forward it on.

---

