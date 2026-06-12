---
title: "Ubable to access Ubuntu PC over LAN when using PPPOE"
date: 2012-04-05
forum: Networking &amp; Wireless
---

### Post by mgblake7 on 2012-04-05
Hi

I am having an issue accessing my Ubuntu PC over the LAN when my DSL connection is active.

When I disconnect the DSL and switch to eth0 it works perfectly, but surely the ppp connection runs over the ethernet one?

would appreciate any help.

---

### Post by nothingspecial on 2012-04-07
*Thread moved to **Networking & Wireless**.*

---

### Post by dandnsmith on 2012-04-07
Can you clarify something here.
It isn't immediately clear whether the Ubuntu PC and the DSL connection are both over eth0.

---

### Post by mgblake7 on 2012-04-10
It would seem that it is, Im no Ubuntu expert, but when i click on the DSL connection, it says "Auto Eth0 Disconnected" and then "DSL Connected".

This is my if config result when DSL is active:
```

eth0      Link encap:Ethernet  HWaddr 00:13:d4:31:3c:83  
          inet6 addr: fe80::213:d4ff:fe31:3c83/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:15122303 errors:0 dropped:0 overruns:0 frame:0
          TX packets:19780078 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7430294787 (7.4 GB)  TX bytes:15800790285 (15.8 GB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8138 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8138 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:792805 (792.8 KB)  TX bytes:792805 (792.8 KB)

ppp0      Link encap:Point-to-Point Protocol  
          inet addr:#.#.#.#  P-t-P:#.#.#.#  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          RX packets:2090 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2182 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:1018879 (1.0 MB)  TX bytes:380216 (380.2 KB)

wlan0     Link encap:Ethernet  HWaddr 00:19:cb:41:08:e8  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


```

and when Auto eth0 is active:
```

eth0      Link encap:Ethernet  HWaddr 00:13:d4:31:3c:83  
          inet addr:192.168.1.7  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::213:d4ff:fe31:3c83/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:15123502 errors:0 dropped:0 overruns:0 frame:0
          TX packets:19780917 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7431300832 (7.4 GB)  TX bytes:15800931536 (15.8 GB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8154 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8154 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:793989 (793.9 KB)  TX bytes:793989 (793.9 KB)

wlan0     Link encap:Ethernet  HWaddr 00:19:cb:41:08:e8  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


```

---

### Post by dandnsmith on 2012-04-10
OK
that clearly shows that there is an either/or arrangement at present.
There may possibly be some room for manouevre, depending on the physical connections, but this would have to be specially set up.
I still don't see what your physical connection arrangements are.

---

### Post by mgblake7 on 2012-04-10
I have a single network card connected to a LAN which uses a router that connects to a separate DSL account.

does that help?

---

### Post by dandnsmith on 2012-04-10
Hmmm!
I was beginning to wonder if that were the case.
Why are you doing PPPoE from your PC rather than letting the router take care of everything? This would be the usual way to do things, rather than locking the internet connection to your PC - is there a reason to do it your way (odd router model ...)?

---

### Post by mgblake7 on 2012-04-10
The reason for that set up is that the Ubuntu PC is a torrent server I've set up, which is connecting over an uncapped DSL connection.

the uncapped connection is slow during the day however and is not suitable for the rest of the network. I also cant have the server connecting over our standard dsl account as it would finish the cap pretty quickly.

is it possible to have eth0 and ppp0 connected simultaneously in Ubuntu?

---

### Post by dandnsmith on 2012-04-10
I've seen people looking for a way to use one physical ethernet port for multiple (virtual) interfaces, each with its own address etc.
There have been some threads on these fora on the topic - a search should reveal them. That part is certainly possible, and has been used to (effectively) separate traffic for two distinct subnets through one interface.
I'd be interested to hear that you make some headway on this - but don't know whether it would be possible to use you connection the ways you'd like - I've a nasty feeling that you might get the multiple interfaces configured, but then find that the other end of the physical wire (at the router) would then be the block (as you'd need two interfaces, effectively, there as well).

Good luck in your quest.

---

### Post by maximus5 on 2012-11-10
mgblake7

Hey...I do this all the time. Completely possible. 

After connecting to your PPPoE (DSL) account (using ubuntu network manager), start the terminal up and type the following: sudo ifconfig eth0 192.168.1.7

The terminal supports the virtual devices. 

You could make a shortcut on your desktop to run this command after you've connected to the DSL connection each time.

THIS means you'd be connected to your DSL and local network SIMALTANEOUSLY =)

---

