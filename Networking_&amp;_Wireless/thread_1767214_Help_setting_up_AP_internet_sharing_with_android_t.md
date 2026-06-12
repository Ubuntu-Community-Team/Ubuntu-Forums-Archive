---
title: "Help setting up AP internet sharing with android teathered internet"
date: 2011-05-25
forum: Networking &amp; Wireless
---

### Post by domtron on 2011-05-25
Hello, I'm trying to set up a wireless AP with Internet sharing. I  currently have the AP setup with hostapd and a dhcp server. The clients  can connect but there is not Internet sharing. Now my situation is  somewhat uniqe in that my internet connection is my teathered android  cell phone. The tether app is azilink and i use openvpn to create a  virtual networking interface(tun0).

I'm on Ubuntu 10.04(lucid)
Kernal Linux 2.6.32-31
my wireless adapter is a ASUS WL-167G
   >54 Mbps standered 802.11g
   >USB 2.0

my wirless device is wlan1
my internet comes through tun0

ifconfig gives me
```

tun0      Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  
          inet addr:192.168.56.2  P-t-P:192.168.56.1  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:10692 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11149 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:5519679 (5.5 MB)  TX bytes:1101763 (1.1 MB)

wlan1     Link encap:Ethernet  HWaddr 00:24:8c:a4:ae:1b  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


```(i left out the eth0 and lo)

in /etc/network/interfaces i have
```

auto lo wlan1
iface wlan1 inet dhcp
iface lo inet loopback

```in /etc/dhcp3/dhcpd.conf
```

default-lease-time 600;
max-lease-time 7200;

option subnet-mask 255.255.255.0;
option broadcast-address 192.168.1.255;
option routers 192.168.1.254;
option domain-name-servers 192.168.1.1, 192.168.1.2;
#option domain-name “yourdomainname.com”;

subnet 192.168.1.0 netmask 255.255.255.0 {
option ip-forwarding on;
range 192.168.1.10 192.168.1.200;
}

```for teathering my openvpn.conf is
```

dev tun

remote 127.0.0.1 41927 tcp-client
proto tcp-client
ifconfig 192.168.56.2 192.168.56.1
route 0.0.0.0 128.0.0.0
route 128.0.0.0 128.0.0.0
keepalive 10 30
dhcp-option DNS 192.168.56.1

```and  if anyone is familer with google android's adb driver: would it be  possible to use adb forward to pass connected clients to the Internet?

I think thats every thing...

Thanks for any help you can give

---

### Post by domtron on 2011-05-25
bump

---

### Post by Wolf9466 on 2011-05-25
You'll probably need iptables, and you'll also need the wireless interface to support master mode, unless you want it ad-hoc. Check for iptables, and try 'iwconfig wlan1 mode master'.

---

### Post by domtron on 2011-05-26
I have the ap setup, the wireless adapter is in master mode thanks to hostapd. However clients that connect don't get Internet. I just need something to bride data from the wlan and the tun0 virtual devices. I tried brctl but it says tun0 can't be added to the bridge i made.

domtron@domtron-desktop:~$ sudo brctl addbr br0
domtron@domtron-desktop:~$ sudo brctl addif br0 tun0
can't add tun0 to bridge br0: Invalid argument

---

### Post by Wolf9466 on 2011-05-26
Try using iptables to redirect traffic?

---

