---
title: "Internet Connectivity Failing on 8.10"
date: 2009-04-26
forum: Networking &amp; Wireless
---

### Post by haineb on 2009-04-26
I've got an 8.10 box that is hooked up to my LAN. All my other (non-Linux) machines on the LAN are working just fine. The Linux box is unable to reach the internet, at least almost entirely.

-- Rambling details --
The Linux box has dual NICs into the router. Because it's a simple router, I've hardcoded one IP (from the host side) on one NIC for consistent accessibility, and left the other on DHCP (configs/interface statuses at end). When I initially set this up, my connection to the internet seemed mostly functional. However, the system seemed to sort of degrade into no internet connectivity. (This was after plenty of restarts and whatnot. The system didn't go from working to broken after one restart.) The first thing that I noticed was that DNS was... sketchy. I also noticed some very occasional problems with connectivity to both internet and LAN. (These problems probably aren't relevant, but I'm not sure.) However, the problem has recently gotten worse.
(I'm kind of a Linux noob, but I appreciate a challenge, which... this definitely is...)
-- End rambling details --

The Linux box still has 100% connectivity within my LAN. I can ping my router just fine, my router can ping the internet just fine, but the Linux box itself has no internet accessibility. I'd blame the router, but all the other systems on the network are behaving perfectly normally. I also don't believe I've made any configuration changes to the Linux box or the router. All my routing tables look perfectly happy.

The one thing that makes me exceptionally suspicious is that 'apt-get update' seems to be able to retrieve information on what new updates are available. The update fails when it starts to try to download the new packages. To me, this suggests that SOME sort of connectivity is out there, I just can't exactly nail it down.

I was going to just reformat and upgrade to 9.04, but it's a challenge to fix what I've got going on. Does anyone have any ideas as to what might be going on with my connectivity? Any help would be appreciated. Thanks.






-- Configs/statuses --

haineb@host1:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

# NIC used for regular DHCP connectivity
auto eth0
iface eth0 inet dhcp

# NIC used for hardcoded line to router
# DHCP pool starts at 100
auto eth1
iface eth1 inet static
      address 192.168.1.2
      netmask 255.255.255.0
      network 192.168.1.0
      broadcast 192.168.1.255
      gateway 192.168.1.1
      # DNS servers hardcoded with whatever was picked dynamically... clearly this may need to be updated at a later point...
      dns-nameservers 24.92.226.40 24.92.226.41

haineb@host1:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:02:e3:06:f1:12
          inet addr:192.168.1.105  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::202:e3ff:fe06:f112/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:17006 errors:2 dropped:0 overruns:0 frame:0
          TX packets:16566 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:4301723 (4.3 MB)  TX bytes:1433750 (1.4 MB)
          Interrupt:19 Base address:0xb800

eth1      Link encap:Ethernet  HWaddr 00:0e:a6:a8:87:e4
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20e:a6ff:fea8:87e4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1041 errors:0 dropped:0 overruns:0 frame:0
          TX packets:486 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:983901 (983.9 KB)  TX bytes:43985 (43.9 KB)
          Interrupt:23 Base address:0x4000

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:200 (200.0 B)  TX bytes:200 (200.0 B)

haineb@host1:~$ netstat -rn
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.1.0     0.0.0.0         255.255.255.0   U         0 0          0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U         0 0          0 eth1
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG        0 0          0 eth1
0.0.0.0         192.168.1.1     0.0.0.0         UG        0 0          0 eth0

-- End configs/statuses --

---

### Post by Doncr on 2009-04-27
```
# DNS servers hardcoded with whatever was picked dynamically... clearly this may need to be updated at a later point...
dns-nameservers 24.92.226.40 24.92.226.41
```

Can you do this? Shouldn't the DNS server be in the /etc/resolve.conf file?

NetworkManager keeps deleting the contents of the resolve.conf file - maybe that is the problem.

---

### Post by uniden9 on 2009-04-28
Your problem is going to be your routes.

haineb@host1:~$ netstat -rn
Kernel IP routing table
Destination Gateway Genmask Flags MSS Window irtt Iface
192.168.1.0 0.0.0.0 255.255.255.0 U 0 0 0 eth0
192.168.1.0 0.0.0.0 255.255.255.0 U 0 0 0 eth1
169.254.0.0 0.0.0.0 255.255.0.0 U 0 0 0 eth0
0.0.0.0 192.168.1.1 0.0.0.0 UG 0 0 0 eth1
0.0.0.0 192.168.1.1 0.0.0.0 UG 0 0 0 eth0

You have two default gateways and both nics have the exact same network attached. Its confusing to the router, and its probably picked the wrong one.  Its not that you can not have more than one default gateway, it just greatly complicates routing tables.  This looks more like you are creating a bridge between eth0 to eth1.  Try deleting the none internet default gateway from the routing table, which ever it is.
0.0.0.0 192.168.1.1 0.0.0.0 UG 0 0 0 eth1
0.0.0.0 192.168.1.1 0.0.0.0 UG 0 0 0 eth0

$sudo route del default gw 192.168.1.1 eth?

Note that you can use more than one default gateway, but its more trouble than its worth. Just add in your static routes.

Justin

---

### Post by haineb on 2009-05-10
Removing the second default route did the trick, thanks. The corrected interfaces file can be found at the bottom of this post.



Why is this necessary? Ideally, I'd like fully redundant NICs on this machine.

You mentioned that this could be confusing the router, but I don't see how that would be possible. As far as the router is concerned, these should be two completely seperate NICs, two different IP addresses, two different traffic flows, functionally completely seperate devices. I can't really imagine any way that the outgoing traffic stream would be a problem. (Apart from, perhaps, the host not having a way to resolve the tie in its metrics, but that would be... very unusual...)

Is the issue with how the host is handling the incoming traffic streams? I would have expected that it wouldn't really care, but perhaps I was wrong. Clearly *something* is causing an issue...



(As far as I know, hardcoding the DNS servers should work fine, but once I removed the second default gateway, the DNS server hardcodes weren't making any difference. It was just a misguided attempt to fix the problem.)



Functioning interfaces config:
haineb@host1:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

# NIC used for regular DHCP connectivity
auto eth0
iface eth0 inet dhcp

# NIC used for hardcoded line to router
# DHCP pool starts at 100
auto eth1
iface eth1 inet static
      address 192.168.1.2
      netmask 255.255.255.0
      network 192.168.1.0
      broadcast 192.168.1.255
      # gateway 192.168.1.1 # Causes kernel routing problems when enabled?

---

### Post by haineb on 2009-05-10
Whoops. Should have Googled first. I believe the following post sort of explains the issue to some degree:

[http://kindlund.wordpress.com/2007/11/19/configuring-multiple-default-routes-in-linux/](http://kindlund.wordpress.com/2007/11/19/configuring-multiple-default-routes-in-linux/)

---

