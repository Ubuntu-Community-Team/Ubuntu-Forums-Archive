---
title: "creating an access point, dhcp via dnsmasq"
date: 2006-05-20
forum: Networking &amp; Wireless
---

### Post by samel_tvom on 2006-05-20
Hello!

I have just purchased a D-link DWL-G520 wireless card. It works with madwifi.
It can connect to my netgear accesspoint/router and everything is fine.

Now I want this card to be an access point. So I do the following:
```
#iwconfig ath0 mode Master
#iwconfig ath0 essid "HAXX"
#ifconfig ath0 10.0.0.1
```

And then I can find it with my laptop (which also can connect to my netgear AP)
So far so good, now I just have to configure dnsmasq (or so he thought...)

My dnsmasq.conf looks like this:
```
resolv-file=/etc/resolv.conf
no-poll
domain-needed
bogus-priv
strict-order

interface=ath0
interface=eth1

dhcp-range=192.168.0.10,192.168.0.50,12h
dhcp-range=10.0.0.10,10.0.0.100,12h

dhcp-host=00:0A:E4:52:6B:12,alice
dhcp-host=00:40:CA:45:10:9C,bob

dhcp-authoritative
```

And the output from ifconfig looks like:
```
root@force:~# ifconfig 
ath0      Link encap:Ethernet  HWaddr 00:15:E9:30:8C:4A  
          inet addr:10.0.0.1  Bcast:10.255.255.255  Mask:255.0.0.0
          inet6 addr: fe80::215:e9ff:fe30:8c4a/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1492  Metric:1
          RX packets:192 errors:689383 dropped:0 overruns:0 frame:689383
          TX packets:8 errors:282 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:200 
          RX bytes:104152 (101.7 KiB)  TX bytes:1648 (1.6 KiB)
          Interrupt:5 Memory:c8b40000-c8b50000 

eth0      Link encap:Ethernet  HWaddr 00:40:CA:1C:97:77  
          inet addr:85.235.31.133  Bcast:85.235.31.255  Mask:255.255.255.0
          inet6 addr: fe80::240:caff:fe1c:9777/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:517621 errors:0 dropped:0 overruns:0 frame:0
          TX packets:72772 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:69874515 (66.6 MiB)  TX bytes:70195546 (66.9 MiB)
          Interrupt:11 Base address:0x1080 

eth1      Link encap:Ethernet  HWaddr 00:90:27:5C:A0:5A  
          inet addr:192.168.0.1  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::290:27ff:fe5c:a05a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:263787 errors:0 dropped:0 overruns:0 frame:0
          TX packets:723590 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:45560011 (43.4 MiB)  TX bytes:762141527 (726.8 MiB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:72953 errors:0 dropped:0 overruns:0 frame:0
          TX packets:72953 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:21471070 (20.4 MiB)  TX bytes:21471070 (20.4 MiB)

```

So I thought everything was tiptop. On the AP I issue the following:
```
#dnsmasq -d
```

When I try to connect to the AP with my laptop by doing
```
#iwconfig wlan0 essid "HAXX"
#dhcpcd wlan0 (have tried dhclient as well)
```
I get no ip, but the AP gives:
```
root@force:/var/lib/misc# dnsmasq -d
dnsmasq: started, version 2.22 cachesize 150
dnsmasq: DHCP, IP range 10.0.0.10 -- 10.0.0.100, lease time 12h
dnsmasq: DHCP, IP range 192.168.0.10 -- 192.168.0.50, lease time 12h
dnsmasq: read /etc/hosts - 12 addresses
dnsmasq: reading /etc/resolv.conf
dnsmasq: using nameserver 81.88.9.220#53
dnsmasq: using nameserver 81.88.9.218#53
dnsmasq: DHCPDISCOVER(ath0) 00:0e:2e:3f:37:f5
dnsmasq: DHCPOFFER(ath0) 10.0.0.10 00:0e:2e:3f:37:f5
dnsmasq: DHCPDISCOVER(ath0) 00:0e:2e:3f:37:f5
dnsmasq: DHCPOFFER(ath0) 10.0.0.10 00:0e:2e:3f:37:f5
dnsmasq: DHCPDISCOVER(ath0) 00:0e:2e:3f:37:f5
dnsmasq: DHCPOFFER(ath0) 10.0.0.10 00:0e:2e:3f:37:f5
```
It looks like the AP tries to offer the ip but somehow it doesn't work. I know that it's nothing wrong on the client side, because if I try to connect to my netgear AP/router it works and I get an IP by issuing the following commands on the client(laptop):
```
#iwconfig wlan0 essid "NETGEAR"
#dhcpcd wlan0

```

So what's wrong with this picture?

Thanks in advance!

---

