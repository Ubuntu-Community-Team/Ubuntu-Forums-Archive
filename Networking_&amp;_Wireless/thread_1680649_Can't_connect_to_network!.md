---
title: "Can't connect to network!"
date: 2011-02-02
forum: Networking &amp; Wireless
---

### Post by scarypajamas on 2011-02-02
I have a Linksys AE1000 wireless adapter and I used the post found [here]("http://www.fedoraforum.org/forum/showthread.php?t=244215") to install the drivers.

I've figure I installed the drivers successfully because when I use "iwlist ra0 scan" I get a listing of available networks.  The problem is, I can only connect to unsecured networks.  For instance,

```
sudo iwconfig ra0 essid "unsecure network"
```
The above command connects me but the one below doesn't
```
sudo iwconfig ra0 essid "secure network" key s:mykey
```

Another problem is that even if I connect to the unsecured network, "ping www.google.com" returns me:  "ping: unknown host www.google.com"

Any thoughts?

The output of "ifconfig"
```

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:9 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:832 (832.0 B)  TX bytes:832 (832.0 B)

ra0       Link encap:Ethernet  HWaddr 68:7f:74:ef:76:dc  
          inet6 addr: fe80::6a7f:74ff:feef:76dc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6288 errors:0 dropped:0 overruns:0 frame:0
          TX packets:127 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1223285 (1.2 MB)  TX bytes:10784 (10.7 KB)

```



The output of "iwconfig"
```

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

ra0       Ralink STA  ESSID:"linksys"  Nickname:"RT3572STA"
          Mode:Managed  Frequency=2.437 GHz  Access Point: 00:18:39:B4:EA:AF   
          Bit Rate=1 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=46/100  Signal level:-89 dBm  Noise level:-89 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```



The contents of "/etc/network/interfaces"
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# My network interface
auto ra0
iface ra0 inet static
	address 192.168.1.3
	netmask 255.255.255.0
	gateway 192.168.1.254

```

---

### Post by AlecJ on 2011-02-02
Why have got these set?

iface ra0 inet static
    address 192.168.1.3
    netmask 255.255.255.0
    gateway 192.168.1.254

[FONT=monospace]should be set for DCHP?

[/FONT]iface ra0 inet [FONT=monospace]DCHP[/FONT]

---

### Post by scarypajamas on 2011-02-02
> **AlecJ said:**
> Why have got these set?

iface ra0 inet static
    address 192.168.1.3
    netmask 255.255.255.0
    gateway 192.168.1.254

[FONT=monospace]should be set for DCHP?

[/FONT]iface ra0 inet [FONT=monospace]DCHP[/FONT]

Well, I'm trying to set this up on a server so I want to use a static IP.  Is there something I have to do with my router to tell it that I want to use 192.168.1.3?  I'm using a linksys router.

---

