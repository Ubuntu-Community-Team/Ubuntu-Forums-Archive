---
title: "getting remote frontend to work (Networking)"
date: 2010-07-13
forum: Mythbuntu
---

### Post by bance on 2010-07-13
Hi guys,

I've finally managed to get myth-buntu to work on my combined fornt/backend machine! :D

Now I want to connect a remote frontend, the problem I have is that I don't have an internet connection at the moment. I do have a 4 port switch and a 4 port broadband router, I hope this hardware is enough to set up a LAN.

Ok, so because there is no internet connection, mythbuntu doesn't recognise 'etho 0' and tells me there is no network connection.

Question is, can anyone point me to a simple guide as to how to get this working......  all searches so far concern internet connection problems, and I haven't found anything with regards to a simple LAN.

I have cat5/5e iinstalled to all locations.

TIA, Steve.

---

### Post by ian dobson on 2010-07-13
Hi,

You don't need an internet connection to get a lan working.

What do you see when you do the following from a terminal window:-

ifconfig

then
lspci

Does the system see the eth port, but not get a IP address. Normally the router hands out local (lan valid) ip addresses.

Regards
Ian Dobson

---

### Post by SnafuFlux on 2010-07-13
> **bance said:**
> the problem I have is that I don't have an internet connection at the moment. 
How did you make this post then?  ;)

---

### Post by bance on 2010-07-13
@ Ian  :-      Will post output tomorrow when am at relevant machine....    am at home with IC at the mo.

@SnafuFlux     See above ;)

@Ian :-       When I last got everything working , I used the router hoping to test the frontend, set IP adressess etc in frontend set-up , but got some error messages regarding 'etho0 up' & 'etho0 down' repetitively not sure if this might be a hardware issue?

I have also tried an ethernet crossover cable but I wasn't sure about settings...      tried> 'network connections'> , select 'etho0',> 'edit',> IPV4 tab, >method > link 'local only' .... but no joy!

Am sorry bit of a noob, but I've done my best to research this issue, thank's for replying. ](*,)

---

### Post by laffinet on 2010-07-13
You need to connect both machines to the router. If your network adapters are working properly and are configured (network manager should take care of that) you should be able to connect both machines.

First thing is to find out the IP for each machine (you should set static IPs for both machines down the track, will make things a lot easier).

To find out your current IP run:
```
ifconfig
```
from a terminal. This will return something like this:
```
eth0 Link encap:Ethernet HWaddr 00:0A:E4:35:36:75
**inet addr:192.168.2.101 **Bcast:192.168.2.255 Mask:255.255.255.0
inet6 addr: fe80::20a:e4ff:fe35:3675/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:1478755 errors:0 dropped:0 overruns:0 frame:0
TX packets:1769877 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:740589340 (706.2 MiB) TX bytes:1385358580 (1.2 GiB)

```
Your IP address is the "indet addr:" bit.
Now try:
```
ping *insertIPaddress*
```
If it returns something like this:
```
Reply from 72.3.133.152: bytes=32 time=69ms TTL=47

```
both machines can see each other.

Let us know how you go.

---

### Post by bance on 2010-07-14
Hi guys,

OK, I've issued 'ifconfig' in terminal, and output for backend is fine inet address etc. all shows up and a connection is made.

However in the frontend machine the entire second line is missing i.e. no inet address. So I suppose I'm going to have to set one!

A googling we shall go!!!:rolleyes:

---

### Post by ian dobson on 2010-07-14
Hi,

You can manually edit the network configuration in the /etc/networks/interface file.

If you issue a lspci from the terminal, do you see your network listed?

Regards
Ian Dobson

---

### Post by bance on 2010-07-14
OK,  got an address for the missing line as per the above post by using

```
ifconfig eth0 192.168.10.3 up
```/etc/network/interfaces lokks like this :-

auto lo
iface lo inet loopback


frontend ifconfig reads :-

```
eth0      Link encap:Ethernet  HWaddr e0:cb:4e:06:25:7f  
          inet6 addr: fe80::e2cb:4eff:fe06:257f/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:20 errors:0 dropped:0 overruns:0 frame:0
          TX packets:544 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2273 (2.2 KB)  TX bytes:178870 (178.8 KB)
          Interrupt:21 Base address:0xc000 



lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:216 errors:0 dropped:0 overruns:0 frame:0
          TX packets:216 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:16200 (16.2 KB)  TX bytes:16200 (16.2 KB)
```frontend lspci reads like this :-


```
00:00.0 Host bridge: nVidia Corporation MCP79 Host Bridge (rev b1)
00:00.1 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.0 ISA bridge: nVidia Corporation MCP79 LPC Bridge (rev b2)
00:03.1 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.2 SMBus: nVidia Corporation MCP79 SMBus (rev b1)
00:03.3 RAM memory: nVidia Corporation MCP79 Memory Controller (rev b1)
00:03.5 Co-processor: nVidia Corporation MCP79 Co-processor (rev b1)
00:04.0 USB Controller: nVidia Corporation MCP79 OHCI USB 1.1 Controller (rev b1)
00:04.1 USB Controller: nVidia Corporation MCP79 EHCI USB 2.0 Controller (rev b1)
00:08.0 Audio device: nVidia Corporation MCP79 High Definition Audio (rev b1)
00:09.0 PCI bridge: nVidia Corporation MCP79 PCI Bridge (rev b1)
00:0a.0 Ethernet controller: nVidia Corporation MCP79 Ethernet (rev b1)
00:0b.0 IDE interface: nVidia Corporation MCP79 SATA Controller (rev b1)
00:10.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
00:15.0 PCI bridge: nVidia Corporation MCP79 PCI Express Bridge (rev b1)
01:00.0 VGA compatible controller: nVidia Corporation ION VGA (rev b1)
02:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
```

frontend dmesg reads something like :-

677866 eth0 up
456456 eth0 down

repetitively,

Any ideas?

---

### Post by klc5555 on 2010-07-14
Just use the Network Manager on the desktop of the Frontend machine to set a static (fixed) ip address and netmask for the "wired connection" eth0. The netmask must be the same as it is on the Backend machine, and both should be 255.255.255.0 for a plain vanilla class "C" network. If the address on the backend is 192.168.10.3 then use something like 192.168.10.4 for the frontend (or anything 192.168.10.x between 1 and 255, except for the "3" your backend is on and whatever address the router may be using) 

Entire process shouldn't take but 5 minutes.

---

### Post by bance on 2010-07-16
Thanks for all the replies,

I've solved this now...... turns out I had some dodgy rj45 connections.:oops:

---

