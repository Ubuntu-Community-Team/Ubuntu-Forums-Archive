---
title: "No wireless since installation and no Ethernet connection after first upgrade"
date: 2011-02-02
forum: Networking &amp; Wireless
---

### Post by ivotkl on 2011-02-02
Hi everyone! First of all I want to thank you all for the great support you provide each day to newbies like me. :lolflag:
 
Now, here's the deal:
I've posted the situation on two different threads explaining myself, but as they were kind of oldies or with low recent activity, I got no reply. Posts would be [this one]("http://ubuntuforums.org/showthread.php?p=10392560#post10392560") and [this one]("http://ubuntuforums.org/showthread.php?p=10391310#post10391310").
 
Information posted is:
[quote=ivotkl (on both threads)]
Comands entered:
ifconfig
iwconfig
sudo lshw -C network
 
 
 
Output shows:
root@ivan-lnv:/home/ivan# ifconfig
lo Link encap:Local Loopback 
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:16 errors:0 dropped:0 overruns:0 frame:0
TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0 
RX bytes:960 (960.0 B) TX bytes:960 (960.0 B)
 
root@ivan-lnv:/home/ivan# iwconfig
lo no wireless extensions.
 
eth0 no wireless extensions.
 
wlan0 IEEE 802.11bg ESSID:eek:ff/any 
Mode:Managed Access Point: Not-Associated Tx-Power=20 dBm 
Retry long limit:7 RTS thr:eek:ff Fragment thr:eek:ff
Encryption key:eek:ff
Power Management:eek:ff
 
root@ivan-lnv:/home/ivan# sudo lshw -C network
*-network 
description: Network controller
product: BCM4312 802.11b/g
vendor: Broadcom Corporation
physical id: 0
bus info: pci@0000:04:00.0
version: 01
width: 64 bits
clock: 33MHz
capabilities: pm msi pciexpress bus_master cap_list
configuration: driver=b43-pci-bridge latency=0
resources: irq:18 memory:f4500000-f4503fff
*-network DISABLED
description: Ethernet interface
product: NetLink BCM5906M Fast Ethernet PCI Express
vendor: Broadcom Corporation
physical id: 0
bus info: pci@0000:07:00.0
logical name: eth0
version: 02
serial: 00:26:22:c8:ba:d7
capacity: 100MB/s
width: 64 bits
clock: 33MHz
capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.102 duplex=half firmware=sb v3.04 latency=0 link=yes multicast=yes port=twisted pair
resources: irq:17 memory:f4600000-f460ffff
*-network DISABLED
description: Wireless interface
physical id: 1
logical name: wlan0
serial: 00:26:82:2b:9c:11
capabilities: ethernet physical wireless
configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
 
 
 
 
 
Do I need to use broadcom-wl-4.150.10.5.tar.bz2, broadcom-wl-4.80.53.0.tar.bz2, both or none (meaning a different one)? How do I do that?
 
Oh and BTW, I have no Eth0 after upgrading the system, not even booting up with the previous kernel, but I do have wirless and wired connection with XP.
I'm running Ubuntu Studio with Windows XP dual boot. Lenovo G550 with 4GB RAM. Model name is 2958J6Y.
 
Thank you so much for the help.
Greets.
 
PS: I also posted it [[COLOR=#444444]here[/COLOR]]("http://ubuntuforums.org/showthread.php?p=10391310#post10391310") because I didn't know which topic suits my situation best. I guess the other one, but anyways... Hope you can help me. =)[/quote]

---

### Post by grahammechanical on 2011-02-02
Have you installed Network Manager? I understand that it is not installed by Ubuntu Studio.

You could try the following in a terminal

```
sudo ifconfig wlan0 down
```  followed by  ```
sudo ifconfig wlan0 up

```and
```
sudo ifdown eth0
```    followed by ```
sudo if up eth0
```It seems that it is best to take down the network device before putting it back up in case it is up and you have not noticed it.

Regards.

---

### Post by ivotkl on 2011-02-02
Ok. I' ve done that and here are the results:
 
```
ivan@ivan-lnv:~$ sudo ifconfig wlan0 down
ivan@ivan-lnv:~$ sudo ifconfig wlan0 up
SIOCSIFFLAGS: No such file or directory
ivan@ivan-lnv:~$ sudo ifdown eth0
ifdown: interface eth0 not configured
ivan@ivan-lnv:~$ sudo ifup eth0
Ignoring unknown interface eth0=eth0
```

I may not know much, but apparently my wireless driver is not configured or not installed. I mean, on Ubuntu (non studio, when it worked properly -different story-), as I have triple boot (again, different story), if I had switched off wireless on Windows, it wouldn't work on ubuntu (I mean phisically, by using the switch on the laptop's front). Anyway, I will not able to install it without a wired connection.
 
Apparently, eth0 was de-configured. It seems strange since  when I was prompted to configure at least one network at the time of installation, I've chosen to configure it manually afterwards and when I booted for the first time after installation wired connection worked fine.
 
Thank you. I will wait for your reply. =)

---

### Post by chenxiaolong on 2011-02-08
Try configuring your ethernet manually by shutting down all the networking services and manually connecting:

First of all, kill the network-manager applet and stop it's service. Then stop, the networking service. If you don't have network-manager installed, skip the first 2 lines (you can check with "dpkg -l | grep network-manager").

```
killall nm-applet
sudo /etc/init.d/network-manager stop
sudo /etc/init.d/networking stop
```

Now try bringing up your ethernet interface and assign a DHCP address to it.

```
sudo ifconfig eth0 up
sudo dhclient eth0
```

Now, try pinging the Ubuntu website, for example, to see if you have internet access.

```
ping www.ubuntu.com
```

If you still can't get online, please post the outputs of (probably easier to put it in a tar.gz and attach it):

```
dmesg | grep -i -e tg3 -e eth0 -e ethernet -e broadcom -e b43 -e wl
cat /etc/network/interfaces
```

The first line will output the boot messages and search for the keywords: tg3 (ethernet driver), eth0, ethernet, broadcom, b43, and wl. The second line will output the network configuration file that's read at boot.

---

### Post by Hedzombie on 2011-02-08
I'm having the same problem,except mine is on a clean install i did yesterday on a HPg60-249wm notebook i'm refurbishing.I get the final message.

NO DHCPOFFERS received
NO Working Leases in persistant database-sleeping

---

### Post by chenxiaolong on 2011-02-08
Another thought that just occurred to me: it could possibly be a kernel driver regression in the kernel. It's the only thing I can think of that would affect the ethernet after an update. If your old kernel, before the update, still shows up in the Grub boot menu (hold shift on bootup if you don't see it), could you try booting from it? I think the version is 2.6.35-22-generic.

EDIT: A post of the output of "dmesg | grep -i -e tg3 -e eth0 -e ethernet -e broadcom -e b43 -e wl" would really help to see if it's a kernel related error.

---

### Post by ivotkl on 2011-02-09
Ok, so I did that and I have ethernet connection. Thank you so much dude, you are awesome!!! Thank you. =)

Anyway, here is the outcome of the codes you've asked.
```
ivan@ivan-lnv:~$ killall nm-applet
nm-applet: no process found
ivan@ivan-lnv:~$ sudo /etc/init.d/network-manager stop
[sudo] password for ivan: 
sudo: /etc/init.d/network-manager: command not found
ivan@ivan-lnv:~$ sudo /etc/init.d/networking stop
 * Deconfiguring network interfaces...                                   [ OK ] 
ivan@ivan-lnv:~$ sudo ifconfig eth0 up
ivan@ivan-lnv:~$ sudo dhclient eth0
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/eth0/00:26:22:c8:ba:d7
Sending on   LPF/eth0/00:26:22:c8:ba:d7
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPOFFER of 192.168.0.100 from 192.168.0.1
DHCPREQUEST of 192.168.0.100 on eth0 to 255.255.255.255 port 67
DHCPACK of 192.168.0.100 from 192.168.0.1
bound to 192.168.0.100 -- renewal in 39315 seconds.
ivan@ivan-lnv:~$ ping www.ubuntu.com
PING www.ubuntu.com (91.189.90.41) 56(84) bytes of data.
64 bytes from jujube.canonical.com (91.189.90.41): icmp_seq=1 ttl=51 time=250 ms
64 bytes from jujube.canonical.com (91.189.90.41): icmp_seq=2 ttl=51 time=264 ms
64 bytes from jujube.canonical.com (91.189.90.41): icmp_seq=3 ttl=51 time=263 ms
64 bytes from jujube.canonical.com (91.189.90.41): icmp_seq=4 ttl=51 time=251 ms
64 bytes from jujube.canonical.com (91.189.90.41): icmp_seq=5 ttl=51 time=268 ms
64 bytes from jujube.canonical.com (91.189.90.41): icmp_seq=6 ttl=51 time=253 ms
64 bytes from jujube.canonical.com (91.189.90.41): icmp_seq=7 ttl=51 time=265 ms
64 bytes from jujube.canonical.com (91.189.90.41): icmp_seq=8 ttl=51 time=253 ms
^C
--- www.ubuntu.com ping statistics ---
9 packets transmitted, 8 received, 11% packet loss, time 8009ms
rtt min/avg/max/mdev = 250.170/258.935/268.492/6.818 ms
ivan@ivan-lnv:~$ dmesg | grep -i -e tg3 -e eth0 -e ethernet -e b43 -e wl
[    1.653944] tg3.c:v3.102 (September 1, 2009)
[    1.654011] tg3 0000:07:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.654028] tg3 0000:07:00.0: setting latency timer to 64
[    1.682372] b43-pci-bridge 0000:04:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[    1.682391] b43-pci-bridge 0000:04:00.0: setting latency timer to 64
[    1.784913] eth0: Tigon3 [partno(BCM95906) rev c002] (PCI Express) MAC address 00:26:22:c8:ba:d7
[    1.784917] eth0: attached PHY is 5906 (10/100Base-TX Ethernet) (WireSpeed[0])
[    1.784920] eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] TSOcap[0]
[    1.784922] eth0: dma_rwctrl[76180000] dma_mask[64-bit]
[   18.798431] b43-phy0: Broadcom 4312 WLAN found (core revision 15)
[   18.865897] Registered led device: b43-phy0::tx
[   18.865917] Registered led device: b43-phy0::rx
[   18.865934] Registered led device: b43-phy0::radio
[  126.466276] tg3 0000:07:00.0: irq 30 for MSI/MSI-X
[  126.499926] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  128.109329] tg3: eth0: Link is up at 100 Mbps, full duplex.
[  128.109329] tg3: eth0: Flow control is on for TX and on for RX.
[  128.110401] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[  138.457061] eth0: no IPv6 routers present
ivan@ivan-lnv:~$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback
```

---

### Post by chenxiaolong on 2011-02-09
Great! I'm glad it worked for you! 

If you also have wireless on your computer, I suggest that you install network-manager to connect to your wireless or to automatically set up your ethernet.

---

### Post by ivotkl on 2011-02-09
Alrighty then. =)
Thank you so much for the help. I will post the results editing this post.
 
Greets!

---

### Post by \/anand on 2011-07-15
hey. im in a similar situation except i guess its a kernel related error. The incomprehensible thing in my case is the network adapter is not working neither in old kernel versions nor in win7 !!!! im confused about how it could be disabled in win7:confused:

I read instruction in this thread and here's what i got as output:
```
void@voidy:~$ sudo ifconfig wlan0 down

wlan0: ERROR while getting interface flags: No such device

void@voidy:~$ sudo ifconfig wlan0 up

wlan0: ERROR while getting interface flags: No such device

void@voidy:~$ sudo ifdown eth0

ifdown: interface eth0 not configured

void@voidy:~$ sudo ifup eth0

Ignoring unknown interface eth0=eth0.

void@voidy:~$ killall nm-applet

void@voidy:~$ sudo /etc/init.d/network-manager stop

Rather than invoking init scripts through /etc/init.d, use the service(8)

utility, e.g. service network-manager stop



Since the script you are attempting to invoke has been converted to an

Upstart job, you may also use the stop(8) utility, e.g. stop network-manager

network-manager stop/waiting

void@voidy:~$ sudo /etc/init.d/networking stop

 * Deconfiguring network interfaces...                                                                                    

                            [ OK ] 

void@voidy:~$ sudo ifconfig eth0 up

void@voidy:~$ sudo dhclient eth0

There is already a pid file /var/run/dhclient.pid with pid 1590

killed old client process, removed PID file

Internet Systems Consortium DHCP Client V3.1.3

Copyright 2004-2009 Internet Systems Consortium.

All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/



Listening on LPF/eth0/20:cf:30:cc:b7:19

Sending on   LPF/eth0/20:cf:30:cc:b7:19

Sending on   Socket/fallback

DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8

DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14

DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12

DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 21

DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6

No DHCPOFFERS received.

No working leases in persistent database - sleeping.


void@voidy:~$ dmesg | grep -i -e tg3 -e eth0 -e ethernet -e broadcom -e b43 -e wl

[    1.561619] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded

[    1.565484] eth0: RTL8168d/8111d at 0xf808a000, 20:cf:30:cc:b7:19, XID 083000c0 IRQ 31

[   12.291879] r8169: eth0: link down

[   12.291960] ADDRCONF(NETDEV_UP): eth0: link is not ready

[ 2293.169969] r8169: eth0: link down

[ 2293.170141] ADDRCONF(NETDEV_UP): eth0: link is not ready


```thanks in advance.

---

### Post by ivotkl on 2012-12-02
Don' t ask why, but when I turn off wireless on windows and restart with adapter' s switch off in ubuntu, it won' t re-enable it regardless the times I turn switch back on.

Currently running 10.04 Lucid Lynx (non Studio), with wireless working.

BTW, what happens if you go to System -> Administration -> Hadrware Drivers?

---

