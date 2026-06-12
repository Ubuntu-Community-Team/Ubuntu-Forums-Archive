---
title: "dhcp3-server nightmare"
date: 2009-12-19
forum: Networking &amp; Wireless
---

### Post by MisplacedNeurons on 2009-12-19
This is my first post, so please treat with care.  I've spent quite a few hours with this issue, to no avail.  I am attempting to use DHCP for an internal network while also serving an external site on the same server with two network interface cards.  Here are the details:

My topology is cable modem --> eth1 of Ubuntu server, eth0 --> LAN

Both NICs are fully functional.

Contents of /etc/network/interfaces

```
auto lo
iface lo inet loopback

mapping hotplug
    script grep
    map eth1

auto eth1
iface eth1 inet dhcp

auto eth0
iface eth0 inet static
address 10.152.187.1
netmask 255.255.255.0
```Results of ifcponfig:
```

eth0      Link encap:Ethernet  HWaddr 00:07:e9:24:16:bc  
          inet addr:10.152.187.1  Bcast:10.152.187.255  Mask:255.255.255.0
          inet6 addr: fe80::207:e9ff:fe24:16bc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:25 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:0 (0.0 B)  TX bytes:3669 (3.6 KB)

eth1      Link encap:Ethernet  HWaddr 00:07:e9:24:16:bd  
          inet addr:xx.xxx.xx.xxx  Bcast:255.255.255.255  Mask:255.255.240.0
          inet6 addr: fe80::207:e9ff:fe24:16bd/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3959 errors:0 dropped:0 overruns:0 frame:0
          TX packets:57 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:241045 (241.0 KB)  TX bytes:6883 (6.8 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)
```The x's on eth1 are my edits of a functioning IP served by my ISP.

Contents of /etc/default/dhcp3-server

```
INTERFACES="eth0"
```Contents of /etc/dhcp3/dhcpd.conf

```
ddns-update-style none;

authoritative;

log-facility local7;

subnet 192.168.1.0 netmask 255.255.255.0 {

        option routers                  192.168.1.1;
        option subnet-mask              255.255.255.0;
        option broadcast-address        192.168.1.255;
        option domain-name-servers      24.93.41.127, 24.93.41.128;
        option ntp-servers              192.168.1.1;
        option netbios-name-servers     192.168.1.1;
        option netbios-node-type 2;
        default-lease-time 86400;
        max-lease-time 86400;
}

subnet  10.152.187.0 netmask 255.255.255.0 {

        option routers                  10.152.187.1;
        option broadcast-address        10.152.187.255;
          range 10.152.187.10 10.152.187.50;
    
        default-lease-time 86400;
        max-lease-time 86400;
}
```Output of route -n

```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.152.187.0    0.0.0.0         255.255.255.0   U     0      0        0 eth0
xx.xx.x0.0     0.0.0.0         255.255.240.0   U     0      0        0 eth1
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         72.177.80.1     0.0.0.0         UG    100    0        0 eth1
```Again, I've anonymized the eth1 Destination.

I've restarted /etc/init.d/networking and /etc/init.d/dhcp3-server each time I've reconfigured, and rebooted the server countless times.  My LAN PCs are receiving IP correctly, but cannot get out to the internet.  When running nslookup for ubuntuforums.org on a client, the error message is ```
;; connection timed out; no servers could be reached
```I've reconfigured everything by swapping NICs in the topology with no luck.  I am unsure why 169.254.0.0 shows as a destination for eth0.  Perhaps this is the issue?

Please, can someone be of assistance?  I've read posts, the man page, and HOW-TOs (the savvy reader will identify a nearly identical configuration to the help.ubuntu.com guide, with the exception that I've included a range in the subnet for the LAN.  I don't know how the configuration would work without it.)

Eagerly anticipating a solution...

---

### Post by Iowan on 2009-12-19
Did you intend to anonymize the eth1 gateway as well? Have you set up DNS servers (addresses) to be passed to the clients? You might check a client (*/etc/resolv.conf* on Linux/Ubuntu machine) to see what they're using.

---

### Post by MisplacedNeurons on 2009-12-19
Iowan,

Thank you for the quick reply.  I was not as concerned about anonymizing my ISPs DNS servers, as they are public.

I've added ```
option domain-name-servers    10.152.187.254;
``` in my dhcpd.conf file in the appropriate subnet section.  After restarting the service, a client's /etc/resolv.conf output is as follows:

```
# Generated by NetworkManager
nameserver 10.152.187.254
```Adding my ISP's DNS addresses to dhcpd.conf and restarting gives the following on a client resolv.conf output:

```
nameserver 10.152.187.254
nameserver 24.93.41.127
nameserver 24.93.41.128
```but still no internet for the LAN.  Am I missing something?  Do I have to set up a DNS server within the subnet separate from any of the dhcp3-server configuration files?

---

### Post by Iowan on 2009-12-20
Can you **ping** internet via name (google.com) or IP address (209.85.225.147)?

---

### Post by MisplacedNeurons on 2009-12-20
No, I cannot ping from any client within the LAN.  The server can access the internet through it's direct connection in eth1 to the router.  Any client can ping the (externally) assigned IP to eth1 and the internally assinged IP to eth0, but cannot ping beyond the server.  When I attempt to ping a client from the server, it attempts to resolve the IP externally (which makes sense, because it's on a separate subnet).

---

### Post by Iowan on 2009-12-20
[Here ]("https://help.ubuntu.com/community/Internet/ConnectionSharing") is a help page for ICS. It kinda sounds like DHCP is working, but server isn't "forwarding" to internet.

---

### Post by MisplacedNeurons on 2009-12-20
Thanks for the link.  Not sure that internet connection sharing is the solution I'm seeking, but thanks for the efforts.  At this point, I think I'm simply going to reinstall the OS, perhaps a different distribution, and hope for the best.

---

