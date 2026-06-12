---
title: "Marvell 88e8055, auto-ip not working"
date: 2009-05-21
forum: Networking &amp; Wireless
---

### Post by jeongjaelee on 2009-05-21
Hello. I am using Samsung laptop R410-FA180 with Marvell 88e8055 LAN card installed.

I recently installed Ubuntu 9.04 Jaunty Jackalope on my laptop and the problem is, the lancard does not get ip automatically from DHCP.

I am living in a dorm where each outlet has pre-designated ip and the internet works fine there, but in my home my linux cannot automatically get an ip.

I confirmed this by first logging on win xp(I have dual-boot system) and note the settings there and applying the same settings to ubnutu network manager. Then the internet works fine.

Is there a way to fix my internet?

---

### Post by superprash2003 on 2009-05-21
in your terminal type **sudo dhclient eth0** ( where eth0 is the LAN interface ) and post output

---

### Post by jeongjaelee on 2009-05-22
Here are my outputs:

1. Dhclient
```

Listening on LPF/eth0/00:13:77:9f:f2:f3
Sending on   LPF/eth0/00:13:77:9f:f2:f3
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14

```

(Note that I typed "dhclient" instead of "dhclient -eth0" and pasted only relevant eth0 outputs)

2. netstat -r
```

Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
link-local      *               255.255.0.0     U         0 0          0 wlan0
link-local      *               255.255.0.0     U         0 0          0 pan0
link-local      *               255.255.0.0     U         0 0          0 eth0
default         *               0.0.0.0         U         0 0          0 wlan0

```

3. ethtools -eth0
```

Settings for eth0:
    Supported ports: [ TP ]
    Supported link modes:   10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Half 1000baseT/Full 
    Supports auto-negotiation: Yes
    Advertised link modes:  10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Half 1000baseT/Full 
    Advertised auto-negotiation: Yes
    Speed: 100Mb/s
    Duplex: Full
    Port: Twisted Pair
    PHYAD: 0
    Transceiver: internal
    Auto-negotiation: on
    Supports Wake-on: pg
    Wake-on: d
    Current message level: 0x000000ff (255)
    Link detected: yes

```

4. ifconfig -eth0
```

eth0      Link encap:Ethernet  HWaddr 00:13:77:9f:f2:f3  
          inet6 addr: fe80::213:77ff:fe9f:f2f3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3154 errors:0 dropped:0 overruns:0 frame:0
          TX packets:43 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:145084 (145.0 KB)  TX bytes:10813 (10.8 KB)
          Interrupt:16 

eth0:avahi Link encap:Ethernet  HWaddr 00:13:77:9f:f2:f3  
          inet addr:169.254.11.102  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:16

```

Thank you in advance.

---

### Post by superprash2003 on 2009-05-22
post contents of /etc/dhcp3/dhclient.conf

---

### Post by jeongjaelee on 2009-05-26
```

# Configuration file for /sbin/dhclient, which is included in Debian's
#    dhcp3-client package.
#
# This is a sample configuration file for dhclient. See dhclient.conf's
#    man page for more information about the syntax of this file
#    and a more comprehensive list of the parameters understood by
#    dhclient.
#
# Normally, if the DHCP server provides reasonable information and does
#    not leave anything out (like the domain name, for example), then
#    few changes must be made to this file, if any.
#

option rfc3442-classless-static-routes code 121 = array of unsigned integer 8;

send host-name "<hostname>";
#send dhcp-client-identifier 1:0:a0:24:ab:fb:9c;
#send dhcp-lease-time 3600;
#supersede domain-name "fugue.com home.vix.com";
#prepend domain-name-servers 127.0.0.1;
request subnet-mask, broadcast-address, time-offset, routers,
    domain-name, domain-name-servers, domain-search, host-name,
    netbios-name-servers, netbios-scope, interface-mtu,
    rfc3442-classless-static-routes, ntp-servers;
#require subnet-mask, domain-name-servers;
#timeout 60;
#retry 60;
#reboot 10;
#select-timeout 5;
#initial-interval 2;
#script "/etc/dhcp3/dhclient-script";
#media "-link0 -link1 -link2", "link0 link1";
#reject 192.33.137.209;

#alias {
#  interface "eth0";
#  fixed-address 192.5.5.213;
#  option subnet-mask 255.255.255.255;
#}

#lease {
#  interface "eth0";
#  fixed-address 192.33.137.200;
#  medium "link0 link1";
#  option host-name "andare.swiftmedia.com";
#  option subnet-mask 255.255.255.0;
#  option broadcast-address 192.33.137.255;
#  option routers 192.33.137.250;
#  option domain-name-servers 127.0.0.1;
#  renew 2 2000/1/12 00:00:01;
#  rebind 2 2000/1/12 00:00:01;
#  expire 2 2000/1/12 00:00:01;
#}

```

---

### Post by superprash2003 on 2009-05-26
try this [http://www.prash-babu.com/2009/05/how-to-fix-ip-by-dhcp-issue-in-ubuntu.html](http://www.prash-babu.com/2009/05/how-to-fix-ip-by-dhcp-issue-in-ubuntu.html)

---

### Post by jeongjaelee on 2009-05-26
Thanks for your suggestion, superprash2003, but the wired internet is still not working.
 
I deleted all connections from the network manager and re-configured the whole thing, but the net still not works....

---

### Post by jeongjaelee on 2009-05-30
bump

can anyone help?

---

