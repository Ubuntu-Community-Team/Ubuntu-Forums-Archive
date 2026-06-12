---
title: "DHCP Server for multiple Vlan's"
date: 2010-04-29
forum: Networking &amp; Wireless
---

### Post by KLStringer on 2010-04-29
I'm working on setting up a Ubuntu DHCP server as part of a network restructuring. I've read a couple guides:

[https://help.ubuntu.com/community/dhcp3-server](https://help.ubuntu.com/community/dhcp3-server)

[http://www.ubuntugeek.com/how-to-install-and-configure-dhcp-server-in-ubuntu-server.html](http://www.ubuntugeek.com/how-to-install-and-configure-dhcp-server-in-ubuntu-server.html)

on how to set up the initial configuration.

The network that I'm setting up will have:

Vlan 3 IP Address 192.168.3.1 /24 Gateway 192.168.3.1
Vlan 4 IP Address 192.168.4.1 /24 Gateway 192.168.4.1
Vlan 5 IP Address 192.168.5.1 /24 Gateway 192.168.5.1
Vlan 6 IP Address 192.168.6.1 /24 Gateway 192.168.6.1
Vlan 7 IP Address 192.168.7.1 /24 Gateway 192.168.7.1
Vlan 8 IP Address 192.168.8.1 /24 Gateway 192.168.8.1

The server will be static on 192.168.4.187 
The domain is Cars.local

How do I edit the cfg file to reflect the above?

Thanks in advance for any help its much appreciated.

---

### Post by DGortze380 on 2010-04-29
>  The server will be static on 192.168.4.187 

I think you'll need a valid IP on each VLAN. Remember VLANS break up broadcast domains, so a broadcast packet from 192.168.(3,5-8 ).x won't make it to the 192.168.4.x subnet.

It looks like there are some tricks you can play with Unicast to get around this ([http://tcpmag.com/qanda/article.asp?editorialsid=285](http://tcpmag.com/qanda/article.asp?editorialsid=285))...

But the simplest solution would be to set up multiple Virtual Interfaces on the DHCP Server (Virtual instead of Physical due to the large number of VLANS you want).

---

### Post by KLStringer on 2010-04-29
So far I've edited /etc/default/dhcp3-server to listen on eth1 instead of on eth0,

added to dhcpd.conf:

# VLAN 3 TEST CONFIG
subnet 192.168.3.0  netmask 255.255.255.0 {
range 192.168.3.2 192.168.3.254;
option routers 192.168.3.1;
option broadcast-address 192.168.3.255;
}

# VLAN 6 TEST CONFIG
subnet 192.168.6.0  netmask 255.255.255.0 {
range 192.168.6.2 192.168.6.254;
option routers 192.168.6.1;
option broadcast-address 192.168.6.255;
}

and added a static address the eth1:
auto eth1
iface eth1 inet static
    address 192.168.4.187
    netmask 255.255.255.0
    broadcast 192.168.4.255
    gateway 192.168.4.1


With all the above when I do ipconfig /renew it times out.

---

### Post by KLStringer on 2010-04-29
> **DGortze380 said:**
> I think you'll need a valid IP on each VLAN. Remember VLANS break up broadcast domains, so a broadcast packet from 192.168.(3,5-8 ).x won't make it to the 192.168.4.x subnet.

It looks like there are some tricks you can play with Unicast to get around this ([http://tcpmag.com/qanda/article.asp?editorialsid=285](http://tcpmag.com/qanda/article.asp?editorialsid=285))...

But the simplest solution would be to set up multiple Virtual Interfaces on the DHCP Server (Virtual instead of Physical due to the large number of VLANS you want).


I have a 6024 layer 3 switch doing DHCP Relay for that.

---

### Post by KLStringer on 2010-04-30
I've done more troubleshooting and have found out that from the Ubuntu DHCP server I can't ping out to the 192.168.4.1 gateway, from a test PC I can ping to the 192.168.4.1 gateway so I'm thinking something on the server itself hasn't been correctly configured.

Currently I'm using both NIC cards eth0 is connected to vis dhcp to the 192.168.1.0 /24 network and eth1 is static at 192.18.1.187 on the 192.168.4.0 /24 and set to listen for dhcp requests. My next step is going to be disconnecting eth0 from the 192.168.1.0 /24  network and trying the set up again to see if I can ping out to the 192.168.4.1 gateway.

Onwards and upwards, there's no turning back now our destiny is to be completely windows free going into the new year. We have a deadline of September to have the backend up and working, as said any and all help is appreciated.

---

### Post by DGortze380 on 2010-04-30
> **KLStringer said:**
> Currently I'm using both NIC cards eth0 is connected to vis dhcp to the 192.168.1.0 /24 network and eth1 is static at 192.18.1.187 on the 192.168.4.0 /24 and set to listen for dhcp requests. My next step is going to be disconnecting eth0 from the 192.168.1.0 /24  network and trying the set up again to see if I can ping out to the 192.168.4.1 gateway.


You're doing some really weird things with subnets here dude.

post the output of 

```

netstat -rn

```

---

### Post by KLStringer on 2010-04-30
LOL just noticed there was a typo in the last post eth1 is static to 192.168.4.187 NOT 192.168.1.187, my mistake.

out put of netstat -rn is


```

Destination      Gateway       Genmask           Flags    MSS  Window   irtt   Iface
192.168.4.0     0.0.0.0        255.255.255.0       U      0      0      0       eth1
192.168.1.0     0.0.0.0        255.255.255.0       U      0      0      0       eth0
0.0.0.0         192.168.4.1   0.0.0.0              UG     0      0      0       eth1
0.0.0.0         192.168.1.1   0.0.0.0              UG     0      0      0       eth0
```

---

### Post by KLStringer on 2010-04-30
Update:

I've moved everything from eth1 to eth0 and changed dhcp to listen on eth0 for requests. From the server I still can't ping 192.168.4.1, from the host I can ping 192.168.4.1 but not the server at 192.168.4.187.

New netstat -rn looks like:

Dest GW Mask Flag MSS Window irtt Iface

192.168.4.0  0.0.0.0 255.255.255.0 U 0 0 0 eth0
0.0.0.0  192.168.4.1 0.0.0.0 UG 0 0 0 eth0

Is this right? To me it looks like a loop to get to the 192.168.4.0 /24 network its going to 192.168.4.1 via 0.0.0.0 which points it right back to the 192.168.4.0 /24 network.

---

### Post by DGortze380 on 2010-05-01
> **KLStringer said:**
> Update:

I've moved everything from eth1 to eth0 and changed dhcp to listen on eth0 for requests. From the server I still can't ping 192.168.4.1, from the host I can ping 192.168.4.1 but not the server at 192.168.4.187.

New netstat -rn looks like:

Dest GW Mask Flag MSS Window irtt Iface

192.168.4.0  0.0.0.0 255.255.255.0 U 0 0 0 eth0
0.0.0.0  192.168.4.1 0.0.0.0 UG 0 0 0 eth0

Is this right? To me it looks like a loop to get to the 192.168.4.0 /24 network its going to 192.168.4.1 via 0.0.0.0 which points it right back to the 192.168.4.0 /24 network.

That seems to be normal. Matches mine anyway.

---

### Post by KLStringer on 2010-05-03
Hmm well then there must be something else that's causing me to not be able to ping the GW or for a host to get an IP address from the server. The only thing that I can think that might be causing a problem is there are still 2 old DNS entries in the /etc/resolv.conf file but deleting or commenting them out didn't change anything.  I don't think that a lack of having a DNS server would prevent me from pinging by IP address since it's just the gateway. I've checked the cable just to be sure that wasn't the problem and it check's out fine. 

Something's keeping me from connecting to the network, don't know what it could be I've checked all the entries for setting up DHCP and as far as I can tell their correct. The port on the L3 switch responds to pings from other hosts just not from the server.

---

### Post by KLStringer on 2010-05-03
Read this thread

[http://ubuntuforums.org/showthread.php?t=358546](http://ubuntuforums.org/showthread.php?t=358546)

and followed it's suggestions and still can't ping gateway.

](*,)

---

### Post by KLStringer on 2010-05-03
ifconfig:
```

eth0

Link encap: Ethernet HWaddr 00:14:22:79:fc:ba
inet addr: 192.168.4.187 Bcast: 192.168.4.255 Mask: 255.255.255.0
inet6 addr: fe80::214:22ff:fe79:fcba/64 scope: Link
UP BROADCAST RUNNING MULITCAST MTU: 1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets: 194 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX butes:0 (0.0 B) TY bytes:12556 (12.5 KB)
```netstat -r
```

Kernel IP routing table
Destination Gateway Genmask Flags MMS Window irtt Iface
192.168.4.0 * 255.255.255.0 U 0 0 0 eth0
default 192.168.4.1 0.0.0.0 UG 0 0 0 eth0
```route -n

```
Kernel IP routing table
Destination Gateway Genmask Flags Metric Ref Use Iface
192.168.4.0 0.0.0.0 255.255.255.0 U 0 0 0 eth0
0.0.0.0 192.168.4.1 0.0.0.0 UG 100 0 0 eth0
```/etc/resolv.conf

```
domain cars.local
search cars.local
#nameserver 192.168.1.10
#nameserver 192.168.1.11
#####nameservers commented out no nameserver in test enviorment ######
```/etc/dhcp3/dhcpd.conf

```
ddns-update-style none;
default-lease-time 600;
max-lease-time 7200;
authoritative;
log-facility local7;

# VLAN 3 Test Config

subnet 192.168.3.0 netmask 255.255.255.0 {
range 192.168.3.2 192.168.3.254;
option routers 192.168.3.1;
option subnet-mask 255.255.255.0;
option broadcast-address 192.168.3.255;
}

# VLAN 4 Test Config

subnet 192.168.4.0 netmask 255.255.255.0 {
range 192.168.4.2 192.168.4.180;
option routers 192.168.4.1;
option subnet-mask 255.255.255.0;
option broadcast-address 192.168.4.255;
}

# VLAN 6 Test Config
subnet 192.168.6.0 netmask 255.255.255.0 {
range 192.168.6.2 192.168.6.254;
option routers 192.168.6.1;
option subnet-mask 255.255.255.0;
option broadcast-address 192.168.6.255;
}
```/etc/network/interfaces

```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static

address 192.168.4.187
netmask 255.255.255.0
network 192.168.4.0
broadcast 192.168.4.255
gateway 192.168.4.1

```/etc/default/dhcp3-server

```
INTERFACES="eth0"
```This server is connected to a Layer 3 switch as part of VLAN 4, VLAN 4 has IP 192.168.4.1 on the switch. There are 2 test PC's (one on VLAN 3, the other on VLAN 6) connected to a layer 2 switch that both can ping 192.168.4.1 but not this server at 192.168.4.187, the test PC's can also ping each other. The cable from this server to the switch has tested good. The port this server is connected to on the switch has been added to VLAN 4: 

```
enable
config
int eth g4
switchport mode access vlan 4
exit
copy run start
exit
```

The switches are a Dell Powerconnect 6024 (Layer 3) and 2 Dell Powerconnect 2824's (Layer 2).

If I've missed something let me know.

---

### Post by KLStringer on 2010-05-04
I ran tcpdump while I had a host request an IP address and I could see the DHCP request in the dump and then ARP requests for the servers IP address:

```
snip
00:21:47.215564 vlan 4, p 0, IP 192.168.6.1.bootpc > 192.168.4.187.bootps: BOOTP/DHCP, Request from 00:1a:a0:08:f9:0b (oui Unknown), length 300
00:21:47.215569 vlan 4, p 0, ARP, Request who-has 192.168.4.187 tell 192.168.4.1, length 46
00:21:48.216589 STP 802.1d, Config, Flags [none], bridge-id 8000.00:15:c5:d7:fa:c2.8004, length 43
snip

```This repeats for a few minutes then stops once the other PC stops asking and the
```

00:21:48.216589 STP 802.1d, Config, Flags [none], bridge-id  8000.00:15:c5:d7:fa:c2.8004, length 43
```part repeats till I stop the dump.

---

### Post by DGortze380 on 2010-05-04
Did you check any ACLs on the Layer 3 Switch?
Did you clear the ARP Table on the switch?

---

### Post by KLStringer on 2010-05-04
no ACLs are configured and ARP is clear, still no joy.
:confused:

---

### Post by KLStringer on 2010-05-05
Still looking....set up port mirroring and have wireshark running on my laptop but I don't see anything new that I wasn't seeing before.

---

### Post by KLStringer on 2010-05-06
](*,)](*,)](*,)](*,)

Someone out there has to know something, I've checked everything that I can think to check, I've updated everything and ran diagnostics for a week now and still can't get DHCP to respond or even to just be able to ping the gateway from the server.

Why doesn't the server respond to the ARP who has requests from the 6024?
Why can't the server ping the gateway or any other address?

This is driving me crazy not knowing Linux enough to figure it out on my own, Google can't help me I've read all its got to say.

---

### Post by bab1 on 2010-05-06
> **KLStringer said:**
> ...

Someone out there has to know something, I've checked everything that I can think to check, I've updated everything and ran diagnostics for a week now and still can't get DHCP to respond or even to just be able to ping the gateway from the server.

Why doesn't the server respond to the ARP who has requests from the 6024?
Why can't the server ping the gateway or any other address?

This is driving me crazy not knowing Linux enough to figure it out on my own, Google can't help me I've read all its got to say.

Sometimes I think we make things to complicated in the beginning.  My guess is you have a loop somewhere on one of your L2 switches and Spanning Tree Protocol (STP) is kicking in, shutting down a port (might be internal).

I assume this testbed can be reconstructed anyway you want.  I would suggest you revert all the ports in the L3 switch to VLAN1 and connect the host with the DHCP server to it along with 1 host that is dhcp client.  If that works out then you can add a 2nd. VLAN.  

It might help if we could see a diagram of what you have done.  A picture is a thousand words...

---

### Post by KLStringer on 2010-05-06
Everything works until I try to add in the DHCP server. If I statically assign IP address the 2 test PC can talk all day long. DHCP Relay is working I can see the packets come in with tcpdump, the server never responds to them or to the 6024's ARP who has requests. The server can only ping its IP or the loopback address so I know the interface is up. The DHCP server starts without any problems and I can restart the network interfaces without any problems.

I've attached a diagram of my layout, let me know if there's anything else I can provide.

---

### Post by bab1 on 2010-05-06
> **KLStringer said:**
> Everything works until I try to add in the DHCP server. If I statically assign IP address the 2 test PC can talk all day long. DHCP Relay is working I can see the packets come in with tcpdump, the server never responds to them or to the 6024's ARP who has requests. The server can only ping its IP or the loopback address so I know the interface is up. The DHCP server starts without any problems and I can restart the network interfaces without any problems.

I've attached a diagram of my layout, let me know if there's anything else I can provide.

Why would you be reluctant to start over with a very simple 1 network setup?  What you have isn't working at the present time.

I would create a LAN that does work with DHCP first and build on success.  As a side thought: Is the L2 switch managed?  Edit:  Just saw the trunked route.

---

### Post by KLStringer on 2010-05-06
I'm not against starting over with just a single VLAN, I was at home when I replied earlier and am just now getting to work. Also I think that the biggest problem with the current set-up not working is the fact that the server can't ping anything, even if I go to a 1 subnet set-up and still can't ping anything I'm no better off than I am right now. Another point is that if I add in a host thats on the same VLAN as the server even it can't get an IP address.

If the server was connecting and responding to the ARP who has requests and DHCP wasn't working that would be a different problem that could be solved by going to a single VLAN set-up. All of this leads me to believe that the problem lies in the fact that the server isn't completely connecting to the network for some reason.

That said it won't take me long to swap things around to VLAN 1 and try it to see if anything changes. I'll post back once I have everything set-up and have tested it.

---

### Post by KLStringer on 2010-05-06
Well its up and running, we have a couple consultants here working on other projects and one of them took a look at it and saw that the VLAN module was missing. :oops:#-oOnce we installed that, made a couple cfg changes, and rebooted everything fell into place.

\\:D/=D>

Once I have access to my desk I'll post the new config files so that if anyone else ever gets stuck maybe they'll find this thread and it'll help them.

---

### Post by bab1 on 2010-05-06
> **KLStringer said:**
> Well its up and running, we have a couple consultants here working on other projects and one of them took a look at it and saw that the VLAN module was missing. :oops:#-oOnce we installed that, made a couple cfg changes, and rebooted everything fell into place.

\\:D/=D>

Once I have access to my desk I'll post the new config files so that if anyone else ever gets stuck maybe they'll find this thread and it'll help them.

No bridge.  :-)    All L2 stuff.

---

### Post by KLStringer on 2010-05-06
Yep, the server, altho on the right subnet, didn't know it was on a vlan, once we fixed that everything worked. 

Now my next trick is to set-up a fail-over dhcp server :twisted:

---

### Post by KLStringer on 2010-05-17
Sorry took so long to get back to this thread its been busy around here the last week or so. 

Our whole problem all along was that the vlan module was never installed. Once we did "apt-get install vlan" and made the changes below to the configuration files everything worked perfectly. All the other configuration files posted in the thread stayed the same. 

/etc/network/interfaces
```
auto lo
iface lo inet loopback

auto vlan4
iface vlan4 inet static

address           192.168.4.187
netmask           255.255.255.0
network           192.168.4.0
broadcast         192.168.4.255
gateway           192.168.4.1
hostname          test_DHCP_Server
vlan_raw_device   eth0

```

and


/etc/default/dhcp3-server
```

INTERFACES="vlan4"
```

---

### Post by follencavale on 2013-01-29
**I managed to get 3 dhcp ranges based on 3 different vlans on a single NIC on my ubuntu 12.10. Hope it can help.**

[SIZE=2]**1. deactivate network-manager**[/SIZE]
```
$ sudo /etc/init.d/network-manager stop
```or
```
$ sudo update-rc.d -f network-manager remove
```[B]

2. install vlan[/B]
```
$ sudo apt-get install vlan 
$ sudo modprobe 8021q

```[B]
3. change the network config[/B]
```
$ sudo vim /etc/network/interfaces
```This is what my file looks like; you should change according to your needs
_tip:_ in my file, eth0.2 means using the vlan tag number 2 (so i.e. eth0.453 would mean using the vlan tag number 453)

```
auto lo
iface lo inet loopback

auto eth0.1
iface eth0.1 inet static
 address 10.0.1.254
 netmask 255.255.255.0

iface vlan1 inet static
 vlan-raw-device eth0
 address 10.0.1.254
 netmask 255.255.255.0

auto eth0.2
iface eth0.2 inet static
 address 10.0.2.254
 netmask 255.255.255.0

iface vlan2 inet static
 vlan-raw-device eth0
 address 10.0.2.254
 netmask 255.255.255.0

auto eth0.3
iface eth0.3 inet static
 address 10.0.3.254
 netmask 255.255.255.0

iface vlan3 inet static
 vlan-raw-device eth0
 address 10.0.3.254
 netmask 255.255.255.0

```[B]

4. reload this new network configuration and check it[/B]
```
$ sudo /etc/init.d/networking restart
[I]* Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...                                                                                                           
RTNETLINK answers: No such process

ssh stop/waiting
ssh start/running, process 3759
Set name-type for VLAN subsystem. Should be visible in /proc/net/vlan/config
Added VLAN with VID == 1 to IF -:eth0:-
WARNING:  VLAN 1 does not work with many switches,
consider another number if you have problems.
ssh stop/waiting

ssh start/running, process 4002[/I]

``````
$ sudo cat /proc/net/vlan/config
[I]VLAN Dev name     | VLAN ID
Name-Type: VLAN_NAME_TYPE_RAW_PLUS_VID_NO_PAD
eth0.1         | 1  | eth0
eth0.2         | 2  | eth0
eth0.3         | 3  | eth0[/I]

``````
$ ifconfig
[I]eth0.1    Link encap:Ethernet  HWaddr 54:04:a6:25:24:9f  
          inet adr:10.0.1.254  Bcast:10.0.1.255  Masque:255.255.255.0
          adr inet6: fe80::5604:a6ff:fe25:249f/64 Scope:Lien
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Packets reçus:0 erreurs:0 :0 overruns:0 frame:0
          TX packets:53 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:0 
          Octets reçus:0 (0.0 B) Octets transmis:7620 (7.6 KB)

eth0.2    Link encap:Ethernet  HWaddr 54:04:a6:25:24:9f  
          inet adr:10.0.2.254  Bcast:10.0.2.255  Masque:255.255.255.0
          adr inet6: fe80::5604:a6ff:fe25:249f/64 Scope:Lien
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Packets reçus:4156 erreurs:0 :0 overruns:0 frame:0
          TX packets:977 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:0 
          Octets reçus:220624 (220.6 KB) Octets transmis:103336 (103.3 KB)

eth0.3    Link encap:Ethernet  HWaddr 54:04:a6:25:24:9f  
          inet adr:10.0.3.254  Bcast:10.0.3.255  Masque:255.255.255.0
          adr inet6: fe80::5604:a6ff:fe25:249f/64 Scope:Lien
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Packets reçus:9521 erreurs:0 :0 overruns:0 frame:0
          TX packets:418 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:0 
          Octets reçus:480001 (480.0 KB) Octets transmis:43522 (43.5 KB)[/I]

```[B]

5. change dhcp server config[/B]
```
$ sudo vim /etc/dhcp/dhcpd.conf
```This is what my file looks like; you should change according to your needs
```
ddns-update-style none;
option domain-name "hello.lan";
option domain-name-servers 10.0.0.254;
option domain-name-servers 8.8.8.8;
default-lease-time 600;
max-lease-time 7200;
authoritative;
log-facility local7;
subnet 10.0.1.0 netmask 255.255.255.0 {
  range 10.0.1.20 10.0.1.30;
  option routers 10.0.1.254;
}
subnet 10.0.2.0 netmask 255.255.255.0 {
  range 10.0.2.20 10.0.2.30;
  option routers 10.0.2.254;
}
subnet 10.0.3.0 netmask 255.255.255.0 {
  range 10.0.3.20 10.0.3.30;
  option routers 10.0.3.254;
}
host static-machine-vlan1{
  hardware ethernet 90:94:e4:f7:c3:f3;
  fixed-address 10.0.1.11;
}
```finally restart the dhcp server
```
$ sudo /etc/init.d/isc-dhcp-server restart
```**It works great with my Netgear Prosafe switch GS108E.**

---

### Post by ataylor1988 on 2013-05-08
> **follencavale said:**
> **I managed to get 3 dhcp ranges based on 3 different vlans on a single NIC on my ubuntu 12.10. Hope it can help.**

[SIZE=2]**1. deactivate network-manager**[/SIZE]
```
$ sudo /etc/init.d/network-manager stop
```or
```
$ sudo update-rc.d -f network-manager remove
```[B]

2. install vlan[/B]
```
$ sudo apt-get install vlan 
$ sudo modprobe 8021q

```[B]
3. change the network config[/B]
```
$ sudo vim /etc/network/interfaces
```This is what my file looks like; you should change according to your needs
_tip:_ in my file, eth0.2 means using the vlan tag number 2 (so i.e. eth0.453 would mean using the vlan tag number 453)

```
auto lo
iface lo inet loopback

auto eth0.1
iface eth0.1 inet static
 address 10.0.1.254
 netmask 255.255.255.0

iface vlan1 inet static
 vlan-raw-device eth0
 address 10.0.1.254
 netmask 255.255.255.0

auto eth0.2
iface eth0.2 inet static
 address 10.0.2.254
 netmask 255.255.255.0

iface vlan2 inet static
 vlan-raw-device eth0
 address 10.0.2.254
 netmask 255.255.255.0

auto eth0.3
iface eth0.3 inet static
 address 10.0.3.254
 netmask 255.255.255.0

iface vlan3 inet static
 vlan-raw-device eth0
 address 10.0.3.254
 netmask 255.255.255.0

```[B]

4. reload this new network configuration and check it[/B]
```
$ sudo /etc/init.d/networking restart
[I]* Running /etc/init.d/networking restart is deprecated because it may not enable again some interfaces
 * Reconfiguring network interfaces...                                                                                                           
RTNETLINK answers: No such process

ssh stop/waiting
ssh start/running, process 3759
Set name-type for VLAN subsystem. Should be visible in /proc/net/vlan/config
Added VLAN with VID == 1 to IF -:eth0:-
WARNING:  VLAN 1 does not work with many switches,
consider another number if you have problems.
ssh stop/waiting

ssh start/running, process 4002[/I]

``````
$ sudo cat /proc/net/vlan/config
[I]VLAN Dev name     | VLAN ID
Name-Type: VLAN_NAME_TYPE_RAW_PLUS_VID_NO_PAD
eth0.1         | 1  | eth0
eth0.2         | 2  | eth0
eth0.3         | 3  | eth0[/I]

``````
$ ifconfig
[I]eth0.1    Link encap:Ethernet  HWaddr 54:04:a6:25:24:9f  
          inet adr:10.0.1.254  Bcast:10.0.1.255  Masque:255.255.255.0
          adr inet6: fe80::5604:a6ff:fe25:249f/64 Scope:Lien
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Packets reçus:0 erreurs:0 :0 overruns:0 frame:0
          TX packets:53 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:0 
          Octets reçus:0 (0.0 B) Octets transmis:7620 (7.6 KB)

eth0.2    Link encap:Ethernet  HWaddr 54:04:a6:25:24:9f  
          inet adr:10.0.2.254  Bcast:10.0.2.255  Masque:255.255.255.0
          adr inet6: fe80::5604:a6ff:fe25:249f/64 Scope:Lien
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Packets reçus:4156 erreurs:0 :0 overruns:0 frame:0
          TX packets:977 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:0 
          Octets reçus:220624 (220.6 KB) Octets transmis:103336 (103.3 KB)

eth0.3    Link encap:Ethernet  HWaddr 54:04:a6:25:24:9f  
          inet adr:10.0.3.254  Bcast:10.0.3.255  Masque:255.255.255.0
          adr inet6: fe80::5604:a6ff:fe25:249f/64 Scope:Lien
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Packets reçus:9521 erreurs:0 :0 overruns:0 frame:0
          TX packets:418 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:0 
          Octets reçus:480001 (480.0 KB) Octets transmis:43522 (43.5 KB)[/I]

```[B]

5. change dhcp server config[/B]
```
$ sudo vim /etc/dhcp/dhcpd.conf
```This is what my file looks like; you should change according to your needs
```
ddns-update-style none;
option domain-name "hello.lan";
option domain-name-servers 10.0.0.254;
option domain-name-servers 8.8.8.8;
default-lease-time 600;
max-lease-time 7200;
authoritative;
log-facility local7;
subnet 10.0.1.0 netmask 255.255.255.0 {
  range 10.0.1.20 10.0.1.30;
  option routers 10.0.1.254;
}
subnet 10.0.2.0 netmask 255.255.255.0 {
  range 10.0.2.20 10.0.2.30;
  option routers 10.0.2.254;
}
subnet 10.0.3.0 netmask 255.255.255.0 {
  range 10.0.3.20 10.0.3.30;
  option routers 10.0.3.254;
}
host static-machine-vlan1{
  hardware ethernet 90:94:e4:f7:c3:f3;
  fixed-address 10.0.1.11;
}
```finally restart the dhcp server
```
$ sudo /etc/init.d/isc-dhcp-server restart
```**It works great with my Netgear Prosafe switch GS108E.**


So i have copied this almos exactly except i have setup vlans 2-12
It seems to setup correctly.  i connect the linux machine to the trunk port for those vlans on the layer 3 switch and i can watch the vlan interfaces come up on the router.
however i cannot communicate to the linux box or vise versa.  I cannot ping so on and so forth.

So i tried just setting up eth0 with no vlan and i could then ping the box from the router.   Any ideas?
once i get basic communication working i will start to takle the DHCP server but need to get basic stuff working first

---

