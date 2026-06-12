---
title: "Sporatic network connection"
date: 2011-04-08
forum: Networking &amp; Wireless
---

### Post by tiggyboo on 2011-04-08
My recent installation of 10.04 is showing really sporatic network connections.  I.e., connectivity just seems to come and go for a few hours at a time with no discernable pattern.  Hardware looks okay, at least in terms of activity/status lights.  I seem to be able to consistently reach the network on the box in question, and the outages seem to only come in the form of the box not being reachable from anywhere else on the network. In an effort to dig deeper I ran across several suggestions for generating diagnostic output, but for the most part I'm at a loss in terms of interpreting it.  I'm hoping someone will jump out at someone with a more experienced eye, and that they can point me in the right direction.  Thanks very much in advance to anyone taking the time to check this out!

box@obee:~$ [COLOR="Red"]sudo iptables -L[/COLOR]
[sudo] password for box:
WARNING: All config files need .conf: /etc/modprobe.d/blacklist-modem, it will b
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base, it will be igno
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination


box@obee:~$ [COLOR="Red"]ifconfig[/COLOR]eth0      Link encap:Ethernet  HWaddr 00:1c:23:b9:3a:96
          inet addr:172.23.100.121  Bcast:172.23.101.255  Mask:255.255.254.0
          inet6 addr: fe80::21c:23ff:feb9:3a96/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:807124 errors:0 dropped:0 overruns:0 frame:0
          TX packets:90366 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:134459075 (134.4 MB)  TX bytes:55016485 (55.0 MB)
          Interrupt:16 Memory:f4000000-f4012800

eth1      Link encap:Ethernet  HWaddr 00:1c:23:b9:3a:94
          inet addr:172.23.100.121  Bcast:172.23.101.255  Mask:255.255.254.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 Memory:f8000000-f8012800

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3095 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3095 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:745673 (745.6 KB)  TX bytes:745673 (745.6 KB)

box@obee:~$ [COLOR="Red"]sudo mii-tool -v[/COLOR][sudo] password for box:
eth0: negotiated 1000baseT-FD flow-control, link ok
  product info: vendor 00:08:18, model 54 rev 6
  basic mode:   autonegotiation enabled
  basic status: autonegotiation complete, link ok
  capabilities: 1000baseT-FD 100baseTx-FD 100baseTx-HD 10baseT-FD 10baseT-HD
  advertising:  1000baseT-FD 100baseTx-FD 100baseTx-HD 10baseT-FD 10baseT-HD flow-control
  link partner: 1000baseT-FD 100baseTx-FD 100baseTx-HD 10baseT-FD 10baseT-HD
eth1: no link
  product info: vendor 00:08:18, model 54 rev 6
  basic mode:   autonegotiation enabled
  basic status: no link
  capabilities: 1000baseT-FD 100baseTx-FD 100baseTx-HD 10baseT-FD 10baseT-HD
  advertising:  100baseTx-FD 100baseTx-HD 10baseT-FD 10baseT-HD flow-control

box@obee:~$ [COLOR="Red"]sudo ethtool -S eth0[/COLOR]NIC statistics:
     rx_bytes: 134654980
     rx_error_bytes: 0
     tx_bytes: 55033572
     tx_error_bytes: 0
     rx_ucast_packets: 102626
     rx_mcast_packets: 49132
     rx_bcast_packets: 657319
     tx_ucast_packets: 90327
     tx_mcast_packets: 41
     tx_bcast_packets: 126
     tx_mac_errors: 0
     tx_carrier_errors: 0
     rx_crc_errors: 0
     rx_align_errors: 0
     tx_single_collisions: 0
     tx_multi_collisions: 0
     tx_deferred: 0
     tx_excess_collisions: 0
     tx_late_collisions: 0
     tx_total_collisions: 0
     rx_fragments: 0
     rx_jabbers: 0
     rx_undersize_packets: 0
     rx_oversize_packets: 0
     rx_64_byte_packets: 446347
     rx_65_to_127_byte_packets: 192474
     rx_128_to_255_byte_packets: 115320
     rx_256_to_511_byte_packets: 13820
     rx_512_to_1023_byte_packets: 1660
     rx_1024_to_1522_byte_packets: 39456
     rx_1523_to_9022_byte_packets: 0
     tx_64_byte_packets: 5109
     tx_65_to_127_byte_packets: 36016
     tx_128_to_255_byte_packets: 9553
     tx_256_to_511_byte_packets: 4570
     tx_512_to_1023_byte_packets: 4194
     tx_1024_to_1522_byte_packets: 31052
     tx_1523_to_9022_byte_packets: 0
     rx_xon_frames: 0
     rx_xoff_frames: 0
     tx_xon_frames: 0
     tx_xoff_frames: 0
     rx_mac_ctrl_frames: 0
     rx_filtered_packets: 483891
     rx_ftq_discards: 0
     rx_discards: 0
     rx_fw_discards: 0
	 
box@obee:~$ [COLOR="Red"]sudo netstat -i[/COLOR]Kernel Interface table
Iface   MTU Met   RX-OK RX-ERR RX-DRP RX-OVR    TX-OK TX-ERR TX-DRP TX-OVR Flg
eth0       1500 0    809328      0      0 0         90545      0      0      0 BMRU
eth1       1500 0         0      0      0 0             0      0      0      0 BMU
lo        16436 0      3101      0      0 0          3101      0      0      0 LRU

---

### Post by dandnsmith on 2011-04-08
A quick glance suggests an obvious problem - you have two interfaces configured and up, both on IP address 172.23.100.121. This means the poosr system is totally confused about which to use and what to reply on. Come to think of it theres something odd about that broadcast address too!

---

### Post by tiggyboo on 2011-04-09
Thanks.  Figured I was missing the forrest for the trees somewhere along the line :-).  Assuming eth0 is the one to keep, when I do:

sudo ifdown eth1

I get:

ifdown: interface eth1 not configured

And looking in the network connections gui, eth1 is the only one that appears (before and after the ifdown.)

Any thoughts?  Is there a way to start from scratch with network configuration?

Thanks!
Al

---

### Post by tiggyboo on 2011-04-09
Found that eth1 had disappeared from my interfaces file somehow, yet it continued to show up in ifconfig.  ifconfig eth1 down seemed to do the trick in getting rid of it.

Yet, this happens when I restart networking:

sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...
SIOCADDRT: File exists
Failed to bring up eth0.
   ...done.

Although the network seems up...

Thanks,
Al

---

### Post by dandnsmith on 2011-04-09
I don't know any way of starting from scratch.
With my own setup I really do have 2 eth interfaces, only one of which works - added a card when the first stopped working.
I then had a problem as it was still trying to use the original (on the motherboard), so I removed its IP address using that GUI. After that I still had to do a bit of fiddling to add correct routing - but that was the basis, and you might try something similar.

There should be an interface(s) file, somewhere under /etc - but a quick hunt showed I'd lost track of it's location for the newer linux versions.

HTH

---

### Post by tiggyboo on 2011-04-09
Thanks Derek - yeah interaces is not in /etc/network. I think my problems stem mainly from doing some stuff from the command line and some via gui, resulting in some jumbled files :-).
Al

---

### Post by dandnsmith on 2011-04-10
In my /etc/network/interfaces is only bits pertaining to *lo* - nothing for *ethx*.
The man page for interfaces suggests you could 'ban' one of the interfaces if it isn't serving any purpose (my useless one is disabled in the gui interface}.
You could check the routes, using the *route* command, just to see whether stuff is being correctly routed.

Good luck

---

