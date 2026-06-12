---
title: "Static IP addresses not working in Ibex"
date: 2009-02-01
forum: Networking &amp; Wireless
---

### Post by thefutoneng on 2009-02-01
I have just upgraded to Ibex and I am not able to gain access to my local network.  I am using the same interfaces file that I used in gutsy with static addresses configured for two interfaces on two different networks.  All cables are secure, I see link lights on the switch (cisco 3560). At times, I do not see any MAC addresses being advertised by the host and there are never any ARP entries seen on the router.  The problem definitely is on the host.

/etc/network/interfaces
```

auto lo
iface lo inet loopback

iface eth0 inet static
address 192.168.2.10
netmask 255.255.255.0
gateway 192.168.2.241
up route del -net default gw 192.168.2.241

iface eth1 inet static
address 192.168.1.10
netmask 255.255.255.0
gateway 192.168.1.1

auto eth0

auto eth1

```

ifconfig -a
```

eth0      Link encap:Ethernet  HWaddr 00:0e:a6:f5:ee:7f  
          inet addr:192.168.2.10  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::20e:a6ff:fef5:ee7f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:1 dropped:0 overruns:0 frame:1
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:2232 (2.2 KB)
          Interrupt:218 Base address:0xa000 

eth1      Link encap:Ethernet  HWaddr 00:0e:a6:f5:f8:c7  
          inet addr:192.168.1.10  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20e:a6ff:fef5:f8c7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:30 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:5219 (5.2 KB)
          Interrupt:217 Base address:0xe000 

```

attempted restart
```

root@underwearless:~# /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                                                                                                         SIOCDELRT: No such process
 * if-up.d/mountnfs[eth0]: waiting for interface eth1 before doing NFS mounts

```

---

### Post by Iowan on 2009-02-01
Network manager has evolved between Gutsy (which I still run) and Intrepid.  [Here]("http://www.prash-babu.com/2009/01/how-to-setup-static-ip-in-ubuntu.html") is a How-To for Intrepid static IP address.  There's also a [workaround]("http://www.prash-babu.com/2009/01/how-to-setup-static-ip-in-ubuntu.html"). A final option is to un-install NM and install the old manager - [here]("http://ubuntuforums.org/showpost.php?p=6623406&postcount=10").

---

### Post by thefutoneng on 2009-02-02
Network Manager was configured exactly as the interfaces file depicted. Nevertheless, I attempted to disable network manager according to the the instructions on the thread below to no avail.  Now the statically configured addresses do not appear in the ifconfig output.  Running a networking restart simply returns [OK] without actually bringing up an interface. 

[http://ubuntuforums.org/showpost.php?p=6623406&postcount=10](http://ubuntuforums.org/showpost.php?p=6623406&postcount=10)

---

### Post by thefutoneng on 2009-02-02
Additionally when I attempt to launch nm-connection-editor as root and try to use DHCP, I get an error stating:

```

Updating connection failed: nm-ifupdown-connection.c.82- connection update not supported (read only)..

```

---

### Post by dmizer on 2009-02-02
If you disable nm, you can't use nm-connection-editor.

Assuming you have installed gnome-network-admin, you can configure your network under System > administration > network

---

### Post by thefutoneng on 2009-02-03
I understand  once Network Manager is disabled you can't use nm-connection-editor.  I performed the operations in a logical sequence.  Still no network connectivity.

---

### Post by thefutoneng on 2009-02-04
I got frustrated with Ibex and installed Hardy and I'm experiencing similar issues.  All connections are greyed out in network-admin.

---

### Post by Iowan on 2009-02-04
Start again by posting */etc/network/interfaces*.

---

### Post by dmizer on 2009-02-04
> **thefutoneng said:**
> I got frustrated with Ibex and installed Hardy and I'm experiencing similar issues.  All connections are greyed out in network-admin.

Did you try clicking on the "unlock" button?

---

### Post by thefutoneng on 2009-02-05
Interfaces file posted below.  Unable to ping the default gateway of each interface and drops are accumulating on both interfaces.  It looks like everything is configured properly but the machine is not able to actually put packets over the wire.  I see mac addresses being advertised on the switch but no ARP entry.

/etc/network/interfaces
```


auto lo
iface lo inet loopback


iface eth0 inet static
address 192.168.2.10
netmask 255.255.255.0
gateway 192.168.2.241

auto eth0

iface eth1 inet static
address 192.168.1.10
netmask 255.255.255.0
gateway 192.168.1.1

auto eth1

```

eth0 and eth1
```


eth0      Link encap:Ethernet  HWaddr 00:0e:a6:f5:ee:7f  
          inet addr:192.168.2.10  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::20e:a6ff:fef5:ee7f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:92 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:20771 (20.2 KB)
          Interrupt:218 Base address:0xc000 

eth1      Link encap:Ethernet  HWaddr 00:0e:a6:f5:f8:c7  
          inet addr:192.168.1.10  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20e:a6ff:fef5:f8c7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:135 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:31924 (31.1 KB)
          Interrupt:217 Base address:0x6000 

```

networking restart
```

 * Reconfiguring network interfaces...       [ OK ]
RTNETLINK answers: No such process

```

---

### Post by Iowan on 2009-02-05
Results of **lshw -C network**?

---

### Post by thefutoneng on 2009-02-06
From lshw, it looks like the OS is only able to see the wireless card but both of the ethernet interfaces show up in the output of dmesg.  I highly doubt it is the board, both NICs were functioning properly before upgrading to Ibex (I have since downgraded to Hardy).

lshw -C network
```

sudo lshw -C network
[sudo] password for rob: 
  *-network               
       description: Wireless interface
       physical id: 1
       logical name: wlan1
       serial: 00:15:af:0c:fb:3a
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

```

dmesg
```

sudo dmesg | grep eth
[   47.806014] forcedeth: Reverse Engineered nForce ethernet driver. Version 0.61.
[   48.326084] forcedeth 0000:00:11.0: ifname eth0, PHY OUI 0x5043 @ 1, addr 00:0e:a6:f5:ee:7f
[   48.326091] forcedeth 0000:00:11.0: highdma csum vlan pwrctl mgmt timirq gbit lnktim msi desc-v3
[   48.845145] forcedeth 0000:00:12.0: ifname eth1, PHY OUI 0x5043 @ 1, addr 00:0e:a6:f5:f8:c7
[   48.845150] forcedeth 0000:00:12.0: highdma csum vlan pwrctl mgmt timirq gbit lnktim msi desc-v3
[   50.316437] Driver 'sr' needs updating - please use bus_type methods
[   56.426386] Driver 'sd' needs updating - please use bus_type methods
[  137.296909] eth1: no IPv6 routers present
[  137.808131] eth0: no IPv6 routers present
[  679.830751] eth0: no IPv6 routers present
[  774.518563] eth0: no IPv6 routers present
[ 1087.447045] eth1: no IPv6 routers present
[ 1329.297756] eth0: no IPv6 routers present
[ 1329.417575] eth1: no IPv6 routers present
[ 3215.365697] eth1: no IPv6 routers present
[ 3215.713169] eth0: no IPv6 routers present
[ 3235.479068] eth1: no IPv6 routers present
[ 3236.051198] eth0: no IPv6 routers present
[13015.267632] NETDEV WATCHDOG: eth0: transmit timed out
[13015.267638] eth0: Got tx_timeout. irq: 00000036
[13015.267640] eth0: Ring at 37068000
[13015.267642] eth0: Dumping tx registers
[13015.268086] eth0: Dumping tx ring
[26015.470226] NETDEV WATCHDOG: eth0: transmit timed out
[26015.470232] eth0: Got tx_timeout. irq: 00000036
[26015.470234] eth0: Ring at 37068000
[26015.470235] eth0: Dumping tx registers
[26015.470683] eth0: Dumping tx ring

```

---

### Post by thefutoneng on 2009-02-08
I configured two DHCP pools on the Cisco switch that my machine connects to to see if my computer could get network connectivity that way.  Both ethernet interfaces were unable to get a lease and were assigned link local addresses. 

If you look at the MAC addresses in the previous ifconfig's posted, they match the MACs in the DHCP binding output.  The DHCPDISCOVER packets sent by the host were seen and responded to by the switch with offers but the host seems to have disregarded them.
```

jc300c02-usrs01#show ip dhcp server  statistics 
Memory usage         6017
Address pools        2
Database agents      0
Automatic bindings   2
Manual bindings      0
Expired bindings     6
Malformed messages   0

Message              Received
BOOTREQUEST          0
DHCPDISCOVER         176
DHCPREQUEST          7
DHCPDECLINE          0
DHCPRELEASE          0
DHCPINFORM           17

Message              Sent
BOOTREPLY            0
DHCPOFFER            113
DHCPACK              1
DHCPNAK              0

jc300c02-usrs01#show ip dhcp binding 
IP address       Client-ID/              Lease expiration        Type
                 Hardware address
192.168.1.2      000e.a6f5.f8c7          Mar 21 1993 12:13 AM    Automatic
192.168.2.8      000e.a6f5.ee7f          Mar 21 1993 12:14 AM    Automatic


```

ifconfig after both eth0 and eth1 were configured for DHCP and networking restart was run.
```

eth0      Link encap:Ethernet  HWaddr 00:0e:a6:f5:ee:7f  
          inet6 addr: fe80::20e:a6ff:fef5:ee7f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:110 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:26455 (25.8 KB)
          Interrupt:217 Base address:0xe000 

eth1      Link encap:Ethernet  HWaddr 00:0e:a6:f5:f8:c7  
          inet6 addr: fe80::20e:a6ff:fef5:f8c7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:372 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:50056 (48.8 KB)
          Interrupt:218 

```

I read an article that I can no longer find that stated one of the alpha releases of Ibex rendered all ethernet interfaces permanently unusable because of some firmware changes it made if static address were configured.  I hope that bug has been addressed, can anyone confirm they are using static addresses in Ibex successfully?

---

### Post by FishRCynic on 2009-02-08
auto lo
iface lo inet loopback


iface eth0 inet static
address 192.168.2.10
netmask 255.255.255.0
gateway 192.168.2.241

auto eth0

iface eth1 inet static
address 192.168.1.10
netmask 255.255.255.0
gateway 192.168.1.1

auto eth1


what happens when/if you delete the auto eth0 and auto eth1 from the file?

or move them under auto lo?

another thought
have you been here?
[http://www.ubuntugeek.com/ubuntu-networking-configuration-using-command-line.html](http://www.ubuntugeek.com/ubuntu-networking-configuration-using-command-line.html)

or

[http://www.ubuntugeek.com/how-to-set-a-static-ip-address-in-ubuntu-810-intrepid-ibex.html](http://www.ubuntugeek.com/how-to-set-a-static-ip-address-in-ubuntu-810-intrepid-ibex.html)

---

### Post by thefutoneng on 2009-02-10
I have tried all variations of the interfaces file as far as the position of the "auto" statements is concerned.  I am no longer running Ibex, I installed Hardy and still not able to get network connectivity.

---

### Post by thefutoneng on 2009-02-14
I figured out that I was hitting this [HTML]<a href=https://bugs.launchpad.net/ubuntu/+source/linux/+bug/136836>bug</a>[/HTML] which affects Nvidia mcp55 ethernet cards.

In order to fix this, I updated /etc/modprobe.d/options with the following line:

options forcedeth msi=0 msix=0

and then ran:

sudo update-initramfs -u

and rebooted and my network connectivity was restored.  Thanks everyone for your help.

---

