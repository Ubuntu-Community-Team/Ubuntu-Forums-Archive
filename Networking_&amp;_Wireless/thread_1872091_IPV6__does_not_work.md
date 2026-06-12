---
title: "IPV6  does not work"
date: 2011-10-30
forum: Networking &amp; Wireless
---

### Post by Hkeyos on 2011-10-30
hey, my ubuntu11.10 can get ipv6 address successfully, but can not get internet connection. while, i switch to windows7, it works well. This is my address info.
eth0      Link encap:Ethernet  HWaddr 10:78:d2:f4:33:70  
          inet addr:202.117.10.136 Bcast:202.117.10.255  Mask:255.255.255.0
          inet6 addr: 2002:ca75:f56:6:1278:d2ff:fef4:3370/64 Scope:Global
          inet6 addr: fec0::6:1278:d2ff:fef4:3370/64 Scope:Site
          inet6 addr: 2001:250:1001:1712:1278:d2ff:fef4:3370/64 Scope:Global
          inet6 addr: 2001:da8:4000:a000:1278:d2ff:fef4:3370/64 Scope:Global
          inet6 addr: fe80::1278:d2ff:fef4:3370/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
when i trace router, all failed. :(
traceroute6 bt.shu6.edu.cn
traceroute to bt.shu6.edu.cn (2001:da8:8006:1:218:71ff:fe77:3ccb) from 2001:da8:4000:a000:1278:d2ff:fef4:3370, port 33434, from port 61733, 30 hops max, 60 bytes packets
 1  * * *         
 2  * * *         
 3  * * *         
 4  * * *         
 5  * * *         
 6  * * *         
:-(
who can help me, thanks.

---

### Post by lemming465 on 2011-10-31
Could we see the Linux output from```

ip address show
ip -4 route show
ip -6 route show
```
Also, on windows 7, could we see the output from```

ipconfig /all
route print
```
And, could you describe your ISP connection upstream in a little more detail?
Is there a Wifi router?  A broadband DSL or cable modem?  Does the ISP offer a v4-only connection, a v6-only connection, a dual-stack connection with both, a dual-stack-lite connection, or what?  You seem to have a public IPv4 address, for example.  Are you using a tunnel broker or a native v6 connection?

What's a little odd looking in your ifconfig output is that you appear to have both a 6to4 tunnel addresss (2002:...) and two native IPv6 addresses (2001:250:..., 2001:da8:...).  Also weird is that the /48 prefix on your 6to4 tunnel address doesn't embed your IPv4 address; you have 2002:ca75:f56:... when I would expect you to have 2002:ca75:a88:...

Do you know how your IPv6 addresses are being configured?  Typical for native IPv6 would be stateless autoconfiguration based on router advertisements from your upstream device, but static and DHCPv6 are also possibilities.  Most consumer grade wifi and broadband gear currently gets DHCPv6 wrong.

---

