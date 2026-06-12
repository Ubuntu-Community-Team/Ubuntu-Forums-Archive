---
title: "SLOW gigabit lan"
date: 2012-03-02
forum: Networking &amp; Wireless
---

### Post by amuh on 2012-03-02
I have a problem with my newly built NAS / webhost PC. I'm currently running Ubuntu Server with 2 NIC's and experiencing slow file transfers (around 5MB/s) 

1 nic (integrated with my motherboard)connected with my Gigabit router (dlink dir 655)

nic no 2 ([an external nic from intel]("http://www.intel.com/content/www/us/en/network-adapters/gigabit-network-adapters/gigabit-ct-desktop-adapter.html"))is connected straight to my desktop and is used to handle traffic caused by file transfer (i.e. traffic to the NAS) 

The LAN is wired with CAT6 from Belkin, newly bought. 

The PC consists of a Atom Mini ITX D525 1.8gz dual core cpu. 4Gb RAM and an SSD from corsair(i think). The Pc also has a 2TB Sata Samsung hard drive used for storage. 

I Know that my nic on the desktop is OK since I am able to transfer files to my laptop(without passing data through the router) at around 30-40 Mb/s 

I've tried running Iperf with the NAS as a server and the desktop as a client and vice versa. Here's the results:

The Desktop as server

```
iperf -c 10.0.0.11
------------------------------------------------------------
Client connecting to 10.0.0.11, TCP port 5001
TCP window size: 16.0 KByte (default)
------------------------------------------------------------
[  3] local 10.0.0.1 port 47686 connected with 10.0.0.11 port 5001
[ ID] Interval       Transfer     Bandwidth
[  3]  0.0-10.0 sec   750 MBytes   629 Mbits/sec

```

The Desktop as client
```
iperf -c 10.0.0.1
------------------------------------------------------------
Client connecting to 10.0.0.1, TCP port 5001
TCP window size: 8.00 KByte (default)
------------------------------------------------------------
[128] local 10.0.0.11 port 63041 connected with 10.0.0.1 port 5001
[ ID] Interval       Transfer     Bandwidth
[128]  0.0-10.0 sec   388 MBytes   325 Mbits/sec
```

To me it seems ok, not more. But this shouldn't be a reason for the slow file transfers. Right?

The SSD disk on the server gets theese results from dd
```
dd if=/dev/zero bs=1024k of=tstfile count=1024

1024+0 poster in
1024+0 poster ut
1073741824 byte (1,1 GB) kopierade, 4,5668 s, 235 MB/s

```

And now I'm stuck. Is the PC too slow to handle traffic faster than 5MB/s, even though i'm only using 6% of the RAM and hardly any cpu at all? 

This is the output from ifconfig (eth0 is connected to the router, eth1 to the desktop) 
```
ifconfig -a
eth0      Link encap:Ethernet  HWaddr f4:6d:04:5f:b5:e6
          inet addr:192.168.0.100  Bcast:0.0.0.0  Mask:255.255.255.0
          inet6 addr: fe80::f66d:4ff:fe5f:b5e6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1287021 errors:0 dropped:0 overruns:0 frame:0
          TX packets:504199 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:993459426 (993.4 MB)  TX bytes:68990096 (68.9 MB)
          Interrupt:43 Base address:0xe000

eth1      Link encap:Ethernet  HWaddr 68:05:ca:03:4d:90
          inet addr:10.0.0.1  Bcast:10.0.3.255  Mask:255.255.252.0
          inet6 addr: fe80::6a05:caff:fe03:4d90/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:73522212 errors:0 dropped:4960 overruns:0 frame:0
          TX packets:4197350 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:109989241001 (109.9 GB)  TX bytes:1224681913 (1.2 GB)
          Interrupt:16 Minne:fbfe0000-fc000000

```. 

Just to clarify i'm running Ubuntu server 11.10 64bit and the Latest NIC driver from Intel. 

It seems that i doesn't matter if the file transfer is through Samba or sftp, the speed is the same. 

What can I do next? I'm really stuck.. :confused:

---

### Post by amuh on 2012-03-03
Update and bump! 

It seems that even the integrated nic is slow.

Could it be a problem with the driver?? Even after ive downloaded the latest ethernet driver from Intel (1.9.5) the speed is still stuck at 5MB/s and up to 6Mb/s. With the same cable connected straight to my laptop i get speed 35-45Mb/s. Is it Ubuntu related? Or is it Intel having bad drivers and I should return the NIC?

---

### Post by praseodym on 2012-03-03
What devices are they?

> lspci -nnk | grep -iA2 net
lsmod
please.

---

### Post by amuh on 2012-03-03
lspci -nnk | grep -iA2 net
gives me:
```
lspci -nnk | grep -iA2 net
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)
        Subsystem: ASUSTeK Computer Inc. P8P67 and other motherboards [1043:8432]
        Kernel driver in use: r8169
--
04:00.0 Ethernet controller [0200]: Intel Corporation 82574L Gigabit Network Connection [8086:10d3]
        Subsystem: Intel Corporation Gigabit CT Desktop Adapter [8086:a01f]
        Kernel driver in use: e1000e

```
and lsmod results in 
```
 lsmod
Module                  Size  Used by
vboxnetadp             13382  0
vboxnetflt             28302  0
vboxdrv               268186  2 vboxnetadp,vboxnetflt
ppdev                  17113  0
snd_hda_codec_via      71209  1
snd_hda_intel          33390  0
snd_hda_codec         104802  2 snd_hda_codec_via,snd_hda_intel
snd_hwdep              13613  1 snd_hda_codec
snd_pcm                96755  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0
psmouse                73882  0
serio_raw              13166  0
snd_rawmidi            30547  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
asus_atk0110           18078  0
parport_pc             36962  1
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
i915                  566658  1
drm_kms_helper         42558  1 i915
drm                   236330  2 i915,drm_kms_helper
snd                    68182  9 snd_hda_codec_via,snd_hda_intel,snd_hda_codec,sn                      d_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i2c_algo_bit           13423  1 i915
video                  19412  1 i915
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
lp                     17799  0
parport                46562  3 ppdev,parport_pc,lp
ahci                   26002  2
libahci                26861  1 ahci
r8169                  52788  0
e1000e                160535  0

```

---

### Post by praseodym on 2012-03-03
Ok,

some more infos, please:

```
cat /etc/udev/rules.d/70-persistent-net.rules
cat /etc/network/interfaces
cat /etc/resolv.conf
route -n
```
Install the package "ethtool" and show additionally:

```
sudo ethtool eth0
sudo ethtool eth1
```

---

### Post by amuh on 2012-03-03
Ok, here goes
cat /etc/udev/rules.d/70-persistent-net.rules
```
cat /etc/udev/rules.d/70-persistent-net.rules
# This file was automatically generated by the /lib/udev/write_net_rules
# program, run by the persistent-net-generator.rules rules file.
#
# You can modify it, as long as you keep each rule on a single
# line, and change only the value of the NAME= key.

# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="f4:6d:04:5f:b5:e6", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x8086:0x10d3 (e1000e)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="68:05:ca:03:4d:90", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"
```


cat /etc/network/interfaces
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
address 192.168.0.100
netmask 255.255.255.0
gateway 192.168.0.1

auto eth1
iface eth1 inet static
#address 192.168.0.101
#network 192.168.0.0
#broadcast 192.168.0.255
address 10.0.0.2
network 10.0.0.0
netmask 255.255.252.0
broadcast 10.0.0.255
```


cat /etc/resolv.conf
```

cat /etc/resolv.conf
nameserver 192.168.0.1
```

route -n
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    100    0        0 eth0
10.0.0.0        0.0.0.0         255.255.252.0   U     0      0        0 eth1
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
```

ethtool output
```
Settings for eth0:
        Supported ports: [ TP MII ]
        Supported link modes:   10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
                                1000baseT/Half 1000baseT/Full
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
                                1000baseT/Half 1000baseT/Full
        Advertised pause frame use: Symmetric Receive-only
        Advertised auto-negotiation: Yes
        Link partner advertised link modes:  10baseT/Half 10baseT/Full
                                             100baseT/Half 100baseT/Full
                                             1000baseT/Full
        Link partner advertised pause frame use: Symmetric Receive-only
        Link partner advertised auto-negotiation: Yes
        Speed: 1000Mb/s
        Duplex: Full
        Port: MII
        PHYAD: 0
        Transceiver: internal
        Auto-negotiation: on
        Supports Wake-on: pumbg
        Wake-on: g
        Current message level: 0x00000033 (51)
                               drv probe ifdown ifup
        Link detected: yes



Settings for eth1:
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
        Speed: 1000Mb/s
        Duplex: Full
        Port: Twisted Pair
        PHYAD: 1
        Transceiver: internal
        Auto-negotiation: on
        MDI-X: on
        Supports Wake-on: pumbg
        Wake-on: g
        Current message level: 0x00000001 (1)
                               drv
        Link detected: yes
```

---

### Post by praseodym on 2012-03-03
Try to shut off the auto-negotiation of each card:

```
sudo ethtool -s eth0 speed 1000 autoneg off
sudo ethtool -s eth1 speed 1000 autoneg off
sudo /etc/init.d/networking restart
```
Reversible with "on" instead of "off". Did you set the route for eth1? Changed "false" to "true" in the **/etc/NetworkManager/nm-system-settings.conf**

---

### Post by amuh on 2012-03-03
Hmm, no. Ive not set the route on eth1, just set the ip and such. And it seems that autoneg off doesn't work. It doesnt render an error or such, the value off just doesn't seem to "catch"

---

### Post by praseodym on 2012-03-03
Cable/switch can handle Gigabit? Router, too?

---

### Post by amuh on 2012-03-03
> **praseodym said:**
> Cable/switch can handle Gigabit? Router, too?

Yeah, the cables are of type Cat6/Cat5e and the router has the capacity to handle 1Gigabit. I even used a crossover cable to connect my laptop/desktop straight to the NAS and the speed reaches 6Mb/s at most

I just noticed that traffic TO the server is around 4-6Mb/s and traffic from the server is around 10-12Mb/s. What could that mean?

---

### Post by Sergius14 on 2012-03-05
I been working a couple of years in networking and infrastructure.

It is very difficult to handle 1 Gbit (or more) with standard computers, even most "enterprise servers", but not impossible.

There is a couple of reasons that you have to keep in mind:

Disk speed (already tested)
Bus Speed (sometimes there are very low north/south bridges with very low buses).
The NIC can't handle the speed... (chipset/bus limits)

I this moment a I have a HP ProLiant G6 with a Raid 5 i can't have more than 250/350 mbps. Not only disks are taken inplace, but also internal buses (from raid controller to nic, etc.).


For example:

Running Iperf on a Laptop, I got 1 Gbit using TCP.... and 300 using UDP. in real life it is imposible due disk speed. When runing UDP (depending combinations), CPU went 100%....

Also could be a limit of the nic chipset (almost imposible to find out or measure).


250/350 mbps are the most common values  that I found in standard computing.

---

### Post by RoosterHam on 2012-05-13
Just today I have come across a similar situation in which factors within 2 hosts is limiting actual transfer compared to theoretical. That said I am still getting 26MB/s over my gigabit link.

My home network consists of a desktop system, a desktop set up as a media centre, a server (so far just samba file shares), a wireless n router and several laptops and mobiles that connect via wifi. the desktop, media centre and server all have on-board 100Mbps Ethernet controllers, and the router's wired ports are 100Mbps.

All my movies and music are stored on the samba server and duplicated on the desktop for insurance. while 100Mbps is plenty to play files on the MC directly from the samba share, moving anything over 50GB was an arduous wait, the initial backup took close to 19 hours.

So I added two PCI gigabit nics, one in the server, one in the desktop, crossover cable directly between hosts, and a static route and /etc/hosts addition both sides. Also note disks involved are all sata2, each drive being 1TB, the server being raid array+LVM smallest practical physical partition size, the desktop being basic guid partitions on jbod.

Actual transfer rate is sitting at 26MB/s, while sata2, pci bus, and ethernet are all capable of over 125MB/s.

Factors that come to mind are overhead involved in each step of the transfer, the lack of any tweaking/optimising of hard drives, nics or samba itself, the slow spin speed of the large capacity drives and using pci bus rather than pci-e/pci-x.

Yet the 26MB/s I'm getting is well above the 6MB/s you are seeing...

---

### Post by Yfrwlf on 2012-07-15
> **RoosterHam said:**
> Just today I have come across a similar situation in which factors within 2 hosts is limiting actual transfer compared to theoretical. That said I am still getting 26MB/s over my gigabit link.

My home network consists of a desktop system, a desktop set up as a media centre, a server (so far just samba file shares), a wireless n router and several laptops and mobiles that connect via wifi. the desktop, media centre and server all have on-board 100Mbps Ethernet controllers, and the router's wired ports are 100Mbps.

All my movies and music are stored on the samba server and duplicated on the desktop for insurance. while 100Mbps is plenty to play files on the MC directly from the samba share, moving anything over 50GB was an arduous wait, the initial backup took close to 19 hours.

So I added two PCI gigabit nics, one in the server, one in the desktop, crossover cable directly between hosts, and a static route and /etc/hosts addition both sides. Also note disks involved are all sata2, each drive being 1TB, the server being raid array+LVM smallest practical physical partition size, the desktop being basic guid partitions on jbod.

Actual transfer rate is sitting at 26MB/s, while sata2, pci bus, and ethernet are all capable of over 125MB/s.

Factors that come to mind are overhead involved in each step of the transfer, the lack of any tweaking/optimising of hard drives, nics or samba itself, the slow spin speed of the large capacity drives and using pci bus rather than pci-e/pci-x.

Yet the 26MB/s I'm getting is well above the 6MB/s you are seeing...

Having the same problems and have always been curious about all this.  All I know is that typically a similar desktop (slower, actually) commonly gets speeds of around 30 MB/sec doing file transfers in Windows to and from a Linux server, yet Linux to and from Linux is 1/3rd the speed, around 12 MB/sec.  Clearly some more tests are needed to find where the bottleneck is.

Swap out various layers of the software stack.  Try different types of file transfers: SSH, NFS, FTP, HTTP, SMB.  Try different versions of Linux, and try Windows.  It might be wise to use a timer to get the file transfer rate instead of relying on various programs.  Try different computers, different cables, etc, though if you make any software stack changes and see drastically different speeds there won't be a need to test hardware.

---

