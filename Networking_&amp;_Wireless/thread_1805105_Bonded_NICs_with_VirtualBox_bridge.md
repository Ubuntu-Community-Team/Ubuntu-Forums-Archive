---
title: "Bonded NICs with VirtualBox bridge"
date: 2011-07-15
forum: Networking &amp; Wireless
---

### Post by Vertigo_ on 2011-07-15
I've searched, and I really have, but haven't come up with any forums posts or google results on this issue. Perhaps I've been searching for the wrong thing, and I apologize if there is.

I've setup a Ubuntu 10.04 LTS box with 3 NICs bonded and VirtualBox 4.0.10 with a couple VM's bridged to bond0. The problem is, I'm getting spotty connections. I've tested the VM host to make sure the bonding is configured correctly and works(seems good) with no dropped packets. I have also removed the NetworkManager as per suggestion.

```
# The loopback network interface
auto lo
iface lo inet loopback

# Bonding for eth0 eth1 eth2
auto bond0
iface bond0 inet static
address 10.x.x.x
netmask 255.255.0.0
gateway 10.x.x.x
dns-nameservers 10.x.x.x
post-up ifenslave bond0 eth0 eth1 eth2
pre-down ifenslave -d bond0 eth0 eth1 eth2
```

I currently have 3 VM's I'm running to make sure I get it setup right. 2 are running Ubuntu 10.04 servers and the 3rd is running WinXP. The 2 *nix VMs are having massive packet loss, in the area of 80-90%. The XP VM is doing just fine, no packet loss and hasn't seemed to lock up at any point(yet). I've tried different adapters in VirtualBox for the network cards but it doesn't make a difference. It leads me to believe this is possibly a driver issue.

If it helps, the VMs are Zentyal 2.0.4 and a FOG .31 server. Any ideas where it's going wrong?

---

### Post by jmoorse on 2011-07-16
Just to make sure I understand:

Traffic to/from vm host via bond0 = great.  (Please provide output of 'sudo ping [Gateway IP] -c 1000 -f' from the host and from a vm guest)

Traffic to/from Windows Guest = great.

Traffic to/from *nix vm guests to same network = poor?  Can you provide output of pings from 1 vm guest to another?  Have you installed the vbox guest additions?

You don't need to x out 10. IP address space FYI.  Did you mean to use a /16 (255.255.0.0 mask?)

I apologize if some of the questions are a bit remedial, I know nothing of your linux/network skills.

---

### Post by Vertigo_ on 2011-07-18
The traffic to/from the Host is solid, having 0% packet loss(250,000 out of 250,000). 

Traffic to/from the XP Guest is nearly as good with only 2% loss(216,720 out of 221,554), having only 4,834 packets lost. 

Traffic from the two Ubuntu Guests is not good, with 82% and 85% loss.

*nix Guest #1: 83% loss(243,176 sent, 40,087 received)
rtt min/avg/max/mdev : 0.000/0.394/11.100/0.222 ms

*nix Guest #2: 85% loss(242,732 sent, 36,348 received)
rtt min/avg/max/mdev : 0.000/0.391/11.472/0.270 ms

I x'd out the numbers due to habit, and I did mean for a /16 subnet. I left the host/vm's to continue the ping since I left work Friday, and they were still active this morning(so at least none of them froze). Out of curiosity, what if I leave the binding to the VM's? I'm not sure I could get zentyal to play nice with that, but I may give it a try today.

---

### Post by Vertigo_ on 2011-07-18
> **jmoorse said:**
> 
Traffic to/from *nix vm guests to same network = poor?  Can you provide output of pings from 1 vm guest to another?  Have you installed the vbox guest additions?

You don't need to x out 10. IP address space FYI.  Did you mean to use a /16 (255.255.0.0 mask?)

I apologize if some of the questions are a bit remedial, I know nothing of your linux/network skills.

Obviously your questions were NOT too remedial... as it completely slipped my mind to ping guest to guest. Guest to guest ping is fine, no loss... guest to GW or network is not so fine. I have not installed the guest additions, and though it would be nice if that fixed it... I'm really hoping it won't solve anything or I wasted a day due to stupidity. Time to try it with the guest additions!

---

### Post by jmoorse on 2011-07-18
Even the 2% loss concerns me.

Does the ifconfig output on the linux guests show anything in RX/TX that is not under 'packets:' ?  What about the host?

Did you install the vbox guest additions?

I am not sure what you mean by:

> 
Out of curiosity, what if I leave the binding to the VM's? I'm not sure I could get zentyal to play nice with that, but I may give it a try today.


---

### Post by Vertigo_ on 2011-07-18
> **jmoorse said:**
> Even the 2% loss concerns me.

Does the ifconfig output on the linux guests show anything in RX/TX that is not under 'packets:' ?  What about the host?

Did you install the vbox guest additions?


I am really at a loss here.

I've installed the guest additions(as of today), and updated to the newest vbox(4.0.12). Now the packet drop is around 30-60% usually, on the *nix guests. The Host computer is running fine, and the XP guest is doing fine.

The guests are able to ping each other and even the host with 0 loss, but the GW or any other computer gets packet loss. If I disable the bonding, and bridge directly to a NIC the guest *nix system has no problem. Bridging to the bond0 interface causes them to start dropping packets. Also, there is nothing other than the RX/TX on the guest's interfaces. The host does have 'interrupt' listed after RX/TX on the slaves..


[QUOTE=jmoorse]I am not sure what you mean by:

[QUOTE=Vertigo_]
Out of curiosity, what if I leave the binding to the VM's? I'm not sure I could get zentyal to play nice with that, but I may give it a try today.[/QUOTE][/QUOTE]
My comment was a typo, I was talking about leaving the bonding to the guests, each virtual interface bridged to a different NIC. My guess would be that it would "work", but that is more of a work-around than a fix.

---

### Post by jmoorse on 2011-07-18
Fun stuff :)  Let's check a few more things.  Can you provide the output of ifconfig from the host and both guests?

Please install ethtool on the host + guests (sudo apt-get install ethtool) and provide the output of 
```

sudo ethtool [eth or bond interface]
sudo ethtool -i [eth or bond interface]

```

---

### Post by Vertigo_ on 2011-07-18
Host
```

Link detected: yes
driver: bonding
version: 3.5.0
firmware-version: 2
bus-info: 
**$ifconfig -a**
bond0     Link encap:Ethernet  HWaddr 00:19:db:49:d2:3f  
          inet addr:10.2.0.3  Bcast:10.2.255.255  Mask:255.255.0.0
          inet6 addr: fe80::219:dbff:fe49:d23f/64 Scope:Link
          UP BROADCAST RUNNING MASTER MULTICAST  MTU:1500  Metric:1
          RX packets:511 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1506 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:44143 (44.1 KB)  TX bytes:101215 (101.2 KB)

eth0      Link encap:Ethernet  HWaddr 00:10:5a:c8:17:12  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 Base address:0x4000 

eth1      Link encap:Ethernet  HWaddr 00:19:db:49:d2:3f  
          UP BROADCAST RUNNING SLAVE MULTICAST  MTU:1500  Metric:1
          RX packets:511 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1506 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:44143 (44.1 KB)  TX bytes:101215 (101.2 KB)
          Interrupt:27 

eth2      Link encap:Ethernet  HWaddr 00:50:04:ce:b9:b8  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:19 Base address:0x8400 

vboxnet0  Link encap:Ethernet  HWaddr 0a:00:27:00:00:00  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

Fog .31
```

**$ifconfig -a**
eth0      Link encap:Ethernet  HWaddr 08:00:27:2a:b8:f4  
          inet addr:10.2.0.10  Bcast:10.2.255.255  Mask:255.255.0.0
          inet6 addr: fe80::a00:27ff:fe2a:b8f4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:109 errors:0 dropped:0 overruns:0 frame:0
          TX packets:92 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:10837 (10.8 KB)  TX bytes:11886 (11.8 KB)

**$ethtool**
driver: e1000
version: 7.3.21-k5-NAPI
firmware-version: N/A
bus-info: 0000:00:03.0
Settings for eth0:
        Supported ports: [ TP ]
        Supported link modes:   10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
                                1000baseT/Full 
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
                                1000baseT/Full 
        Advertised pause frame use: No
        Advertised auto-negotiation: Yes
        Link partner advertised link modes:  Not reported
        Link partner advertised pause frame use: No
        Link partner advertised auto-negotiation: No
        Speed: 1000Mb/s
        Duplex: Full
        Port: Twisted Pair
        PHYAD: 0
        Transceiver: internal
        Auto-negotiation: on
        MDI-X: Unknown
        Supports Wake-on: umbg
        Wake-on: d
        Current message level: 0x00000007 (7)
        Link detected: yes

```

Zentyal
```

**$ifconfig -a**
eth0      Link encap:Ethernet  HWaddr 08:00:27:f8:32:31  
          inet addr:10.2.2.105  Bcast:10.2.255.255  Mask:255.255.0.0
          inet6 addr: fe80::a00:27ff:fef8:3231/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:630 errors:0 dropped:0 overruns:0 frame:0
          TX packets:220 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:55889 (55.8 KB)  TX bytes:28167 (28.1 KB)

driver: e1000
version: 7.3.21-k5-NAPI
firmware-version: N/A
bus-info: 0000:00:11.0

Settings for eth0:
        Supported ports: [ TP ]
        Supported link modes:   10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
                                1000baseT/Full 
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
                                1000baseT/Full 
        Advertised pause frame use: No
        Advertised auto-negotiation: Yes
        Link partner advertised link modes:  Not reported
        Link partner advertised pause frame use: No
        Link partner advertised auto-negotiation: No
        Speed: 1000Mb/s
        Duplex: Full
        Port: Twisted Pair
        PHYAD: 0
        Transceiver: internal
        Auto-negotiation: on
        MDI-X: Unknown
        Supports Wake-on: d
        Wake-on: d
        Current message level: 0x00000007 (7)
        Link detected: yes

```

---

### Post by jmoorse on 2011-07-18
Interesting.  Have the machines been rebooted since you last tried the ping tests?

It looks like the bond is in active / passive mode.  

Can you provide the output from the vm host of:
```

cat /proc/net/bonding/bond0

```

Am I correct in assuming this bond runs to your switch?  What model switch is it?

---

### Post by Vertigo_ on 2011-07-18
There IS a problem with my bonding. 

```
Ethernet Channel Bonding Driver: v3.5.0 (November 4, 2008)

Bonding Mode: adaptive load balancing
Primary Slave: None
Currently Active Slave: eth1
MII Status: up
MII Polling Interval (ms): 100
Up Delay (ms): 0
Down Delay (ms): 0

Slave Interface: eth1
MII Status: up
Link Failure Count: 0
Permanent HW addr: 00:19:db:49:d2:3f

```

Only one slave... I have two 3Com 905B NIC's with an onboard gigabit NIC. I was using mode 6(alb) bonding which the 3c59x driver/NIC is not able to handle. I looked at dmesg and found: 

```
[   15.323724] bonding: bond0: Error: dev_set_mac_address of dev eth2 failed! ALB mode requires that the base driver support setting the hw address also when the network device's interface is open

```

I also had to add lines to my interfaces config to make the the interfaces work right.

```
iface eth0 inet manual
iface eth1 inet manual
iface eth2 inet manual
``` 

I'm using HP ProCurve 2650 switches, and in order to save a little time opted for mode 6 rather than configure the switches for 802.3ad and mode 4 like I should have done in the first place. I really didn't want to have to try and figure out the old passwords on these switches or reset them.

I have another server in another building that I will test the bridge/bond on in the mean time to see if the faulty bonding on this server is perhaps a reason for the strange packet drop on the *nix guests. It still concerns me that the XP guest works perfectly while the *nix don't.

---

### Post by jmoorse on 2011-07-19
I am interested to see what the results are now that the bonding issue has been discovered.

---

