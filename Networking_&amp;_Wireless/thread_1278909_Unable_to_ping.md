---
title: "Unable to ping"
date: 2009-09-30
forum: Networking &amp; Wireless
---

### Post by bharath_neo on 2009-09-30
Hi,

I had set up my new ubuntu server today and tried configuring the wireless.

I have my wireless interface up. My iwconfig output shows that it is hooked to the access pt.

 ```

wlan0     IEEE 802.11bg  ESSID:"wire"  
           Mode:Managed  Frequency:2.412 GHz  Access Point: 00:1B:5B:1E:41:51   
           Bit Rate:1 Mb/s   Tx-Power=20 dBm   
           Retry limit:7   RTS thr=off   Fragment thr=2352 B   
           Power Management:off
           Link Quality=70/100  Signal level=-50 dBm  Noise level= -95 dBm
           Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
           Tx excessive retries:0  Invalid misc:0   Missed beacon:0
virbr0         No wireless extensions.

```

My ifconfig output shows that the wlan0 is up and running.

```

wlan0     Link encap:Ethernet  HWaddr 00:16:cf:42:ed:06
          inet6 addr: fe80::215:afff:fe30:ffba/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2089 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:89142 (89.1 KB)  TX bytes:1040 (1 KB)

```

When I try to do a ping [www.google.com]("http://www.google.com"), it gives ping:unknown host [www.google.com]("http://www.google.com").
Same with when I try it with an ip address. It says Network is unreachable.

I tried looking at the route table.

```

Kernel IP routing table
Destination  Gateway         Genmask        Flags Metric Ref  Use Iface
192.168.122.0     *          255.255.255.0  U     0      0     0  virbr0
#

```

Looks like there is no ipv4 route thats present for wlan0. 
I tried adding it explicitly through the route add default command.
But still the ping doesnt go through. 
I think what I did for adding the route was wrong. Also wlan0 has only an 
inet6 address and no inet address. Is that fine not having an ipv4 address?

```

Kernel IP routing table
Destination  Gateway         Genmask        Flags Metric Ref  Use Iface
192.168.1.0       *          255.255.255.0  U     0      0     0  wlan0
192.168.122.0     *          255.255.255.0  U     0      0     0  virbr0
#

```

Can someone point me to what is wrong to get my ping going through?

---

### Post by t0mppa on 2009-09-30
I suppose it could be that purely an IPv6 address would work for you, but that'd be a first I've seen on these forums. Also, then your router should be on IPv6 as well as all your routing information, DNS addresses, etc. Are you using DHCP or static address? And how are you making the connection, manually or through some GUI?

The route you added is only the local network, it is just telling the system that any contact to 192.168.1.x addresses doesn't need to be sent through a router, but can be directly established. You still need a route for all the rest of the addresses, which would be a default route with your router as the gateway through which the traffic goes. Can add that with **route add default gw <ip_address_of_your_router> wlan0**.

---

### Post by bharath_neo on 2009-09-30
The ip address is assigned through DHCP. I tried to add the ipaddress of the gateway, but it gives me a SIOCADDRT:No such process error.

SIOCADDRT:No such process

The commad i tried was route add default gw 192.168.1.254 wlan0 (but wlan0 was not an option. The only option in w was window).

---

### Post by t0mppa on 2009-09-30
Ok, then go to terminal and run the following commands to see what's happening:```
dmesg | grep wlan0
less /var/log/syslog | grep DHCP
```

If neither shows any activity with the AP, then I think we should take a look at your drivers instead.

---

### Post by bharath_neo on 2009-10-01
Hi,

Thanks for taking a look. I had tried dmesg prev and had seen this error. Had tried adding blacklist ipv6 on /etc/modprobe.d/blacklist as well. Still did not work :(

dmesg | grep wlan0

```

[62.570689] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[89.899403] wlan0: direct probe to AP 00:1b:5b:1e:41:51 try 1
[90.090064] wlan0: direct probe to AP 00:1b:5b:1e:41:51 try 2
[90.091766] wlan0: direct probe responded
[90.091770] wlan0: authenticate with AP 00:1b:5b:1e:41:51
[90.093353] wlan0: authenticated
[90.093357] wlan0: associate with AP 00:1b:5b:1e:41:51
[90.096543] wlan0: RX AssocResp from 00:1b:5b:1e:41:51 (capab=0x431 status=0 aid=3)
[90.096549] wlan0: associated
[90.097229] ADDRCONF(NETDEV_CHANGE) wlan0: link becomes ready
[101.09605] wlan0: no IPV6 routers present

```

less /var/log/syslog | grep DHCP

```

Sep 30 07:43:10 ubuntu dnsmasq[2485]: no address range available for DHCP request via wlan0
Sep 30 07:53:57 ubuntu dnsmasq[2477]: DHCP, IP range 192.168.122.2 -- 192.168.122.254, lease time 1h

```

---

### Post by bharath_neo on 2009-10-01
Hi,
Thanks a lot for helping me. I just realized my mistake. Forgot to start the dhclient which has caused this issue.

---

### Post by t0mppa on 2009-10-01
No problem, glad you got it working.

P.S. You can mark the thread as solved from the thread tools, so people can see you don't need help anymore.

---

