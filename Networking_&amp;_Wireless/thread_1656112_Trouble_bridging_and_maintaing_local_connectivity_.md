---
title: "Trouble bridging and maintaing local connectivity 10.04"
date: 2010-12-30
forum: Networking &amp; Wireless
---

### Post by TimLockwood123 on 2010-12-30
Hi my name is Tim, I have an Ubuntu Lucid 10.04 box running kernel 2.6.32-27-generic and I am trying to set it up as a wireless access point. I've had trouble bridging my wlan0 interface and my LAN network interface eth0 (which is also the interface through which I receive internet), please help me!

I am using hostapd to set my wlan nic up as an access point which appears to be working successfully, I can associate with the access point but currently cannot obtain an ip address. I believe this is because dhcp3-server cannot bind to br0, and I am having trouble setting up br0.

When I set up br0 I lose internet connectivity on the box through eth0, which I believe is because eth0 successfully bridges to wlan0 and as a side effect I lose local connectivity. I am using the following commands to create the bridge:

```

brctl addbr br0
sudo brctl addbr br0
brctl addif br0 eth0 wlan0
sudo brctl addif br0 eth0 wlan0

```  

I appreciate this is not persistent but until the bridge is working as desired I cannot put this into my interfaces file. Please can someone provide some direction as to how I can maintain local connectivity on the box with a bridge in place? Is this possible?

My LAN dhcp is provided by a separate router and this assigns the ip address to the ubuntu box's eth0 interface. The router ip is 192.168.0.1, the LAN is 192.168.0.0. I was intending to then use the ubuntu box to assign ip's on the wlan interface, using the ubuntu box as a dhcp server purely for the wlan as I am unable to figure out how to pass through dhcp from my LAN's router to wireless clients.

I will post up my hostapd.conf and dhcpd.conf as it may be of some help.

```

dhcpd.conf
default-lease-time            600;
max-lease-time                7200;

subnet 192.168.0.0 netmask 255.255.255.0 {
    range 192.168.0.102 192.168.0.150;
    option subnet-mask            255.255.255.0;
    option broadcast-address      192.168.0.255;
    option routers                192.168.0.1;
    }

```

```

hostapd.conf
interface=wlan0
driver=nl80211
ssid=APRIL2
channel=1
hw_mode=g

```

Thanks for any help, I've spent many hours searching and trying to sort it out.:confused:

---

### Post by spiky001 on 2010-12-30
Have you looked at adhoc?

---

### Post by TimLockwood123 on 2010-12-30
We need more than adhoc as there are multiple clients.
Thanks.

---

