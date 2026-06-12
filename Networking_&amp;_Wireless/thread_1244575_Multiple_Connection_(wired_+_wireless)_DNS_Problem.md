---
title: "Multiple Connection (wired + wireless) DNS Problem"
date: 2009-08-19
forum: Networking &amp; Wireless
---

### Post by darkpaladin79 on 2009-08-19
Alright, I've got a problem which I think is unique, so I hope I'm not wasting anyone's time.

Here's the problem. Yesterday, I ran into the problem with the rt73 module that it won't connect to a hidden ssid. I tried switching to wicd, but that didn't help either. Getting rid of any network managers and doing everything manually finally got me connected. The problem is, I can't seem to get dns working. Here's some information on my machine:

Card: Edimax 7138USG

lsusb:
```
ID 148f:2573 Ralink Technology, Corp. RT2501USB Wireless Adapter
```

lsmod:
```
rt73                  224640  1
```
Note: This is the driver I got somewhere on these forums which is patched for injection. I couldn't connect to a hidden ssid at all with the default driver. I know I can do this, since I did it in backtrack with this same card.

iwlist rausb0 scanning:
```
rausb0    Scan completed :
          Cell 01 - Address: 00:0F:B5:6A:D4:6A
                    ESSID:"NETGEAR"
                    Mode:Managed
                    Channel:11
                    Encryption key:on
                    Bit Rates:0 kb/s
          Cell 02 - Address: 00:18:39:EA:7E:8A
                    ESSID:"HOMENETWORK"
                    Mode:Managed
                    Channel:1
                    Encryption key:on
                    Bit Rates:0 kb/s
```

Note: When I'm not connected, the essid for "NETGEAR" (the network I want) comes up blank since it is not broadcasted. I'm connected right now.

lsb_release -d
```
Ubuntu 9.04
```

uname -mr
```
2.6.28-15-generic i686
```

Both the wired and wireless are set up with static dns:
ifconfig:

```
eth0      Link encap:Ethernet  HWaddr 00:16:e6:d3:f7:1a  
          inet addr:192.168.1.103  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:e6ff:fed3:f71a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:27937 errors:0 dropped:0 overruns:0 frame:0
          TX packets:19938 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:32408519 (32.4 MB)  TX bytes:2754322 (2.7 MB)
          Interrupt:16 

rausb0    Link encap:Ethernet  HWaddr 00:0e:2e:cf:a7:f8  
          inet addr:192.168.1.111  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20e:2eff:fecf:a7f8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:22860 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3099 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2086905 (2.0 MB)  TX bytes:274538 (274.5 KB)

```

Here's what it looks like when I'm connected to the wireless network:
iwconfig
```
rausb0    RT73 WLAN  ESSID:"NETGEAR"  
          Mode:Managed  Frequency=2.462 GHz  Access Point: 00:0F:B5:6A:D4:6A   
          Bit Rate=5.5 Mb/s   
          RTS thr:off   Fragment thr:off
          Link Quality=36/100  Signal level:-86 dBm  Noise level:-143 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```


The odd thing is that my dns works fine on my wired connection. My /etc/resolv.conf looks like this:
```
nameserver 208.67.222.222
nameserver 208.67.220.220
```

And for good measure, here's my /etc/network/interfaces:
```
auto lo
iface lo inet loopback
iface eth0 inet static
address 192.168.1.103
netmask 255.255.255.0
gateway 192.168.1.1

iface rausb0 inet static
address 192.168.1.111
netmask 255.255.255.0
gateway 192.168.1.1
```

When I drop my wired connection, I can still ping my router on the wireless, but I can't ping a regular address. Also, if I drop my wired connection, I normally can't get it back up unless I reinstall wicd and connect again. It seems like wicd is setting my dns in some other fashion which I'm missing. Any ideas?

---

### Post by Iowan on 2009-08-19
Check **route -n**. It's probably a bit confused having both interfaces in the same subnet.  The default gateway may be set only for eth0.

---

### Post by darkpaladin79 on 2009-08-20
This is what route -n yields for me:

```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 rausb0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
```

So do I need to add a new route? I'm not really a networking buff, so this doesn't make a whole lot of sense to me.

Edit: Now I'm thinking I would need to change the subnet of my router (I'm trying to bridge my wired network and my friend's wireless network), and then everything would be happy? I guess having two devices looking for a router at 192.168.1.1 will mess things up. I'm going to give that a shot.

---

### Post by darkpaladin79 on 2009-08-20
Alright, I know I shouldn't double post, but I fixed my problem. I had to change my router to a different gateway and subnet. Then, I made my wired connection the default gateway. So, my route -n looks like this now:
```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 rausb0
192.162.0.0     0.0.0.0         255.255.0.0     U     0      0        0 eth0
0.0.0.0         192.162.1.1     0.0.0.0         UG    0      0        0 eth0

```

When I need to switch all traffic over to the wireless connection, I simply switch the default gateway to the other connection to end up with this:

```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     0      0        0 rausb0
192.162.0.0     0.0.0.0         255.255.0.0     U     0      0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 rausb0
```


I'm really happy with this solution, thanks for pointing me in the right direction.

---

### Post by Iowan on 2009-08-20
Thanks for posting results. It's good to share success...

---

