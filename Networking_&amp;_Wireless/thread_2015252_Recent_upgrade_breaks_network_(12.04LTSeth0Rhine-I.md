---
title: "Recent upgrade breaks network (12.04LTS/eth0/Rhine-III chipset)"
date: 2012-07-03
forum: Networking &amp; Wireless
---

### Post by jas251 on 2012-07-03
Evening all...

So over the weekend I committed to an apt-get update and ever since then my Ubuntu server has had network gremlins.  To be more specific, one really big gremlin that seems to be sitting on the channel between the OS and the Ethernet hardware.

PRIOR TO THE UPGRADE ALL WAS WORKING WELL.

I can ping on localhost and 127.0.0.1 (both for dummy check)
I cannot ping outbound to anything (including default gate 192.168.0.1), nor can anything ping inbound to my server (home-server, 192.168.0.100).  UFW is DISABLED.  Basically no traffic in/out.  

When i first installed Ubuntu onto this HP I had to go buy a 2nd ethernet card (which is what I'm using) because the Ubuntu kernel drivers just wouldn't work with the HP motherboard built-in network chipset.  I really don't want to do that again (shouldn't have to since the dang thing USED to work before the update), and re-installing is a bit frightening since I have a LOT of data in my /srv/share directory.

Options I see: 
1. Figure out the network glitch... (preferred)
2. Beg for one of you to tell me how to do a "clean" re-install without munging my data in /srv/share.
3. Shoot the box.  Cry over lost data.  Go to Windows for future important stuff.

Here's what I've got from a debug perspective...

Current version/kernel:
```

uname -a
Linux home-server 3.2.0-26-generic-pae #41-Ubuntu SMP Thu Jun 14 16:45:14 UTC 2012 i686 Athlon i386 GNU/Linux

```

ifconfig:
```

ifconfig

eth0   Link encap:Ethernet HWaddr: fc:75:16:8a:aa:42
       inet addr:192.168.0.100  Bcast:192.168.0.255  Mask:255.255.255.0
       inet6 addr: fe80::fe75::16ff::fe8a::aa42/64 Scope:Link
       UP BROADCAST RUNNING MULTICAST   MTU:1500  Metric:1
       RX packets:927 errors:0 dropped:0 overruns:0 frame:0
       TX packets:230 errors:0 dropped:0 overruns:0 carrier:0
       collisions:0 txqueuelen:1000
       RX bytes:83375 (83.3 KB)  TX bytes:29274 (29.2 KB)
       Interrupt:22 Base address:0xa000

lo     Link encap:Local Loopback
       inet addr:127.0.0.1  Mask:255.0.0.0
       inet6 addr: ::1/128 Scope:Host
       UP LOOPBACK RUNNING MTU:16436  Metric:1
       RX packets:25 errors:0 dropped:0 overruns:0 frame:0
       TX packets:25 errors:0 dropped:0 overruns:0 carrier:0
       collisions:0 txqueuelen:0
       RX bytes:2179 (2.1 KB)  TX bytes:2179 (2.1 KB)


```

/etc/network/interfaces:
```

cat /etc/network/interfaces

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet dhcp


```

route table:
```

route -n

Kernel IP routing table
Destination  Gateway     Genmask       Flags Metric Ref Use Iface
0.0.0.0      192.168.0.1 0.0.0.0       UG    100    0   0   eth0
192.168.0.0  0.0.0.0     255.255.255.0 U     0      0   0   eth0

```

driver:
```

sudo lshw -class network

*-network
   description: Ethernet interface
   product: VT6105/VT6106S [Rhine-III]
   vendor: VIA Technologies, Inc.
   physical id: 8
   bus info: pci@0000:02:08.0
   logical name: eth0
   version: 86
   serial: fc:75:16:8a:aa:42
   size: 100Mbit/s
   width: 32 bits
   clock: 33MHz
   capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
   configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.5.0 duplex=full ip=192.168.0.100 latency=64 link=yes maxlatency=8 mingnt=3 multicast=yes port=MII speed=100Mbit/s
   resources: irq:22 ioport:de00(size=256) memory:fdcff000-fdcff0ff memory:fdce0000-fdceffff

```

lspci
```

lspci | grep Ethernet
02:08.0 Ethernet controller: VIA Technologies, Inc. VT6105/VT6105S [Rhine-III] (rev 86)

```

Gateway ping attempt:
```

ping 192.168.0.1
PING 192.168.0.1 (192.168.0.1) 56(84) bytes of data.
From 192.168.0.100 icmp_seq=1 Destination Host Unreachable
From 192.168.0.100 icmp_seq=2 Destination Host Unreachable
From 192.168.0.100 icmp_seq=3 Destination Host Unreachable
^C
--- 192.168.0.1 ping statistics ---
6 packets transmitted, 0 received, +3 errors, 100% packet loss, time 5029ms
pipe 3


```

localhost ping
```

ping localhost
PING localhost (127.0.0.1) 56(84) bytes of data.
64 bytes from localhost (127.0.0.1): icmp_req=1 ttl=64 time=0.065 ms
64 bytes from localhost (127.0.0.1): icmp_req=2 ttl=64 time=0.059 ms
64 bytes from localhost (127.0.0.1): icmp_req=3 ttl=64 time=0.060 ms
^C
--- localhost ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2003ms
rt min/avg/max/mdev = 0.059/0.061/0.065/0.006 ms

```

Ping self on 192.168.0.100

```

ping 192.168.0.100
PING 192.168.0.100 (192.168.0.100) 56(84) bytes of data.
64 bytes from 192.168.0.100: icmp_req=1 ttl=64 time=0.060 ms
64 bytes from 192.168.0.100: icmp_req=2 ttl=64 time=0.061 ms
64 bytes from 192.168.0.100: icmp_req=3 ttl=64 time=0.059 ms
^C
--- 192.168.0.100 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2003ms
rt min/avg/max/mdev = 0.059/0.060/0.061/0.000 ms

```

Suggestions? What could have changed?

---

### Post by chili555 on 2012-07-03
> 1. Figure out the network glitch... (preferred)I'll take a number 1 with cheese, please. Please show us:```
dmesg | grep eth0
sudo ifdown eth0 && sudo ifup -v eth0
```Why are you using a DHCP address on a server? Isn't it a lot easier to administer and troubleshoot it, presumably with ssh, with a known static IP?

---

### Post by jas251 on 2012-07-03
Thanks Chili -
Yes, static IP probably would have been smart in the long run.  DHCP was the easy way out during the install, and I've got the IP (192.168.0.100) reserved by MAC at the router.

Here's the output:

dmesg | grep eth0
```

[     1.348779] via-rhine 0000:02:08.0: eth0: VIA Rhine III at 0xfdcff000, fc:75:16:8a:aa:42, IRQ 22
[     1.349513] via-rhine 0000:02:08.0: eth0: MII PHY found at address 1, status 0x786d advertising 05e1 Link cde1
[     9.163975] ADDRCONF(NETDEV_UP): eth0: link is not ready
[    10.314872] via-rhine 0000:02:08.0: eth0: link up, 100 Mbps, full-duplex, lpa 0xCDE1 

```

sudo ifdown eth0 && sudo ifup -v eth0:
```

Rather than invoking init scripts through /etc/init.d, user the service(8)
utility, e.g. service smbd reload

Since the script you are attempting to invoke has been converted to an Upstart job, you may also use the reload(8) utility, e.g. reload smbd
Configuring interface eth0=eth0 (inet)
run-parts --verbose /etc/network/if-pre-up.d
run-parts: executing /etc/network/if-pre-up.d/wireless-tools
run-parts: executing /etc/network/if-pre-up.d/wpasupplicant

dhclient3 -e IF_METRIC-100 -pf /var/run/dhclient.eth0.pid -lf /var/lib/dhcp/dhclient.eth0.leases -1 eth0
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service smbd reload

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the reload(8) utility, e.g. reload smbd
run-parts --verbose /etc/network/if-up.d
run-parts: executing /etc/network/if-up.d/000resolvconf
run-parts: executing /etc/network/if-up.d/ntupdate
run-parts: executing /etc/network/if-up.d/openssh-server
ssh stop/waiting
ssh start/running, process 1671
run-parts: executing /etc/network/if-up.d/samba
run-parts: executing /etc/network/if-up.d/upstart
run-parts: executing /etc/network/if-up.d/wpasupplicant

```

---

### Post by chili555 on 2012-07-03
Please let me see:```
ps aux | grep -i net
sudo cat /var/log/syslog | grep -e etwork -e eth0
```Something smells fishy here.

---

### Post by jas251 on 2012-07-03
ps aux | grep -i net
```

root     11  0.0  0.0       0 ?        S<  10:49  0:00 [netns]
jason  1843  0.0  0.1    4368 tty1     S+  12:39  0:00 grep --color=auto -i net

```

sudo cat /var/log/syslog | grep -e etwork -e eth0
```

sudo cat /var/log/syslog | grep -e etwork -e eth0
Jul  3 13:42:43 home-server kernel: [    1.352758] via-rhine 0000:02:08.0: eth0: VIA Rhine III at oxfdcff000, fc:75:16:8a:aa:42, IRQ 22
Jul  3 13:42:43 home-server kernel: [    1.353493] via-rhine 0000:02:08.0: eth0: MII PHY found at address 1, status 0x786d advertising 05e1 Link cde1
Jul  3 13:42:43 home-server kernel: [    9.139784] ADDRCONF(NETDEV_UP): eth0: link is not ready
Jul  3 13:42:43 home-server kernel: [   10.219331] type=1400 audit(1341340963.610:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=542 comm="apparmor_parser"
Jul  3 13:42:43 home-server dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Jul  3 13:42:43 home-server dhclient: DHCPREQUEST of 192.168.0.100 on eth0 to 255.255.255.255 port 67
Jul  3 13:42:43 home-server kernel: [   11.812596] type=1400 audit(1341340965.206:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=935 comm="apparmor_parser"

```

---

### Post by chili555 on 2012-07-03
Just to humor an old doctor, please undo the IP reservation in the router and then do:```
sudo dhclient eth0
```Do you get an address? Can you ping the router?```
ping -c3 192.168.0.1
```If that works, let's change the interfaces file:```
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
address 192.168.0.155
netmask 255.255.255.0
gateway 192.168.0.1
dns-nameservers 8.8.8.8 192.168.0.1
```And restart the interface:```
sudo ifdown eth0 && sudo ifup eth0
```

---

### Post by jas251 on 2012-07-03
No Joy.  DHCP refreshed the IP address just fine, but still no ping.  I went ahead and reconfigured for static anyway and tried again (hoping...) but no change.  

```


sudu dhclient eth0:

Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service smbd reload

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the reload(8) utility, e.g. reload smbd


ping -c3 192.168.0.1
PING (192.168.0.1) 56(84) bytes of data.
From 192.168.0.100 icmp_seq=1 Destination Host Unreachable
From 192.168.0.100 icmp_seq=2 Destination Host Unreachable
From 192.168.0.100 icmp_seq=3 Destination Host Unreachable

--- 192.168.0.1 ping statistics ---
3 packets transmitted, 0 received, +3 errors, 100% packet loss, time 1999ms
pipe 3

```

---

### Post by chili555 on 2012-07-03
No firewall issues, I hope?? Can you turn off any settings in your Ubuntu computer and see if it helps? I am not a firewall expert so I can't help in that area.

---

### Post by jas251 on 2012-07-03
Not that I know of... UFW is inactive...  As far as I know there is nothing else on the machine unless it was pushed as part of the apt-get update.

---

### Post by chili555 on 2012-07-03
Please leave the interface configured as static and reboot so we have a clean slate. Then do:```
dmesg > jas251.txt
zip jas251.zip jas251.txt
```Find the file jas251.zip in your user directory and transfer it on a USB key or similar and post it as an attachment to your reply using the paperclip tool at the top of the reply box.

Weird!

---

### Post by jas251 on 2012-07-04
Here you go... Thanks for walking through this with me.  I appreciate the help.  This one has me stumped.

---

### Post by jas251 on 2012-07-06
Hey Chili -
So chalk another one up to "it wasnt the dang box afterall".  Turns out one of the Ethernet switches between here and there got into a weird state.  Still not sure what was up as traffic to/from all other systems on the network were fine, but it seems that at the E/net level traffic to the linux server's MAC was getting munged.  Hard reset the switch and all works now.
Thanks for your patience and help...

---

### Post by chili555 on 2012-07-06
I'm glad to know it's working by whatever means. Thanks.

---

