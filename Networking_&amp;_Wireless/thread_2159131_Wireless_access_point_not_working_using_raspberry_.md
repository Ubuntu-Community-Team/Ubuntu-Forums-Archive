---
title: "Wireless access point not working using raspberry PI"
date: 2013-07-01
forum: Networking &amp; Wireless
---

### Post by Heeter on 2013-07-01
Hi all,

Undertaking a small project here, I am creating an wifi access point using a raspberry PI, I have hit a small snag. I reset my router to basic 192.168.1.1 for simplicity sake as I learn my way around.

I cannot ping/ssh from my Ubuntu linux desktop to the PI, also cannot ping 'www.google.com" from the raspPI itself. I can ping 8.8.8.8 from the raspPI itself!

My router address: 192.168.1.1
My router dhcp server: 192.168.1.100-150
My PI eth0 address: 192.168.1.128
My PI wlan0 address; 192.168.1.129

Through my raspPI, I can ifconfig -a these ip addresses for the PI. I set it up in hostapd and the dhcpd files. The PI is serving dhcp range of: 192.168.1.151-160.

I can connect to the PI access point with my wireless device, but cannot get on the internet.

These are the configurations that I entered in the dhcpd.conf file on the raspPI:

```

subnet 192.168.1.0 netmask 255.255.255.0 {
range 192.168.1.151 192.168.1.160;
option broadcast-address 192.168.1.255;
option routers 192.168.1.1;
default-lease-time 600;
max-lease-time 7200;
option domain-name "local";
option domain-name-servers 8.8.8.8, 8.8.4.4;
}

```

And this is the result when I run "sudo netstat -rn"

```

Kernel IP routing table
Destination    Gateway           Genmask           Flags    MSS Window   irtt  Iface
0.0.0.0          192.168.1.1      0.0.0.0             UG        0 0                   0  eth0
192.168.1.0    0.0.0.0             255.255.255.0   U          0 0                   0 wlan0
192.168.1.0    0.0.0.0             255.255.255.0   U          0 0                   0 eth0

```

can't quite figure this one out.

I can use a wireless device and pickup/authenticate onto the raspPI, but once connected cannot get onto the internet through the PI.

I cannot ssh into either the eth0 or the wlan0 on the PI from my Ubuntu desktop

Heeter

---

### Post by Heeter on 2013-07-03
any and all help will be greatly appreciated.

---

