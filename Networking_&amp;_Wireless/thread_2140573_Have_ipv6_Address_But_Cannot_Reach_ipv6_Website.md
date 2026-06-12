---
title: "Have ipv6 Address But Cannot Reach ipv6 Website"
date: 2013-04-30
forum: Networking &amp; Wireless
---

### Post by chepix on 2013-04-30
Hi,

I cannot reach the ipv6 website such as [http://ipv6.google.com/](http://ipv6.google.com/) ,

then i go to [http://test-ipv6.com/](http://test-ipv6.com/) and it shows

You appear to have no IPv6 at this time..

then I run ifconfig

```
sudo ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1e:37:21:82:e3  
          inet6 addr: 2402:f000:5:7201:c063:60db:2030:aabe/64 Scope:Global
          inet6 addr: 2402:f000:5:7201:21e:37ff:fe21:82e3/64 Scope:Global
          inet6 addr: fe80::21e:37ff:fe21:82e3/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:112085 errors:0 dropped:0 overruns:0 frame:0
          TX packets:40746 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:96434595 (96.4 MB)  TX bytes:5377655 (5.3 MB)
          Interrupt:16 Memory:ee000000-ee020000 

```
It seems that i do have ipv6 address. Why test-ipv6 tell me no ipv6 address? How can i fix this?

---

### Post by fyfe54 on 2013-04-30
Try installing miredo from the Software Center, then try those addresses again.  (sudo apt-get install miredo)
It worked for me.  

Thanks to Sanderj  - I found the miredo info in his signature.

---

### Post by lemming465 on 2013-05-01
If you have an address but no connectivity, there may be some kind of routing glitch.   Possibly with your ISP, possibly with your network.  Can you provide more details about the equipment along the path from your computer to the general internet and who your ISP is?

Could we see the results from *ip -6 route show* and *ip -6 neighbor show*?

Also, what does *sudo rdisc6 eth0* produce in the way of router advertisements?  (if rdic6 isn't installed, run "sudo apt-get install ndisc6" first).

---

### Post by Iowan on 2013-05-01
> **chepix said:**
> It seems that i do have ipv6 address. Why test-ipv6 tell me no ipv6 address? How can i fix this?It appears that you have 3 ???
One might be self-assigned - lacking other addresses.
The rest???

---

### Post by sandyd on 2013-05-01
> **Iowan said:**
> It appears that you have 3 ???
One might be self-assigned - lacking other addresses.
The rest???

Two is normal (one is the link local)

In that case - can you post the output of
```

route -6 -n
```

Thanks!

Also, there is something wrong with one of your incoming ipv6 routers - 2402:F000:0:2B6::181 is not reachable

---

### Post by chepix on 2013-05-05
Sorry, I didn't check the forum several days and didn't reply in time.
My ISP is CERNET, Chinese education and research network.  ipv6 addresses are distributed via DHCP.

~$ ip -6 route 
2402:f000:5:7201::/64 dev eth0  proto kernel  metric 256  expires 2592043sec
fe80::/64 dev eth0  proto kernel  metric 256 
default via fe80::205:85ff:fe7a:4cb2 dev eth0  proto kernel  metric 1024  expires 1681sec

~$ ip -6 neigh 
fe80::205:85ff:fe7a:4cb2 dev eth0  router FAILED

~$ sudo rdisc6 eth0
 Soliciting ff02::2 (ff02::2) on eth0...
Timed out.
Timed out.
Timed out.
No response.

It seems that the ipv6 router does not work, and i have tried to connect to the same wired network in winxp or win7, it works, without any problem.

In addition, i try to use a wireless route to change the wired to wireless, and connect to the wireless network in debian gnu/linux, it works. then i run the same command as follows:

~$ ip -6 route 
it shows the same as previous one, with the 'eth0' replaced by 'wlan0'

~$ ip -6 neigh 
fe80::205:85ff:fe7a:4cb2 dev wlan0 lladdr 00:05:85:7a:4c:b2 router STALE


~$ sudo rdisc6 wlan0
Hop limit                 :           64 (      0x40)
Stateful address conf.    :           No
Stateful other conf.      :           No
Router preference         :       medium
Router lifetime           :         1800 (0x00000708) seconds
Reachable time            :  unspecified (0x00000000)
Retransmit time           :  unspecified (0x00000000)
 Source link-layer address: 00:05:85:7A:4C:B2
 Prefix                   : 2402:f000:5:7201::/64
  Valid time              :      2592000 (0x00278d00) seconds
  Pref. time              :       604800 (0x00093a80) seconds
 from fe80::205:85ff:fe7a:4cb2

---

### Post by chepix on 2013-05-05
Sorry, I didn't check the forum several days and didn't reply in time.
My ISP is CERNET, Chinese education and research network.  ipv6 addresses are distributed via DHCP.

```
~$ ip -6 route 
2402:f000:5:7201::/64 dev eth0  proto kernel  metric 256  expires 2592043sec
fe80::/64 dev eth0  proto kernel  metric 256 
default via fe80::205:85ff:fe7a:4cb2 dev eth0  proto kernel  metric 1024  expires 1681sec

~$ ip -6 neigh 
fe80::205:85ff:fe7a:4cb2 dev eth0  router FAILED

~$ sudo rdisc6 eth0
 Soliciting ff02::2 (ff02::2) on eth0...
Timed out.
Timed out.
Timed out.
No response.
```

It seems that the ipv6 router does not work, and i have tried to connect  to the same wired network in winxp or win7, it works, without any  problem.

In addition, i try to use a wireless route to change the wired to  wireless, and connect to the wireless network in debian gnu/linux, it  works. then i run the same command as follows:

```
~$ ip -6 route 
it shows the same as previous one, with the 'eth0' replaced by 'wlan0'

~$ ip -6 neigh 
fe80::205:85ff:fe7a:4cb2 dev wlan0 lladdr 00:05:85:7a:4c:b2 router STALE

~$ sudo rdisc6 wlan0
Hop limit                 :           64 (      0x40)
Stateful address conf.    :           No
Stateful other conf.      :           No
Router preference         :       medium
Router lifetime           :         1800 (0x00000708) seconds
Reachable time            :  unspecified (0x00000000)
Retransmit time           :  unspecified (0x00000000)
 Source link-layer address: 00:05:85:7A:4C:B2
 Prefix                   : 2402:f000:5:7201::/64
  Valid time              :      2592000 (0x00278d00) seconds
  Pref. time              :       604800 (0x00093a80) seconds
 from fe80::205:85ff:fe7a:4cb2 				
```

---

### Post by sandyd on 2013-05-07
> **chepix said:**
> Sorry, I didn't check the forum several days and didn't reply in time.
My ISP is CERNET, Chinese education and research network.  ipv6 addresses are distributed via DHCP.

```
~$ ip -6 route 
2402:f000:5:7201::/64 dev eth0  proto kernel  metric 256  expires 2592043sec
fe80::/64 dev eth0  proto kernel  metric 256 
**default via fe80::205:85ff:fe7a:4cb2 dev eth0  proto kernel  metric 1024  expires 1681sec**

~$ ip -6 neigh 
fe80::205:85ff:fe7a:4cb2 dev eth0  router FAILED

~$ sudo rdisc6 eth0
 Soliciting ff02::2 (ff02::2) on eth0...
Timed out.
Timed out.
Timed out.
No response.
```

It seems that the ipv6 router does not work, and i have tried to connect  to the same wired network in winxp or win7, it works, without any  problem.

In addition, i try to use a wireless route to change the wired to  wireless, and connect to the wireless network in debian gnu/linux, it  works. then i run the same command as follows:

```
~$ ip -6 route 
it shows the same as previous one, with the 'eth0' replaced by 'wlan0'

~$ ip -6 neigh 
fe80::205:85ff:fe7a:4cb2 dev wlan0 lladdr 00:05:85:7a:4c:b2 router STALE

~$ sudo rdisc6 wlan0
Hop limit                 :           64 (      0x40)
Stateful address conf.    :           No
Stateful other conf.      :           No
Router preference         :       medium
Router lifetime           :         1800 (0x00000708) seconds
Reachable time            :  unspecified (0x00000000)
Retransmit time           :  unspecified (0x00000000)
 Source link-layer address: 00:05:85:7A:4C:B2
 Prefix                   : 2402:f000:5:7201::/64
  Valid time              :      2592000 (0x00278d00) seconds
  Pref. time              :       604800 (0x00093a80) seconds
 from fe80::205:85ff:fe7a:4cb2 				
```

There is something wrong with the route - the default gateway should not be fe80::205:85ff:fe7a:4cb2, because it is a local ipv6

---

### Post by lemming465 on 2013-05-08
>  ... the default gateway should not be fe80::205:85ff:fe7a:4cb2, because it is a local ipv6 
On the contrary, except for statically configured routes, in conformant IPv6 implementations the default route **must** be a link-local scope fe80::/64 address.   In IPv6 networks, the *only* way to locate a router automatically is by listening for ICMv6 Router Advertisements, and observing the sending address.  See [section 4.2 in RFC 4861 about neighbor discovery]("https://tools.ietf.org/html/rfc4861#page-19").

A typical IPv6 host has a *minimum* of **5** addresses:
[LIST=1]
[*]the node-scope loopback address ::1
[*]a link-local fe80::/64 address, perhaps with host-part using the EUI-64 mapping from a 48-bit ethernet MAC
[*]a global scope address starting with 2000::/3, usually from an on-link prefix
[*]listening on ff02::1, the all-hosts multicast group, where spontaneous RA's go
[*]listening on the ff02::1:ffXX:YYZZ neighbor discovery multicast groups corresponding to every unicast address
[/LIST]
If there are tunnels, privacy addressessing, VM guests, or multiple on-link prefixes involved there could be a lot more than 5 addresses.

The legacy IPv4 case isn't quite as simple as people imagined, with 1 address per host; take a good look at the v4 versus v6 entries in the output of```
ip address show
ip maddress show
```
sometime.

---

### Post by lemming465 on 2013-05-09
Hmm.  If I understand you correctly,
* v6 works from various versions of windows when wired
* v6 works from Linux over wireless
* v6 fails from Linux when wired

It's not clear if there are any virtual machines involved, or if these are physical, and if the XP and Linux hosts are different or dual-boot.  More details would help.

The output from te wired scenario for Linux shows that:
1) you got an RA at least once, because you installed a default route
2) something is wrong with neighbor discovery, because the the router address is unreachable

The scenarios that have done something similar to me historically involved duplicate ethernet addresses somewhere.  E.g. clones of VMware virtual guests that had been "moved" rather "copied", or bad NIC hardware, or Cisco ASA firewall subinterfaces on trunked switch ports using multiple VLAN's, but with a dumb hub in the topology, where the sub-interfaces had specified different IPv6 global addresses but not also specified distinct IPv6 link-local addresses.

A link-local host address is validated after being assigned but before being used by "duplicate address detection", where you send a neighbor solicitation out for your prospective address, and if any advertisements come back, you know someone else is using it, and you stop.  The first RS/RA exchange uses :: as the v6 source address on the router solicitation, which is why you can get one RA back before dying of DAD fratricide.

The ethernet prefix of the router is from Juniper; who don't tend to make consumer gear, so I'm guessing this is at a school or workplace rather than a home?

---

