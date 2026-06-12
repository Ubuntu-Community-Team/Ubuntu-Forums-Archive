---
title: "can't access to eth0"
date: 2011-02-04
forum: Networking &amp; Wireless
---

### Post by phoenixpb on 2011-02-04
this is my config etc/network/interfaces

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp

auto wlan0
iface wlan0 inet manual
        pre-up iw dev wlan0 set type __ap
        hostapd /etc/hostapd/hostapd.conf

auto br0
iface br0 inet static
        address 192.168.0.1
        network 192.168.0.0
        netmask 255.255.255.0
        broadcast 192.168.0.255
        bridge_ports wlan0 eth0
        bridge_fd 0

the problem is the client which access through hostapd can connect to internet but the server no (eth0 is the interface connected to internet) :lolflag:
i'm surely missing something 
thanks

---

### Post by dmizer on 2011-02-04
Can you post the output of:
```
ifconfig
```

---

### Post by phoenixpb on 2011-02-04
ifconfig
br0       Link encap:Ethernet  HWaddr 00:11:d8:bc:58:8f  
          inet addr:192.168.0.111  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::211:d8ff:febc:588f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:55 errors:0 dropped:0 overruns:0 frame:0
          TX packets:29 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:3414 (3.4 KB)  TX bytes:5852 (5.8 KB)

eth0      Link encap:Ethernet  HWaddr 00:11:d8:bc:58:8f  
          inet addr:192.168.0.11  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::211:d8ff:febc:588f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:69 errors:0 dropped:0 overruns:0 frame:0
          TX packets:88 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5588 (5.5 KB)  TX bytes:10445 (10.4 KB)
          Interrupt:19 Base address:0xc800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:52 errors:0 dropped:0 overruns:0 frame:0
          TX packets:52 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4209 (4.2 KB)  TX bytes:4209 (4.2 KB)


infact what i want is :

android phone <---> wlan0 (hostapd) <---> PC <---> eth0 <--->      rooter    (192.168.0.1) <---> internet

---

### Post by dmizer on 2011-02-04
The br0 needs to be on a different subnet than the router connected on eth0.

Rather than configuring br0 for 192.168.0.x, you should configure it for something completely different ... like 10.0.0.x

Why not just configure yoru wireless card for internet sharing via network-manager rather than trying to set up a bridge manually via interfaces? That way you don't have to worry about configuring things on the same subnet, and you'll also get all the correct IPtables settings for IP forewarding.

---

### Post by phoenixpb on 2011-02-04
> **dmizer said:**
> The br0 needs to be on a different subnet than the router connected on eth0.

Rather than configuring br0 for 192.168.0.x, you should configure it for something completely different ... like 10.0.0.x

Why not just configure yoru wireless card for internet sharing via network-manager rather than trying to set up a bridge manually via interfaces? That way you don't have to worry about configuring things on the same subnet, and you'll also get all the correct IPtables settings for IP forewarding.

thanks for your help
because i need a hot-spot not a ad-hoc network :) we need to wait to nm 0.9 to do this

---

### Post by phoenixpb on 2011-02-04
my new configs

interfaces

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto wlan0
iface wlan0 inet manual

auto br0
iface br0 inet static
        address 10.0.0.1
        network 10.0.0.0
        netmask 255.0.0.0
        broadcast 10.255.255.255
        bridge-ports eth0 wlan0
post-up /etc/init.d/dhcp3-server start
post-up /etc/init.d/linux-igd start
post-up /etc/init.d/hostapd restart
post-up /usr/sbin/brctl addif br0 wlan0

/etc/default/dhcp3-server
INTERFACES="eth0"

/etc/dhcp3/dhcpd.conf
default-lease-time 600;
max-lease-time 7200;
option subnet-mask 255.255.255.0;
option broadcast-address 192.168.0.255;
option routers 192.168.0.254;
option domain-name-servers 192.168.0.1;
option domain-name "mydomain.example";

subnet 192.168.0.0 netmask 255.255.255.0 {
range 192.168.0.10 192.168.0.100;
range 192.168.0.150 192.168.0.200;
} 

what is wrong ? :lolflag:

---

### Post by phoenixpb on 2011-02-04
another brick for my problem 

phoenix@styx:~$ cat /var/log/syslog | tail
Feb  4 15:20:58 styx NetworkManager[929]:    SCPlugin-Ifupdown: device added (path: /sys/devices/pci0000:00/0000:00:0a.0/net/mon.wlan0, iface: mon.wlan0): no ifupdown configuration found.
Feb  4 15:21:00 styx avahi-daemon[930]: Joining mDNS multicast group on interface wlan0.IPv6 with address fe80::5ed9:98ff:fec3:bfc1.
Feb  4 15:21:00 styx avahi-daemon[930]: New relevant interface wlan0.IPv6 for mDNS.
Feb  4 15:21:00 styx avahi-daemon[930]: Registering new address record for fe80::5ed9:98ff:fec3:bfc1 on wlan0.*.
Feb  4 15:21:02 styx hostapd: wlan0: STA 00:26:37:e0:60:e6 IEEE 802.11: authenticated
Feb  4 15:21:02 styx hostapd: wlan0: STA 00:26:37:e0:60:e6 IEEE 802.11: associated (aid 1)
Feb  4 15:21:02 styx hostapd: wlan0: STA 00:26:37:e0:60:e6 RADIUS: starting accounting session 4D4C0B4A-00000000
Feb  4 15:21:02 styx hostapd: wlan0: STA 00:26:37:e0:60:e6 WPA: pairwise key handshake completed (RSN)
Feb  4 15:21:09 styx kernel: [   62.536018] [COLOR=Red]wlan0: no IPv6 routers present[/COLOR]
Feb  4 15:21:33 styx hostapd: wlan0: STA 00:26:37:e0:60:e6 IEEE 802.11: disassociated

---

