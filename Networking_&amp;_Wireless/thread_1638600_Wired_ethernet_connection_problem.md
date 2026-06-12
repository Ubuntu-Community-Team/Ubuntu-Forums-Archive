---
title: "Wired ethernet connection problem"
date: 2010-12-05
forum: Networking &amp; Wireless
---

### Post by yvickers on 2010-12-05
I have just installed ubuntu 10.04 using the wubi installer to dual-boot my machine.  Under ubuntu, I am not able to connect to the internet or my router.  Everything works fine under windows.  I have tried to find relevant information in the forums, but nothing seems to work for me.  I have tried disabling ipv6, setting a static ip, but no go.  Does anyone have any ideas?

ifconfig shows no IP, dhclient results in no DHCP offers and pinging my router's IP results in Network is Unreachable.

---

### Post by MooPi on 2010-12-05
can you give us the results of ```
ifconfig
```and the contents of ```
cat /etc/network/interfaces
```

---

### Post by karthick87 on 2010-12-05
Are you using network manager for connecting to internet?

---

### Post by dineshs on 2010-12-06
What does ```
sudo lshw -C network
```say?Please post result.Also ensure that the interface is enabled(If you are using network manager rightclick the NM icon on top right of the panel and ensure that enable networking is ticked)

---

### Post by yvickers on 2010-12-06
**ifconfig:**
```
eth0      Link encap:Ethernet  HWaddr 00:1a:92:42:cd:8a  
          inet6 addr: fe80::21a:92ff:fe42:cd8a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:1876 (1.8 KB)
          Interrupt:33 

eth1      Link encap:Ethernet  HWaddr 00:1a:92:42:d8:4a  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:34 Base address:0x2000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:80 errors:0 dropped:0 overruns:0 frame:0
          TX packets:80 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:6080 (6.0 KB)  TX bytes:6080 (6.0 KB)
```

**cat /etc/network/interfaces**
```
auto lo
iface lo inet loopback
```

Enable Networking is checked in Network Manager.

I ran lshw -C network which briefly produced some text in the terminal, but I think it was just running checks since nothing actually got printed out.  The only one I could catch was PCI (sysfs).

---

### Post by dineshs on 2010-12-06
> I ran lshw -C network which briefly produced some text in the terminal, but I think it was just running checks since nothing actually got printed out. The only one I could catch was PCI (sysfs).
It will take some time for the result(less than a minute)

---

### Post by yvickers on 2010-12-06
These are the exact results I get for lshw.  After it flashes PCI(sysfs) and SCSI it does nothing else.

lshw -C network:
```

@ubuntu:~$ sudo lshw -C network
@ubuntu:~$      

```

---

### Post by yvickers on 2010-12-07
Just a quick update.  Using Network Manager I changed my eth0 to use a static ip address and network manager now sees my card as connected although I still can't ping my local router.  To add even more frustration, when I login to the router's admin page from my netbook, it shows the mac address of my ubuntu card as active.

Anyone have any thoughts?

---

### Post by yvickers on 2010-12-08
One last bump to see if anyone has ideas, thanks.

---

### Post by doughless on 2011-03-26
I am actually having this exact same issue when connecting to a router with DD-WRT build 14929 on my wired ethernet (I haven't tried any other builds, yet). When connecting via wireless, I get an IP address every time. If booting into Windows, it works over the wired and the wireless connections. If using an older router with OpenWrt, Ubuntu and Windows both work over wired and wireless.

I'd normally blame dd-wrt for this issue, but seeing as I get an IP address in Windows just fine, I'm completely at a loss at whose fault this is.

UPDATE: I am able to get a wired connection working sort of, but using ethtool to setting link speed and duplex to 100 Mbps Full, then manually running dhclient eth0. NetworkManager still thinks I'm not connected, but the internet at least works. My new router has a gigabit switch, so I'm guessing the auto negotiate is somehow failing in Ubuntu.

I'm not sure if this situation is similar to the OP, but setting startup scripts to force a 100 Mbit connection might be a possible workaround for him, too.

UPDATE 2: Sorry for the 2nd update, I was wrong in the first update, I can actually get a wired connection by simply manually running dhclient in a terminal window; there is no need to change speed or duplex at all. And as long as I don't play around with my connection using NetworkManager or reboot my computer, my Internet connection will keep working (and NetworkManager still thinks I'm not connected, even though it's wrong).

---

### Post by LucidParody on 2011-05-09
Hello,

I think I had this same problem but may have found a solution. It started when I installed dd-wrt on my router. I tried creating a static dhcp address for my desktop (running ubuntu). When I would reboot, it would not recognize the connection. When I would run sudo dhclient3 eth0, I would get:

```
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/eth0/00:1d:09:95:39:76
Sending on   LPF/eth0/00:1d:09:95:39:76
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 19
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 21
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```

When I turned off static mode, reconnected it to a different eth port on my router and re-ran dhclient3, it would assign a new IP and it would connect. As long as my router was assigning a new IP, it would work. But, if the old lease was in tact after a restart, it wouldn't work regardless of whether I plugged the computer into a different eth port. I would have to go manually into the router and have the router release the IP lease before I could get it to connect.

It seemed to have fixed itself when I went to preferences > network connections > edit Auto eth0 > IPv4 Settings. Here, I changed method to Automatic (DHCP) instead of Automatic (DHCP) addresses only.

Once I did that, it seemed to work again. BUT I don't know if this is a permanent fix. I suppose if you don't hear from me again, this problem has not come back up and therefore you may assume it was a permanent fix.

---

### Post by zepolmot on 2011-05-10
I've been having the same issue, unless the poster above, my Network Manager has always been set to Automatic (DHCP).  I'll be keeping an eye on this thread hoping to find a fix.

---

