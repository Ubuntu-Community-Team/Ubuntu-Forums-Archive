---
title: "Static IP changing randomly"
date: 2012-10-26
forum: Networking &amp; Wireless
---

### Post by Nodapic on 2012-10-26
I've been having an issue for a few months that I can't resolve:

I have an old Dell Desktop running 32-bit 11.04 that is supposed to have a static IP address. It has a wired ethernet line running to it (tested and working).  When I set the IP address to manual in the ubuntu Network Manager, the connections sits there with "Last Used: Never". 

However, at the same time, I am able to access the internet and when I run ifconfig, I get the following:

```
ifconfig
[INDENT]eth0      Link encap:Ethernet  HWaddr 00:07:e9:c6:c5:d2  
          inet addr: [IP that's not my static IP] Bcast:18.34.255.255  Mask:255.255.0.0
          inet6 addr: fe80::207:e9ff:fec6:c5d2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:19751 errors:0 dropped:1 overruns:0 frame:0
          TX packets:4586 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2179247 (2.1 MB)  TX bytes:346304 (346.3 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:28 errors:0 dropped:0 overruns:0 frame:0
          TX packets:28 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1760 (1.7 KB)  TX bytes:1760 (1.7 KB)
[/INDENT] 
```

Note that the IP address that I takes is not the static IP address and is different after reboots (smells like DHCP to me).

After not being able to set the connection successfully, I went to wicd to see if that would work better. wicd did allow me to set the IP address and would keep it for a while - HOWEVER, about once per week it would drop the IP and go to a different one. So that didn't work either.

Here are some more print outs that might be useful:

```
sudo lshw -C Network

[INDENT]  *-network               
       description: Ethernet interface
       product: 82557/8/9/0/1 Ethernet Pro 100
       vendor: Intel Corporation
       physical id: c
       bus info: pci@0000:02:0c.0
       logical name: eth0
       version: 10
       serial: 00:07:e9:c6:c5:d2
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=full firmware=N/A ip=[IP that's not my static IP] latency=64 link=yes maxlatency=56 mingnt=8 multicast=yes port=MII speed=100Mbit/s
       resources: irq:18 memory:fe1fe000-fe1fefff ioport:ec40(size=64) memory:fe1c0000-fe1dffff[/INDENT]
```


```
dmesg | grep eth0

[INDENT][    1.599271] e100 0000:02:0c.0: eth0: addr 0xfe1fe000, irq 18, MAC addr 00:07:e9:c6:c5:d2
[   11.292260] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   11.296281] e100 0000:02:0c.0: eth0: NIC Link is Up 100 Mbps Full Duplex
[   11.296723] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   21.504020] eth0: no IPv6 routers present[/INDENT]
```


Does anyone have an idea what could be going on here? Any suggestions are appreciated!

---

### Post by wyliecoyoteuk on 2012-10-26
Is there a possibility of another device with the same IP?

If it is within a DHCP range, there could be an IP conflict.

---

### Post by Nodapic on 2012-10-26
Hi wyliecoyoteuk

I checked the IP address and it's assigned to only me and not in a DHCP range. I guess that doesn't keep someone from guessing at it and getting lucky. I've never heard of that occurring repeatedly though...

---

### Post by chili555 on 2012-10-26
Was this IP address given to you by your university? I suspect the netmask and/or gateway you entered in Wicd is faulty. Have you entered exactly what was given? Do you mind if we check? Feel free to obscure the last two or three numbers of the IP address thus:```
18.34.231.xyz
```We'd like to see the netmask and gateway exactly. 

Ideally, we'd like to see what is given to you to use by the university and what is in place once your static IP drops in order to compare.

---

### Post by Nodapic on 2012-10-26
Hi chili555, 

I registered the IP address myself on our host registration system; the details are below. I have in the meantime also changed the /etc/network/interfaces file to this:

```
auto eth0
iface eth0 inet static
   address 18.34.2.xyz
   netmask 255.255.0.0
   network 18.34.0.0
   broadcast 18.34.255.255
   gateway 18.34.0.1
```

After restarting the networking service, I now have the needed static IP and it hasn't dropped yet...

PS: This is now using the network manager and not wicd.

---

### Post by chili555 on 2012-10-26
Your interfaces file looks correct to me, except, typically you won't need 'broadcast' or 'network' and you do need loopback. I'd tweak it just a bit to:```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
   address 18.34.2.xyz
   netmask 255.255.0.0
   gateway 18.34.0.1
```You probably also need to specify DNS nameservers:```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
   address 18.34.2.xyz
   netmask 255.255.0.0
   gateway 18.34.0.1
   dns-nameservers 8.8.8.8 18.34.0.1 [COLOR="Red"]<--or whatever you prefer[/COLOR]
```

I think you'll have better luck using either manual methods (/etc/network/interfaces) *OR* Network Manager, but not both. If this computer is going to sit at the university for the foreseeable future, I'd feel confident removing NM.

---

### Post by Nodapic on 2012-10-26
Hi chili555

Thank you, I'll make sure to add the dns and the loop back. So far the connection has been stable so we probably figured it out... I'll mark this thread as solved (or at least I'll try to figure out how to do that... :) ).

---

