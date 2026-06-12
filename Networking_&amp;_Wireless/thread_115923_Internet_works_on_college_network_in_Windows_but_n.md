---
title: "Internet works on college network in Windows but not Ubuntu"
date: 2006-01-11
forum: Networking &amp; Wireless
---

### Post by ashgromnies on 2006-01-11
I am at college and our network does funky things.

Anyways, I have a computer that is dual booting Windows and Ubuntu Linux and I can't seem to connect to the internet from Linux. I receive packets but I receive errors whenever it tries to transmit packets.

Here's my ifconfig:
```

etho0
Link encap:Ethernet HWaddre 00:13:8F:49:B8:4F
inet6 addr: fe80::213:8fff:fe49:b84f/64 Scope:Link
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets: 5451 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:628575 (613.8 KiB) TX bytes:0 (0.0 b)
Interrupt:17 Base address:0xe800

lo
Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:4876 errors:0 dropped:0 overruns:0 frame:0
TX packets:4876 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:443113 (432.7 KiB) TX bytes:443113 (432.7 KiB)
```

If anyone could help at all, I'd be so happy. I really need this thing connected to the net so I can do my programming assigment.


Shouldn't it also be ipv4 rather than inet6?
I've tried running dhclient3 and restarting eth0 but I've had no luck.


Ethernet controller: ALi Corporation: Unknown device 5263 (rev 40)

I can't get an IP via DHCP is the problem I'm having.


```
sit0: unknown hardware address type 776
Listening on LPF/sit0/
Sending on LPF/sit0/
Listening on LPF/eth0/00:13:8f:49:b8:4f
Sending on LPF/eth0/00:13:8f:49:b8:4f
Listening on LPF/lo/
Sending on LPF/lo/
Sending on Socket/fallback

DHCPDISCOVER bla bla(there are about 15 DHCPDISCOVER lines for different devices)

No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

---

### Post by cwaldbieser on 2006-01-11
[QUOTE=ashgromnies]I am at college and our network does funky things.

Anyways, I have a computer that is dual booting Windows and Ubuntu Linux and I can't seem to connect to the internet from Linux. I receive packets but I receive errors whenever it tries to transmit packets.

Here's my ifconfig:
```

etho0
Link encap:Ethernet HWaddre 00:13:8F:49:B8:4F
inet6 addr: fe80::213:8fff:fe49:b84f/64 Scope:Link
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets: 5451 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:628575 (613.8 KiB) TX bytes:0 (0.0 b)
Interrupt:17 Base address:0xe800

lo
Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:4876 errors:0 dropped:0 overruns:0 frame:0
TX packets:4876 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:443113 (432.7 KiB) TX bytes:443113 (432.7 KiB)
```

If anyone could help at all, I'd be so happy. I really need this thing connected to the net so I can do my programming assigment.


Shouldn't it also be ipv4 rather than inet6?
I've tried running dhclient3 and restarting eth0 but I've had no luck.


Ethernet controller: ALi Corporation: Unknown device 5263 (rev 40)

I can't get an IP via DHCP is the problem I'm having.


```
sit0: unknown hardware address type 776
Listening on LPF/sit0/
Sending on LPF/sit0/
Listening on LPF/eth0/00:13:8f:49:b8:4f
Sending on LPF/eth0/00:13:8f:49:b8:4f
Listening on LPF/lo/
Sending on LPF/lo/
Sending on Socket/fallback

DHCPDISCOVER bla bla(there are about 15 DHCPDISCOVER lines for different devices)

No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```[/QUOTE]

ifconfig always seems to give an ipv6 address, even when your interface isn't configured.  The fact that your interface doesn't have an ipv4 address means it isn't configured.

Can you try giving it a static address?  What are the settings from Windows like?

---

### Post by TX7 on 2006-01-11
Yeah. ipconfig it in "dos" and bring up the DNS and put in a static IP. I'd at least skip xxx.xxx.xx.1-30, considering it's a college network and those have probably all been used up already.

---

### Post by ashgromnies on 2006-01-11
[QUOTE=TX7]Yeah. ipconfig it in "dos" and bring up the DNS and put in a static IP. I'd at least skip xxx.xxx.xx.1-30, considering it's a college network and those have probably all been used up already.[/QUOTE]
I put in the results I got from Windows and still can't connect. I think it's an issue with drivers - I have an ALi motherboard.


EDIT: Google says this: [http://kernel.org/pub/linux/kernel/people/akpm/patches/2.6/2.6.13-rc3/2.6.13-rc3-mm1/broken-out/tulip-fixes-for-uli5261.patch](http://kernel.org/pub/linux/kernel/people/akpm/patches/2.6/2.6.13-rc3/2.6.13-rc3-mm1/broken-out/tulip-fixes-for-uli5261.patch) will work... how do I add that change? I will obviously need to rebuild the kernel and I've never done that.. I'm a developer but primarily a Windows one so I'm not familiar with gcc.

---

