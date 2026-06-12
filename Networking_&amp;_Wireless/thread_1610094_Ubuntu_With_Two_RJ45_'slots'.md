---
title: "Ubuntu With Two RJ45 'slots'?"
date: 2010-10-31
forum: Networking &amp; Wireless
---

### Post by csharpplus on 2010-10-31
First of all, I am a newbie, so bear with me if I am missing something too obvious.

I have a machine (configured with a static IP) that is connected to a switch through its RJ45 slot. 
 this machine (and same holds true for the other machines that are connected to the switch) is NOT connected to the internet.


I wanted to connect this machine (only) to the internet (I have a separate router that is connected to the internet line), while still having it connected to the switch that (by design) does not provide connectivity to the internet.

since the machine has only one RJ45 slots, I bought a small device that exposes another RJ45 slot when connected to a USB (it is some sort of USB to RJ45 converter). I figured this can be used to also connect the machine to the router (that -- as I wrote earlier, 'provides' internet). When I connected this new USB/RJ45 adapter, Ubuntu recognized it (I saw a 'connected' message), but when I opened 'Network Connections', I only saw the connection that 'belongs' to the switch (the one that uses the machine's RJ45 slot). I did not see anything regarding the new USB/RJ45 adapter that I added.

Any ideas on how to solve this?  thanks.

---

### Post by Iowan on 2010-10-31
From a terminal (Applications>Accessories>Terminal), check **ifconfig -a** (post if possible). There are several things that *might* cause issues - 
a couple are:
Both interfaces get an address in the same subnet.
Gateway address points to wrong interface.

---

### Post by csharpplus on 2010-10-31
Hi lowan,

Thank you for your reply. Here's what I get when I type **ifconfig -a:**

```

eth0      Link encap:Ethernet  HWaddr 00:16:41:58:56:87  
          inet addr:192.168.0.253  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::216:41ff:fe58:5687/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:823 errors:0 dropped:0 overruns:0 frame:0
          TX packets:61 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:175739 (175.7 KB)  TX bytes:6285 (6.2 KB)
          Memory:ee000000-ee020000 

eth1      Link encap:Ethernet  HWaddr 10:13:51:a7:d0:ff  
          inet addr:192.168.0.253  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::1213:51ff:fea7:d0ff/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:36 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:354 (354.0 B)  TX bytes:5145 (5.1 KB)

irda0     Link encap:IrLAP  HWaddr 00:00:00:00  
          NOARP  MTU:2048  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:8 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:67 errors:0 dropped:0 overruns:0 frame:0
          TX packets:67 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5008 (5.0 KB)  TX bytes:5008 (5.0 KB)

pan0      Link encap:Ethernet  HWaddr 0e:1f:b3:5a:0d:fd  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:13:02:70:d9:09  
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::213:2ff:fe70:d909/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8711 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1649 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3430686 (3.4 MB)  TX bytes:247471 (247.4 KB)


```

I can also add that **192.168.0.253** is the static IP assigned to the 'native' RJ45 slot (this is the slot that belongs to the machine; a cable goes from there to the switch).

Is there any other info that can help solving this? (I will gladly post...). thanks!

---

### Post by Iowan on 2010-10-31
Having both interfaces with the *same* IP address is a problem. Is the "new" interface supposed to get a DHCP address - or did you assign the same address twice?

---

### Post by csharpplus on 2010-10-31
Yes, the "new" interface is supposed to get a DHCP address. I did not do anything except plugging-in the new 'interface' (USB device) that  exposes the new RJ45 slot.

What shall I do to fix this?

---

### Post by Iowan on 2010-10-31
If Network Manager doesn't already show the interface (it *should*, since it gets an IP address), verify that the interface isn't defined in */etc/network/interfaces*.  If it is, you might comment out the definition there. Otherwise, you should be able to create a new connection via Network Manager (Network connections?)

There may be more details (gateway, DNS) to fix - but first things first.

---

### Post by csharpplus on 2010-10-31
Thank you for your help.

Here is my interface file:
```

auto lo
iface lo inet loopback

```

I tried to create a new connection using Network Manager, but what info shall I specify there? If I don't specify anything, it does not seem to 'communicate' with the new device (nothing happens).

---

### Post by csharpplus on 2010-11-02
I am still trying to find a solution...any ideas how to solve this?

---

