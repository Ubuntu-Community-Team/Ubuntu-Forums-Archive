---
title: "Internet Speed Problem"
date: 2009-04-07
forum: Networking &amp; Wireless
---

### Post by PewPewP on 2009-04-07
Hi all,

I'm using Ibex and I seem to be having issues with my internet speed. I (should) have about 6mbs download, still only get about 1mbs tops even though other terminals on the same network get 6mbs. The upload on the other hand doesn't seem affected as of now. 

What strikes me as odd on the whole situation is that when the download speed hits 70/90 kbs the whole network acts as if it were downloading at 700kbs (read: everything halts to a stop). This, and the fact that after leaving the computer on overnight downloading two 1Gb files led to the Network Manager indicating that had downloaded 2.8Gb even though both of the files had barely gone over 10% completion each (aka NM says 2.8Gb were downloaded, even though only 0.2Gb were actually downloaded) 

I've already shut down ipv6 as suggested pretty much everywhere else on the forum. 

I'm using: Wireless (8198 Realtek Semiconductor Corp.) on a fresh install of Ubuntu 8.10 

Thanks in advance for any help

---

### Post by jigsaws on 2009-04-07
If wifi signal strength is ok:

Try to check you network by ping and iptraf.
Then check your MTU, try to turn off tcp window scaling, adjust windows sizes.

---

### Post by PewPewP on 2009-04-07
> **jigsaws said:**
> If wifi signal strength is ok:

Try to check you network by ping and iptraf.
Then check your MTU, try to turn off tcp window scaling, adjust windows sizes.

Wifi strenght is about 70/80%

Ping:

```
-----@--------:~$ ping -c 4 www.google.com
PING www.l.google.com (72.14.221.147) 56(84) bytes of data.
64 bytes from fg-in-f147.google.com (72.14.221.147): icmp_seq=1 ttl=242 time=80.1 ms
64 bytes from fg-in-f147.google.com (72.14.221.147): icmp_seq=2 ttl=242 time=77.7 ms
64 bytes from fg-in-f147.google.com (72.14.221.147): icmp_seq=3 ttl=242 time=79.8 ms
64 bytes from fg-in-f147.google.com (72.14.221.147): icmp_seq=4 ttl=242 time=78.6 ms

--- www.l.google.com ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3011ms
rtt min/avg/max/mdev = 77.712/79.089/80.132/0.960 ms

```

(trimmed) output of ifconfig -a:

```
wlan1     Link encap:Ethernet  HWaddr 00:21:63:8e:62:31  
          inet addr:192.168.11.5  Bcast:192.168.11.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2740878 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2596248 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3126980507 (3.1 GB)  TX bytes:381507638 (381.5 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-21-63-8E-62-31-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

Setting TCP Window Scale now.

Edit:

Set TCP Window Scale off by editing /etc/sysctl.conf and uncommenting "net.ipv4.tcp_syncookies=1". This didn't change anything though...
Another detail I forgot to mention, when the computer starts, the speed is somewhat greater and then declines to the above values.

Edit 2:

Followed this guide: [http://onlyubuntu.blogspot.com/2008/07/how-to-optimize-your-internet.html](http://onlyubuntu.blogspot.com/2008/07/how-to-optimize-your-internet.html)
To set the new TCP Window Scale values. Nothing so far...

Thanks for the reply

---

### Post by PewPewP on 2009-04-07
Maybe it has something to do with this:

```

-----@--------:~$ sudo lshw -C net
[sudo] password for -----: 
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 02
       serial: 00:1e:33:79:2e:c0
       size: 10MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no module=r8169 multicast=yes port=MII speed=10MB/s
  *-network:0
       description: Wireless interface
       physical id: 1
       logical name: wlan1
       serial: 00:21:63:8e:62:31
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.11.5 multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 36:9e:41:bb:77:db
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

```

Anyone with experience on this wireless device (8198 Realtek Semiconductor Corp.) can tell me if this information is accurate? I'm starting to wonder if this has more to do with drivers than TCP definitions...

---

