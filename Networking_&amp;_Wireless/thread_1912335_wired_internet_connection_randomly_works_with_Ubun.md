---
title: "wired internet connection randomly works with Ubuntu"
date: 2012-01-20
forum: Networking &amp; Wireless
---

### Post by bluenite on 2012-01-20
hi, i've been having an issue with Ubuntu whereby it will randomly connect to the internet. Sometimes it remains connected for days, other times it will not connect at all for a number of days.

i've searched this forum and have ran some of the commands in the shell, however, the problem (i believe) is not a hardware issue. my current settup is a windows dual boot and whenever i log into windows, the internet works 100%. when i reboot into Ubuntu, it usually fails to connect. i've disconnected the modem and even turned it off for a few hours, but Ubuntu will randomly connect (if at all).

here are the commands when it failed to connect:

```
ubuntu@ubuntu-Aspire-T135:[~]
(11:23:39) ubuntu $ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:15:e9:82:50:2b  
          inet6 addr: fe80::215:e9ff:fe82:502b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1040 (1.0 KB)  TX bytes:90 (90.0 B)
          Interrupt:18 Base address:0xa000 

eth1      Link encap:Ethernet  HWaddr 00:15:58:26:d1:14  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 Base address:0xc800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:18 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1080 (1.0 KB)  TX bytes:1080 (1.0 KB)

ubuntu@ubuntu-Aspire-T135:[~]
(11:23:40) ubuntu $ lspci -nnk | grep -iA2 net
00:0a.0 Ethernet controller [0200]: VIA Technologies, Inc. VT6105/VT6106S [Rhine-III] [1106:3106] (rev 86)
	Subsystem: D-Link System Inc DFE-530TX rev C [1186:1403]
	Kernel driver in use: via-rhine
--
00:13.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
	Subsystem: Packard Bell B.V. Device [1631:d007]
	Kernel driver in use: 8139too
ubuntu@ubuntu-Aspire-T135:[~]
(11:23:40) ubuntu $ lsmod
Module                  Size  Used by
binfmt_misc             7984  1 
ipt_REJECT              2440  1 
ipt_LOG                 5394  5 
xt_limit                2204  7 
xt_tcpudp               2627  8 
ipt_addrtype            2175  4 
xt_state                1386  7 
snd_via82xx            24092  2 
gameport               11224  1 snd_via82xx
snd_ac97_codec        125227  1 snd_via82xx
ip6table_filter         1719  1 
ac97_bus                1474  1 snd_ac97_codec
ip6_tables             20665  1 ip6table_filter
snd_pcm                89104  2 snd_via82xx,snd_ac97_codec
nf_nat_irc              1601  0 
snd_page_alloc          8588  2 snd_via82xx,snd_pcm
snd_mpu401_uart         6849  1 snd_via82xx
nf_conntrack_irc        4501  1 nf_nat_irc
nf_nat_ftp              1831  0 
snd_seq_midi            5932  0 
nf_nat                 20067  2 nf_nat_irc,nf_nat_ftp
nf_conntrack_ipv4      13143  9 nf_nat
nf_defrag_ipv4          1569  1 nf_conntrack_ipv4
snd_rawmidi            22207  2 snd_mpu401_uart,snd_seq_midi
nvidia               8098045  34 
nf_conntrack_ftp        7158  1 nf_nat_ftp
snd_seq_midi_event      7291  1 snd_seq_midi
nf_conntrack           75238  7 xt_state,nf_nat_irc,nf_conntrack_irc,nf_nat_ftp,nf_nat,nf_conntrack_ipv4,nf_conntrack_ftp
snd_seq                57512  2 snd_seq_midi,snd_seq_midi_event
snd_timer              23850  2 snd_pcm,snd_seq
snd_seq_device          6912  3 snd_seq_midi,snd_rawmidi,snd_seq
ppdev                   6804  0 
iptable_filter          1778  1 
ip_tables              19139  1 iptable_filter
snd                    64181  12 snd_via82xx,snd_ac97_codec,snd_pcm,snd_mpu401_uart,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
x_tables               24423  10 ipt_REJECT,ipt_LOG,xt_limit,xt_tcpudp,ipt_addrtype,xt_state,ip6table_filter,ip6_tables,iptable_filter,ip_tables
soundcore               1240  1 snd
parport_pc             30086  1 
edac_core              46822  0 
psmouse                62080  0 
k8temp                  4128  0 
serio_raw               4910  0 
i2c_viapro              6817  0 
edac_mce_amd            9387  0 
shpchp                 34910  0 
lp                     10201  0 
parport                37032  3 ppdev,parport_pc,lp
8139too                23197  0 
usb_storage            50436  0 
floppy                 65299  0 
8139cp                 20365  0 
pata_via                9280  0 
sata_via                9840  2 
via_rhine              22488  0 
mii                     5261  3 8139too,8139cp,via_rhine
ubuntu@ubuntu-Aspire-T135:[~]
(11:23:40) ubuntu $ cat /etc/resolv.conf
# Generated by NetworkManager
domain cable.virginmedia.net
search cable.virginmedia.net
nameserver 194.168.4.100
nameserver 194.168.8.100
ubuntu@ubuntu-Aspire-T135:[~]
(11:23:40) ubuntu $ cat /etc/network/interfaces
auto lo
iface lo inet loopback

ubuntu@ubuntu-Aspire-T135:[~]
(11:23:40) ubuntu $ ping archive.ubuntu.com -c 6
ping: unknown host archive.ubuntu.com
ubuntu@ubuntu-Aspire-T135:[~]
(11:24:00) ubuntu $ ping 212.11.24.124
connect: Network is unreachable
ubuntu@ubuntu-Aspire-T135:[~]
(11:24:14) ubuntu $ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:15:e9:82:50:2b  
          inet6 addr: fe80::215:e9ff:fe82:502b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1726 (1.7 KB)  TX bytes:90 (90.0 B)
          Interrupt:18 Base address:0xa000 

eth1      Link encap:Ethernet  HWaddr 00:15:58:26:d1:14  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 Base address:0xc800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:18 errors:0 dropped:0 overruns:0 frame:0
          TX packets:18 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1080 (1.0 KB)  TX bytes:1080 (1.0 KB)

ubuntu@ubuntu-Aspire-T135:[~]
(11:24:26) ubuntu $ dmesg | grep -i eth0
[    1.004522] eth0: VIA Rhine III at 0xe8000000, 00:15:e9:82:50:2b, IRQ 18.
[    1.005231] eth0: MII PHY found at address 1, status 0x786d advertising 05e1 Link 45e1.
[   22.604321] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   33.600007] eth0: no IPv6 routers present
ubuntu@ubuntu-Aspire-T135:[~]
(11:24:28) ubuntu $ sudo service networking status
[sudo] password for ubuntu: 
networking stop/waiting
ubuntu@ubuntu-Aspire-T135:[~]
ubuntu@ubuntu-Aspire-T135:[~]
(11:14:21) ubuntu $ cat /etc/network/interfaces
auto lo
iface lo inet loopback

ubuntu@ubuntu-Aspire-T135:[~]
(11:14:28) ubuntu $ sudo service networking status
[sudo] password for ubuntu: 
networking stop/waiting
ubuntu@ubuntu-Aspire-T135:[~]
(11:14:38) ubuntu $ cat /etc/resolv.conf
# Generated by NetworkManager
domain cable.virginmedia.net
search cable.virginmedia.net
nameserver 194.168.4.100
nameserver 194.168.8.100
ubuntu@ubuntu-Aspire-T135:[~]
(11:14:48) ubuntu $ cat /etc/nsswitch.conf
# /etc/nsswitch.conf
#
# Example configuration of GNU Name Service Switch functionality.
# If you have the `glibc-doc-reference' and `info' packages installed, try:
# `info libc "Name Service Switch"' for information about this file.

passwd:         compat
group:          compat
shadow:         compat

hosts:          files mdns4_minimal [NOTFOUND=return] dns mdns4
networks:       files

protocols:      db files
services:       db files
ethers:         db files
rpc:            db files

netgroup:       nis
ubuntu@ubuntu-Aspire-T135:[~]
(11:14:57) ubuntu $ sudo lshw -C network
  *-network:0             
       description: Ethernet interface
       product: VT6105/VT6106S [Rhine-III]
       vendor: VIA Technologies, Inc.
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: 86
       serial: 00:15:e9:82:50:2b
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.4.3 duplex=full latency=64 link=yes maxlatency=8 mingnt=3 multicast=yes port=MII speed=100Mbit/s
       resources: irq:18 ioport:9000(size=256) memory:e8000000-e80000ff memory:40000000-4000ffff
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 13
       bus info: pci@0000:00:13.0
       logical name: eth1
       version: 10
       serial: 00:15:58:26:d1:14
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10Mbit/s
       resources: irq:18 ioport:c800(size=256) memory:e8003000-e80030ff
ubuntu@ubuntu-Aspire-T135:[~]


```

can anyone help with this? any help would be appreciated! :)

---

### Post by optima4 on 2012-01-20
Honestly I'm going to tell you right now, even though your wifi card is perfectly good, its a compatibility issue with Linux. I offer you to read through my threads regarding this. I have had nothing, but trouble since I began with Linux. Some of my posts reflect my hysteria. I am sure of it that there is a work around this such as setting up the network in a way that it has a stronger connection. I remember finally coming ot the conclusion someone ended up making me realize (possibly on LinuxQuestions.org) that though my wifi card is good, Linux does not read the same, its just not the same. 

Thats the price and cost of mislead marketing.

---

### Post by verymadpip on 2012-01-20
You did say wired connection & not wireless right?

I'm not the guy to help you unfortunately, but if you have a little patience there are several very helpful people who can assist with networking, praseodym & wildmanne39 spring to mind.

I recently had trouble with my wired connection which needed some different drivers putting in place.  A 5 minute job with help from these forums.

---

### Post by Claus7 on 2012-01-20
Hello and welcome!

In order for someone to give a hand, more info are required. First of you have to give your card type (I was not able to understand which was), the ubuntu version you are using and how you configured your network in the first place. 

The more info you give, the better for someone who has faced the same problem. Answers do not come out of the blue. Most times is trial and error.

Regards!

---

### Post by spacecheck on 2012-01-20
You may need to review the specs for your system, to select the correct support modules for your specific devices. Conflicting device info from Acer is available here:
[http://support.acer.com/product/default.aspx?modelId=382](http://support.acer.com/product/default.aspx?modelId=382)
and here:
[http://support.acer.com/acerpanam/desktop/0000/Acer/AspireT135/AspireT135sp2.shtml](http://support.acer.com/acerpanam/desktop/0000/Acer/AspireT135/AspireT135sp2.shtml)
with one citing "Integrated Intel® 10/100 Base T" and the other citing "Realtek" while the above cites both:

>   *-network:0 
       description: Ethernet interface
       product: VT6105/VT6106S [Rhine-III]
       vendor: VIA Technologies, Inc.
and:

>   *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.

One is perhaps the WLAN device, with the other the LAN, but if VIA driver is installed for an intel device, performance and other problems should not be surprising.

Happy hunting!

---

### Post by bluenite on 2012-01-20
thanks for all your replies

@verymadpip & @optima4 - the funny thing is, i've had absolutely _no_ issues with my internet connection for years using my current set up - this is only a recent problem!! so i'm really confused that Windows works fine, but Ubuntu is giving me hassle?!?

@Claus7 & @spacecheck - i've run the same commands while the connection was working and yes, it's a wired connection. Configuration itself was doing during the initial installation


```
ubuntu@ubuntu-Aspire-T135:[~]
(08:57:34) ubuntu $ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:15:e9:82:50:2b  
          inet addr:86.**.**.194  Bcast:86.**.**.255  Mask:255.255.252.0
          inet6 addr: fe80::215:e9ff:fe82:502b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:288 errors:0 dropped:0 overruns:0 frame:0
          TX packets:306 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:217970 (217.9 KB)  TX bytes:33290 (33.2 KB)
          Interrupt:18 Base address:0x4000 

eth1      Link encap:Ethernet  HWaddr 00:15:58:26:d1:14  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 Base address:0xc800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)

ubuntu@ubuntu-Aspire-T135:[~]
(08:57:57) ubuntu $ lspci -nnk | grep -iA2 net
00:0a.0 Ethernet controller [0200]: VIA Technologies, Inc. VT6105/VT6106S [Rhine-III] [1106:3106] (rev 86)
	Subsystem: D-Link System Inc DFE-530TX rev C [1186:1403]
	Kernel driver in use: via-rhine
--
00:13.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
	Subsystem: Packard Bell B.V. Device [1631:d007]
	Kernel driver in use: 8139too
ubuntu@ubuntu-Aspire-T135:[~]
(08:58:05) ubuntu $ lsmod
Module                  Size  Used by
vesafb                 13761  1 
binfmt_misc            17565  1 
snd_via82xx            29692  2 
gameport               19652  1 snd_via82xx
snd_ac97_codec        134270  1 snd_via82xx
ac97_bus               12730  1 snd_ac97_codec
snd_pcm                96391  2 snd_via82xx,snd_ac97_codec
snd_page_alloc         18529  2 snd_via82xx,snd_pcm
snd_mpu401_uart        14169  1 snd_via82xx
snd_seq_midi           13324  0 
nvidia               8107272  34 
snd_rawmidi            30486  2 snd_mpu401_uart,snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
ppdev                  17113  0 
snd_seq                61621  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29602  2 snd_pcm,snd_seq
snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    67382  12 snd_via82xx,snd_ac97_codec,snd_pcm,snd_mpu401_uart,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                73535  0 
ipt_REJECT             12576  1 
ipt_LOG                17016  5 
xt_limit               12711  7 
xt_tcpudp              12603  8 
ipt_addrtype           12599  4 
edac_core              53845  0 
serio_raw              13166  0 
soundcore              12680  1 snd
xt_state               12578  7 
i2c_viapro             13153  0 
edac_mce_amd           23464  0 
k8temp                 13016  0 
shpchp                 37297  0 
ip6table_filter        12815  1 
ip6_tables             27845  1 ip6table_filter
nf_nat_irc             12643  0 
nf_conntrack_irc       13383  1 nf_nat_irc
nf_nat_ftp             12649  0 
nf_nat                 25736  2 nf_nat_irc,nf_nat_ftp
nf_conntrack_ipv4      19640  9 nf_nat
parport_pc             36959  1 
nf_defrag_ipv4         12729  1 nf_conntrack_ipv4
nf_conntrack_ftp       13359  1 nf_nat_ftp
nf_conntrack           81956  7 xt_state,nf_nat_irc,nf_conntrack_irc,nf_nat_ftp,nf_nat,nf_conntrack_ipv4,nf_conntrack_ftp
iptable_filter         12810  1 
ip_tables              27456  1 iptable_filter
x_tables               29581  10 ipt_REJECT,ipt_LOG,xt_limit,xt_tcpudp,ipt_addrtype,xt_state,ip6table_filter,ip6_tables,iptable_filter,ip_tables
lp                     17825  0 
parport                46458  3 ppdev,parport_pc,lp
usb_storage            53538  0 
8139too                32086  0 
uas                    17996  0 
pata_via               13632  0 
floppy                 74120  0 
8139cp                 27218  0 
sata_via               13760  2 
via_rhine              31816  0 
ubuntu@ubuntu-Aspire-T135:[~]
(08:58:10) ubuntu $ cat /etc/resolv.conf
# Generated by NetworkManager
domain cable.virginmedia.net
search cable.virginmedia.net
nameserver 194.168.4.100
nameserver 194.168.8.100
ubuntu@ubuntu-Aspire-T135:[~]
(08:58:20) ubuntu $ cat /etc/network/interfaces
auto lo
iface lo inet loopback

ubuntu@ubuntu-Aspire-T135:[~]
(08:58:28) ubuntu $ ping archive.ubuntu.com -c 6
PING archive.ubuntu.com (91.189.92.184) 56(84) bytes of data.
64 bytes from zaurac.canonical.com (91.189.92.184): icmp_req=1 ttl=52 time=14.9 ms
64 bytes from zaurac.canonical.com (91.189.92.184): icmp_req=2 ttl=52 time=11.6 ms
64 bytes from zaurac.canonical.com (91.189.92.184): icmp_req=3 ttl=52 time=13.1 ms
64 bytes from zaurac.canonical.com (91.189.92.184): icmp_req=4 ttl=52 time=14.2 ms
64 bytes from zaurac.canonical.com (91.189.92.184): icmp_req=5 ttl=52 time=10.8 ms
^C
--- archive.ubuntu.com ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 4006ms
rtt min/avg/max/mdev = 10.879/12.984/14.975/1.539 ms
ubuntu@ubuntu-Aspire-T135:[~]
(08:58:42) ubuntu $ dmesg | grep -i eth0
[    0.964233] eth0: VIA Rhine III at 0xe8000000, 00:15:e9:82:50:2b, IRQ 18.
[    0.964942] eth0: MII PHY found at address 1, status 0x786d advertising 05e1 Link 45e1.
[   21.725351] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
[   32.200015] eth0: no IPv6 routers present
ubuntu@ubuntu-Aspire-T135:[~]
(08:58:54) ubuntu $ sudo service networking status
[sudo] password for ubuntu: 
networking stop/waiting
ubuntu@ubuntu-Aspire-T135:[~]
(08:59:07) ubuntu $ !1982
sudo lshw -C network
  *-network:0             
       description: Ethernet interface
       product: VT6105/VT6106S [Rhine-III]
       vendor: VIA Technologies, Inc.
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: 86
       serial: 00:15:e9:82:50:2b
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.5.0 duplex=full ip=86.24.68.194 latency=64 link=yes maxlatency=8 mingnt=3 multicast=yes port=MII speed=100Mbit/s
       resources: irq:18 ioport:9000(size=256) memory:e8000000-e80000ff memory:40000000-4000ffff
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 13
       bus info: pci@0000:00:13.0
       logical name: eth1
       version: 10
       serial: 00:15:58:26:d1:14
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10Mbit/s
       resources: irq:18 ioport:c800(size=256) memory:e8003000-e80030ff
```

---

### Post by Claus7 on 2012-01-21
Hello,

the info you sent I think that they are overwhelming. So the story: I had a dns issue with my network, which meant that I was able to ping, yet I was not able to browse. 

When you mean, that you have no network at all, do you mean that everything is down? Can you ping?

Are you sure that when you do not have network, when you switch to windows, networking is working ok?

Also, which ubuntu version are you using?

Can you remember if you did any specific installation that might have caused the issue?

Regards!

---

### Post by bluenite on 2012-01-21
> **Claus7 said:**
> 
When you mean, that you have no network at all, do you mean that everything is down? Can you ping?


hi, no i can't even ping. error i receive is:

connect: Network is unreachable

> **Claus7 said:**
> 
Are you sure that when you do not have network, when you switch to windows, networking is working ok?


yes, absolutely 100% certain. that's what has confused me! windows works perfect, but Ubuntu is randomly working (50% of the time).

Ubuntu was installed a few years ago and it has always worked perfectly up until 3 weeks ago, where i started to get this problem. at first i thought it was my ISP, but switching to windows proved it wasn't.

> **Claus7 said:**
> 
Can you remember if you did any specific installation that might have caused the issue?


nothing has been added or changed in the last 3 years. i always update whenever asked to do so, but no modifications to any files or HW.

thanks

---

### Post by Claus7 on 2012-01-21
Hello,

I wish I could help you more, yet your 'symptoms' are a little bit strange.

I insist on asking you about your ubuntu flavour, because I had some problems with maverick, which seemed to be a bug. The same also hunted lucid, yet this was happening from time to time, which does not apply to you since you have a connection which was unaffected for years.

Can you go to System->Administration->Log File Viewer and see there if you receive some messages about your network. It would be advisable to do so either right away after booting (while you realised that you have no internet connection) or at the time connection stops.

One more thing I could think of is a static IP instead of dynamic, or change of DNS, which might conflict with modems, yet this is not so much the case, since your hardware remains the same.

Anyway, I think the log files might shed some more light about your issue.

Regards!

---

