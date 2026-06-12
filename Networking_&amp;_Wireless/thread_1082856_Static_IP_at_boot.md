---
title: "Static IP at boot"
date: 2009-02-28
forum: Networking &amp; Wireless
---

### Post by Nirva on 2009-02-28
Hi,

I'm trying to install a Xubuntu server, and therefor I want the wireless network interface to have a static IP-address.
But whenever the server boots, the IP is something different (always the same, but thats probably coincidence)from the one I set in /etc/network/interfaces

So I do 

```
sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...
RNETLINK answers: no such process
SIOCADDRT: No such process
```

The second time I run ```
sudo /etc/init.d/networking restart
``` everything goes fine and ifconfig tells me I have the right IP-assigned, but iwconfig tells me that I'm not even connected ( which is true ).

/etc/network/interfaces looks like this:

```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet static
address 192.168.2.250
wireless-essid myEssid
wireless-key myKey
netmask 255.255.255.0
network 192.168.2.0
broadcast 192.168.2.255
gateway 192.168.2.1


```

Could someone please help me ?

---

### Post by Nirva on 2009-02-28
Update :

After googling some more, I found that this is caused by an error of "Network Manager".
So I removed "Network Manager", as is proposed in some threads, but this still doesn't solve my problem.

Anyone else ?

---

### Post by chili555 on 2009-02-28
> I removed Network ManagerDid you also remove its little buddy *dhcpcd*?

Please do:```
sudo ifdown wlan0 && sudo ifup wlan0
```Then follow up with:```
ifconfig
ping -c3 192.168.2.1
```Let us know the result.

---

### Post by Nirva on 2009-03-01
Hi,

Thanks for helping me.

I removed Network Manager, as some people suggested, but I didn't remove anything like dhcpcd.

When I let the terminal autocomplete 

```
filip@xubuntu-server:~$ sudo apt-get remove dhc
dhcp3-client  dhcp3-common 
``` 

dhcpcd isn't in the list, so I don't have to uninstall it ?

Now that Network Manager is uninstalled, I don't get any IP at all anymore at boot.

These are the responses from the commands you asked me.
( I added -I wlan0 to the ping command, because I plugged an ethernet cable in the machine for debugging over SSH)

```
filip@xubuntu-server:~$ sudo ifdown wlan0 && sudo ifup wlan0
There is already a pid file /var/run/dhclient.wlan0.pid with pid 6214
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:c0:49:d7:6c:b8
Sending on   LPF/wlan0/00:c0:49:d7:6c:b8
Sending on   Socket/fallback
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:c0:49:d7:6c:b8
Sending on   LPF/wlan0/00:c0:49:d7:6c:b8
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 19
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

```
filip@xubuntu-server:~$ ping -c 3 -I wlan0 192.168.2.1
PING 192.168.2.1 (192.168.2.1) from 192.168.2.237 wlan0: 56(84) bytes of data.
From 169.254.9.32 icmp_seq=1 Destination Host Unreachable
From 169.254.9.32 icmp_seq=2 Destination Host Unreachable
From 169.254.9.32 icmp_seq=3 Destination Host Unreachable

--- 192.168.2.1 ping statistics ---
3 packets transmitted, 0 received, +3 errors, 100% packet loss, time 1999ms
, pipe 3
```

I don't know if it is important, but the wireless card is an USR5416 and uses ndiswrapper.

Any help will be very appreciated.

---

### Post by Nirva on 2009-03-01
I found A solution, but it isn't perfect yet.

When I disable the Ndiswrapper driver, and use the ACX driver, the static IP is obtained !! Weird bug !!

Can someone tell me where I should report this bug ?
Or tell me how to fix it ?

But this ACX Driver appears to be much slower... So solutions are still very welcome !

---

