---
title: "Identical machines, 10.04 server works fine, 10.04 desktop has slow internet"
date: 2011-11-22
forum: Networking &amp; Wireless
---

### Post by EarlsFurniture on 2011-11-22
So I've got this really perplexing problem:

I have two identical EL-1352 eMachines.  Each have AMD XII 64bit processors, 4GB RAM, wired ethernet, etc.

On one, I'm running 10.04 LTS Server x64.
On the other, 10.04 Desktop x64.

Both are fully up to date.

The Server works fine.

The Desktop is REALLY slow to load web pages. There is a definite hang on "connecting to" whatever server is in question.  There is also usually a definite lag in actually downloading the page.

Speed tests show the problem machine is getting the same as the server.
Ping is significantly slower on the desktop than the server.
Ping of the router is similar to the server. (not significantly slower, but slightly so)

Both have identical settings as far as I can tell.

```
lshw -C network
``` turns up NOTHING on either machine.

```
lshw
``` does show both have an ethernet device on *bridge

Here's the pertinent results of this command on the server:

```
*-bridge
       description: Ethernet interface
       product: MCP61 Ethernet
       vendor: nVidia Corporation
       physical id: 7
       bus info: pci@0000:00:07.0
       logical name: eth0
       version: a2
       serial: 00:26:2d:2e:20:18
       size: 1000000000
       capacity: 1000000000
       width: 32 bits
       clock: 66MHz
       capabilities: bridge pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 duplex=full ip=192.168.0.40 latency=0 link=yes maxlatency=20 mingnt=1 multicast=yes port=MII speed=1GB/s
       resources: irq:27 memory:febfd000-febfdfff ioport:e480(size=8)
```

and the desktop


```
*-bridge
       description: Ethernet interface
       product: MCP61 Ethernet
       vendor: nVidia Corporation
       physical id: 7
       bus info: pci@0000:00:07.0
       logical name: eth0
       version: a2
       serial: 00:26:2d:2f:31:da
       size: 1000000000
       capacity: 1000000000
       width: 32 bits
       clock: 66MHz
       capabilities: bridge pm msi ht bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 duplex=full ip=192.168.0.46 latency=0 link=yes maxlatency=20 mingnt=1 multicast=yes port=MII speed=1GB/s
       resources: irq:27 memory:febfd000-febfdfff ioport:e480(size=8)
```

Here's the pertinent results of ```
ifconfig
``` on the server:

```
eth0    Link encap:Ethernet  HWaddr 00:26:2d:2e:20:18  
          inet addr:192.168.0.40  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::226:2dff:fe2e:2018/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2643378 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3481872 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1754350981 (1.7 GB)  TX bytes:3455079371 (3.4 GB)
          Interrupt:27 Base address:0xe000
```

and on the Desktop:

```
eth0    Link encap:Ethernet  HWaddr 00:26:2d:2f:31:da  
          inet addr:192.168.0.46  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7471 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5904 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6686225 (6.6 MB)  TX bytes:1253340 (1.2 MB)
          Interrupt:27 Base address:0x4000
```As you can see, I've managed to successfully turn off IPv6 on the Desktop machine. (it is still enabled on the Server, but that one is giving no troubles)

Oddly, there are no dropped packets or errors on the problem machine, but my browser just sits there at a snails pace spinning before loading a page.  Almost always this is the case on initial page load.  It is *sometimes* quicker on the draw on a subsequent load, but not by much. Page rendering once it starts, can also be very slow. I have the same results with both Firefox & Chrome - both fully up to date.

It seems the only difference I can find, is one machine is using the server kernel, the other the desktop kernel.  Could that alone be the issue?  (is it possible to change kernels on a desktop install to a server kernel without re-installing the OS?)

I'm stumped.

Any guesses?

---

