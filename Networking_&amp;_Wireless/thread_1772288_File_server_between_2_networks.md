---
title: "File server between 2 networks"
date: 2011-05-31
forum: Networking &amp; Wireless
---

### Post by sean13128 on 2011-05-31
(Fairly new Ubuntu user)

I have a Desktop with 2 network cards and a file share. 

I currently have eth0 configured and working on a network hosing about 30 people.

Now I have another 50-60 people connected on a separate network that want to be tied into the same file share. 

I have configured both eth0 and eth1 for the networks that they are connected on. currently only eth0 works.

When I configured eth1 for some reason It shows that it was last used "never".





Is there a way to keep these networks separate and share these files from this server?



eth0      Link encap:Ethernet  HWaddr 00:1c:c0:fb:b4:20  
          inet addr:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21c:c0ff:fefb:b420/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2279973 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5550502 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:174376653 (174.3 MB)  TX bytes:7945227940 (7.9 GB)
          Interrupt:20 Memory:e3100000-e3120000 

eth1      Link encap:Ethernet  HWaddr 00:1b:21:ab:4d:b1  
          inet addr:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:21ff:feab:4db1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:35 errors:0 dropped:0 overruns:0 frame:0
          TX packets:77 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2866 (2.8 KB)  TX bytes:13543 (13.5 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:6925 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6925 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:590239 (590.2 KB)  TX bytes:590239 (590.2 KB)



edit: I realise it shows the same IP addresses for each interface in ifconfig, but I have them manualy assigned through the GUI.

---

### Post by Iowan on 2011-05-31
> **sean13128 said:**
> 
edit: I realise it shows the same IP addresses for each interface in ifconfig, but I have them manualy assigned through the GUI.**ifconfig** *should* show what the machine is using. What do you have configured via GUI?

---

### Post by sean13128 on 2011-06-01
I have 

Eth0 192.168.0.2 255.255.255.0
ETH1 192.168.1.2 255.255.255.0

I configured this in the GUI but only Eth0 works. Eth1 shows as never used.

if it helps I have 10.10 x64

I tried configuring \etc\network\interfaces to add eth1 and eth2 as static. It seemed to work as both connections showed in use and working but all pings returned unreachable.

---

### Post by SeijiSensei on 2011-06-01
Let's see what happens if you do everything manually to begin with.

```

sudo ifconfig eth0 down
sudo ifconfig eth1 down
sudo ifconfig eth0 192.168.0.2 netmask 255.255.255.0 broadcast 192.168.0.255
sudo ifconfig eth1 192.168.1.1 netmask 255.255.255.0 broadcast 192.168.1.255
ifconfig

```

Now what does it show?  What do you get by running "route -n"?  Can you ping machines in both networks?  If the IP address assignments are correct, but you can't ping both networks, I'd look into connectivity issues.

Stay away from GUIs when doing things like this.  If everything works correctly with this configuration, then create an /etc/network/interfaces to be consistent with these addresses:

```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.0.2
netmask 255.255.255.0

auto eth1
iface eth1 inet static
address 192.168.1.1
netmask 255.255.255.0

```

If you need to go outside your network from this machine (e.g., to reach the Internet), the interface connected to the network with the external router needs an additional "gateway" directive like "gateway 192.168.0.1" with the address of the router that connects to the outside.

---

### Post by garycahill on 2011-06-01
Quite a few firewalling settings stop pings. Try and switch off ufw (briefly!) or iptables to test pings first.

---

### Post by sean13128 on 2011-06-01
> **SeijiSensei said:**
> Let's see what happens if you do everything manually to begin with.

```

sudo ifconfig eth0 down
sudo ifconfig eth1 down
sudo ifconfig eth0 192.168.0.2 netmask 255.255.255.0 broadcast 192.168.0.255
sudo ifconfig eth1 192.168.1.1 netmask 255.255.255.0 broadcast 192.168.1.255
ifconfig

```

Now what does it show?  What do you get by running "route -n"?  Can you ping machines in both networks?  If the IP address assignments are correct, but you can't ping both networks, I'd look into connectivity issues.

Stay away from GUIs when doing things like this.  If everything works correctly with this configuration, then create an /etc/network/interfaces to be consistent with these addresses:

```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.0.2
netmask 255.255.255.0

auto eth1
iface eth1 inet static
address 192.168.1.1
netmask 255.255.255.0

```

If you need to go outside your network from this machine (e.g., to reach the Internet), the interface connected to the network with the external router needs an additional "gateway" directive like "gateway 192.168.0.1" with the address of the router that connects to the outside.


for some stupid reason I put 192.168.1.1 instead of .2 but I did what you said and updated my interfaces file, no dice yet.


output of route -n is something like

kernel ip routing table
destination
192.168.1.0
192.168.0.0
169.254.0.0
0.0.0.0

Gateway
0.0.0.0
0.0.0.0
0.0.0.0
192.168.0.1

genmask
255.255.255.0
255.255.255.0
255.255.0.0
0.0.0.0

flags
u
u
u
ug

metric
0
1
1000
0

ref
0
0
0
0

use
0
0
0
0

iface 
eth1
eth0
eth0
eth0



pings to everything through eth0 work fine, pinging anything on the eth1 side returns unreachable.

---

