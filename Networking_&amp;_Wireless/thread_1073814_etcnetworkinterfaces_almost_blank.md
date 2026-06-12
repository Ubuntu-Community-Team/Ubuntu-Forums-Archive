---
title: "/etc/network/interfaces almost blank"
date: 2009-02-18
forum: Networking &amp; Wireless
---

### Post by smc18 on 2009-02-18
Hi,

To begin with this isn't causing any problems but is just making my wonder about a few things. 

In my interfaces file I only get the following:

> auto lo
iface lo inet loopback

I have used network connection to setup a static ip on my eth0 interface and wlan0 on my wireless card (which worked without any additional drivers, thank goodness!)

But since I have specified what settings I wanted, shouldn't the settings be saved in that interfaces config file?  If not, where?  Forgive if I'm wrong and please correct me, just curious.

Thanks!!

---

### Post by cariboo on 2009-02-18
If setting a static ip address I get rid of network-manger-gnome and install network-manager-admin, this basically reverts back to the Hardy network manager, which is much more static ip address friendly.

Jim

---

### Post by smc18 on 2009-02-18
Thanks for the suggestion :) I was having problems with 8.1 at first because it would not save my settings,  But to keep a story short, another user posted up a little howto make it save your config (using the gui), and it worked for me, without having to change my network manager.

Im not actually having any problems now, it's just that my /etc/network/interfaces config file seems like it's missing some stuff lol.

here is a sample I found online

> iface eth0 inet static
             address 192.168.0.111
             netmask 255.255.255.0
             gateway 192.168.0.1

my */etc/network/interfaces* only shows:

> auto lo
iface lo inet loopback 

Since I have eth0 and wlan0 interfaces, shouldn't their config be included in the file?

Just a little reminder that I'm not actually have any problems connecting with a static ip on eth0 or with my wireless (wlan0 - using dhcp)

---

### Post by smc18 on 2009-02-18
Does anyone have any other ideas?

---

### Post by pdtpatrick on 2009-02-18
Does the computer currently have internet? run the output of 

sudo /sbin/ifconfig

if you have an ip and you using dhcp then your /etc/network/interfaces should look like this:

> auto lo
iface eth0 inet dhcp

---

### Post by smc18 on 2009-02-18
```
ifconfig
```

> eth0      Link encap:Ethernet  HWaddr 00:1d:09:b8:36:ec  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:9ff:feb8:36ec/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:416168 errors:0 dropped:0 overruns:0 frame:0
          TX packets:291262 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:376075475 (376.0 MB)  TX bytes:98995361 (98.9 MB)
          Interrupt:17 

eth1      Link encap:Ethernet  HWaddr 00:1f:3a:43:d1:b9  
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:3aff:fe43:d1b9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:16364 errors:0 dropped:0 overruns:0 frame:33798
          TX packets:12654 errors:13 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:14654023 (14.6 MB)  TX bytes:3041840 (3.0 MB)
          Interrupt:17 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:18 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1272 (1.2 KB)  TX bytes:1272 (1.2 KB)


I used the network manager to statically assign an IP address to eth0 - my wired connection.
eth1 is my wireless interface and that's getting an IP address via DHCP.

I can connect to the Internet, that's not my problem :) .  Im just curious as to where the settings are stored on the filesystem for my own curiosity.

---

### Post by Iowan on 2009-02-18
I don't have Intrepid installed, but I've read that Network Manager stores its settings in /etc/NetworkManager (spelling and/or capitalization may be different).  What little research I've done suggests there may be several files under that directory.

---

### Post by smc18 on 2009-02-18
thanks :) Found my config for my eth0 interface

```
sudo cat /etc/NetworkManager/system-connections/eth0
```

> [connection]
id=eth0
uuid=xxxxxxxxxxxxxxxxxxxxxxx
type=802-3-ethernet
autoconnect=true
timestamp=0

[802-3-ethernet]
speed=0
duplex=full
auto-negotiate=true
mac-address=xxxxxxxxxxxxxxxxxx
mtu=0

[ipv4]
method=manual
dns=192.168.1.1;
addresses1=192.168.1.100;24;192.168.1.1;
ignore-auto-routes=false
ignore-auto-dns=false

However, eth1 isn't listed but that has a dynamic ip so it may be expected for it not to show up here.

I think I'm satisfied for now. :D

---

