---
title: "IPv6 static + IPv6 privacy addressing"
date: 2013-03-08
forum: Networking &amp; Wireless
---

### Post by markius on 2013-03-08
Minimal install of 12.04LTS

I'd like to have a static IPv6 + privacy address.

With "iface eth0 inet6 auto" I get privacy + SLAAC
With "iface eth0 inet6 static" I only get static.  This seems wrong.

```
root@ubuntu:~# cat /etc/network/interfaces
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
 address 10.150.212.86
 gateway 10.150.212.65
 netmask 255.255.255.192
 network 10.150.212.64
 broadcast 10.150.212.127
 dns-nameservers 10.150.212.141 10.150.212.142
 dns-domain local
# This is an autoconfigured IPv6 interface
iface eth0 inet6 static
 address 2a00:XXXX:5:140::56
 netmask 64
 gateway 2a00:XXXX:5:140::1
 dns-nameservers 2a00:XXXX:5:180::8d,2a00:XXXX:5:180::8e
 dns-domain local
```

```
root@ubuntu:~# cat /etc/sysctl.d/10-ipv6-privacy.conf
# IPv6 Privacy Extensions (RFC 4941)
# ---
# IPv6 typically uses a device's MAC address when choosing an IPv6 address
# to use in autoconfiguration. Privacy extensions allow using a randomly
# generated IPv6 address, which increases privacy.
#
# Acceptable values:
#    0 - donât use privacy extensions.
#    1 - generate privacy addresses
#    2 - prefer privacy addresses and use them over the normal addresses.
net.ipv6.conf.all.use_tempaddr = 2
net.ipv6.conf.default.use_tempaddr = 2
```

```
root@ubuntu:~# ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 00:50:56:a7:37:25
          inet addr:10.150.212.86  Bcast:10.150.212.127  Mask:255.255.255.192
          inet6 addr: fe80::250:56ff:fea7:3725/64 Scope:Link
          inet6 addr: 2a00:XXXX:5:140::56/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:330 errors:0 dropped:0 overruns:0 frame:0
          TX packets:228 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:29414 (29.4 KB)  TX bytes:30357 (30.3 KB)
```

---

### Post by lemming465 on 2013-03-08
The short answer, I fear, is that IPv6 isn't designed to do what you want.

Your key difficulty is that SLAAC is mostly controlled by the RA flags, not by the client.  The prefixes advertised in the RA as being on-link (meaning clients should do neighbor discovery for them, as opposed to forwarding to gateways when going off-link) are flagged as to whether they are intended for autoconfiguration or not.  Privacy addresses are intended to mask the EUI-64 mapped embedding of ethernet 48 bit MAC identifiers, particularly for reducing traceability of mobile devices.  So normally SLAAC is a router choice, and privacy is a client add-on to that.  Static addresses are normally imagined to apply to services expecting inbound connections, which rather obviates privacy.

If you control the router, one ploy would be to use a DHCPv6 server which hands out randomized host parts rather than using SLAAC.  You could still add the static address in a post-up script.

If you don't mind having static + SLAAC + privacy, you could just use the temp_addr=2 add the static in a post-up script.   That would create a situation which tends to send from privacy but can still receive on static.

---

### Post by markius on 2013-03-08
Could I make it do SLAAC + static and prefer the SLAAC address for outbound?

---

### Post by markius on 2013-03-08
Hey lemming465

I kind of had my head up my butt today and consequently didn't properly read your response and I feel like my reply was a bit rude.  Sorry about that.

Now I've actually read and understood, I can see that your solution acheives exactly what I need:

I've changed the relevant part of /etc/network/interfaces...

```
auto eth0
iface eth0 inet static
 address 10.150.212.86
 gateway 10.150.212.65
 netmask 255.255.255.192
 network 10.150.212.64
 broadcast 10.150.212.127
 dns-nameservers 10.150.212.141 10.150.212.142
 dns-domain local
# This is an autoconfigured IPv6 interface
iface eth0 inet6 auto
 up ip -f inet6 addr add 2a00:XXXX:5:140::56/64 dev eth0
```

...which gives me...

```
root@ubuntu:~# ip -f inet6 addr show dev eth0
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qlen 1000
    inet6 2a00:XXXX:5:140:6875:5052:2915:4786/64 scope global temporary dynamic
       valid_lft 604469sec preferred_lft 85469sec
    inet6 2a00:XXXX:5:140:250:56ff:fea7:3725/64 scope global dynamic
       valid_lft 2591669sec preferred_lft 604469sec
    inet6 2a00:XXXX:5:140::56/64 scope global
       valid_lft forever preferred_lft forever
    inet6 fe80::250:56ff:fea7:3725/64 scope link
       valid_lft forever preferred_lft forever
```

And I can confirm that the temporary IPv6 is used for outbound.

Thanks for your help!

---

