---
title: "Local VM not able to ping out, but can SSH in."
date: 2010-11-25
forum: Networking &amp; Wireless
---

### Post by mcdogfood on 2010-11-25
Hello, and thanks for reading. I've spent quite a lot of time reading this forum for similar posts and no one seems to quite be in the same situation, but apologies if this has already been answered somewhere by somewhere else.

I have a Windows XP laptop, connected wirelessly to a router.

On this machine, I've installed VMWare server, and created a Ubuntu 8.0.4 server virtual machine, which boots properly, and I can log in using SSH over PuTTY.

The VM adapter is bridged, and set manually to the wireless card. I've tried it on automatic with the same behaviour.

What I can't do is ping out from the Ubuntu server to anywhere, locally, or worldly, using IP or DNS, although ifconfig reports it has a valid IP address.

eth0      Link encap:Ethernet  HWaddr <deleted>
          inet addr:192.168.0.3  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:29ff:feda:5ebd/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8573 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4138 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:970673 (947.9 KB)  TX bytes:589798 (575.9 KB)
          Interrupt:17 Base address:0x2000

ip neigh reports :
192.168.0.2 dev eth0 lladdr <deleted> REACHABLE
it is also reporting DELAY sometimes, so maybe it's going in a cycle and never able to properly connect.

The MAC addresses are different in ip neigh from the one in ifconfig, but I would expect that.

If anyone has any ideas, I would be very appreciative.

Thank you

Joe

---

