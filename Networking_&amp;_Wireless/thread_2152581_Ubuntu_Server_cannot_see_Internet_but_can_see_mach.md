---
title: "Ubuntu Server cannot see Internet but can see machines on local network"
date: 2013-06-08
forum: Networking &amp; Wireless
---

### Post by MarcusL on 2013-06-08
UPDATE:
Fresh installation Ubuntu 12.04 solved the issue

*****************************************************

Hi all,
I thought of upgrading my Ubuntu server to latest release (it is used as a backup / movie server only, so no GUI on it, command line only) and today I realise (after 2 years running it) that it will not see/ping any external addresses beyond the Gateway (192.160.0.1). I have edited etc/resolv.conf

```

nameserver 192.168.0.1
nameserver 61.9.195.193
nameserver 61.9.207.1

```

When I ping (say Yahoo.com) I get no replies (it just hangs, although the IP is resolved - 206.190.36.45). When I ping same site from one of the Win PCs it replies OK (so firewall/router/modem not stopping ping).
ifconfig is as follows:

```

bond0     Link encap:Ethernet  HWaddr 00:1b:fc:6a:c2:79
          inet addr:192.168.0.31  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:fcff:fe6a:c279/64 Scope:Link
          UP BROADCAST RUNNING MASTER MULTICAST  MTU:1500  Metric:1
          RX packets:60508 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:5266023 (5.2 MB)  TX bytes:468 (468.0 B)


eth0      Link encap:Ethernet  HWaddr 00:1b:fc:6a:d1:00
          inet addr:192.168.0.198  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:fcff:fe6a:d100/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:17954617 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4229235 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:21571837170 (21.5 GB)  TX bytes:9053079394 (9.0 GB)
          Interrupt:17


eth1      Link encap:Ethernet  HWaddr 00:1b:fc:6a:c2:79
          UP BROADCAST RUNNING SLAVE MULTICAST  MTU:1500  Metric:1
          RX packets:60508 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:5266023 (5.2 MB)  TX bytes:468 (468.0 B)
          Interrupt:16 Base address:0xac00


lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1736 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1736 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:114176 (114.1 KB)  TX bytes:114176 (114.1 KB)



```

Can anybody help me understand why the network is working OK peer to peer but the server cannot reach outside?

There is only one firewall in the place and that is on my DLink router.

Thanks in advance!

---

### Post by praseodym on 2013-06-08
Hi,

what kind of hardware is in use? Please show:
```

uname -a
lspci -nnk | grep -iA2 net
lsmod
cat /etc/network/interfaces
dmesg | egrep 'eth0|eth1'
cat /etc/udev/rules.d/70-persistent-net.rules
route -n
```

---

### Post by MarcusL on 2013-06-08
Hi praseodym
Thanks for the reply. Here's the info you requested.

uname -a
```

Linux LSERVER 2.6.38-11-server #48-Ubuntu SMP Fri Jul 29 19:20:32 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux

```

lspci -nnk | grep -iA2 net
```

02:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8056 PCI-E Gigabit Ethernet Controller [11ab:4364] (rev 12)
        Subsystem: ASUSTeK Computer Inc. Device [1043:81f8]
        Kernel driver in use: sky2
--
05:04.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8110SC/8169SC Gigabit Ethernet [10ec:8167] (rev 10)
        Subsystem: ASUSTeK Computer Inc. Device [1043:820d]
        Kernel driver in use: r8169



```

lsmod
```

Module                  Size  Used by
bonding               113742  0
snd_hda_codec_hdmi     28167  1
arc4                   12529  2
rtl8187                60982  0
mac80211              290274  1 rtl8187
snd_hda_codec_analog    98042  1
radeon                982152  1
cfg80211              178528  2 rtl8187,mac80211
eeprom_93cx6           12725  1 rtl8187
hid_a4tech             12678  0
snd_hda_intel          33176  0
ttm                    76664  1 radeon
snd_hda_codec         103768  3 snd_hda_codec_hdmi,snd_hda_codec_analog,snd_hda_intel
snd_hwdep              13604  1 snd_hda_codec
snd_pcm                96297  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
drm_kms_helper         42136  1 radeon
snd_timer              29602  1 snd_pcm
serio_raw              13166  0
snd                    67346  7 snd_hda_codec_hdmi,snd_hda_codec_analog,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_timer
soundcore              12680  1 snd
drm                   227498  3 radeon,ttm,drm_kms_helper
i2c_algo_bit           13400  1 radeon
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
asus_atk0110           17976  0
lp                     17789  0
parport                46458  1 lp
raid10                 30673  0
raid456                62777  1
async_pq               12995  1 raid456
async_xor              12879  2 raid456,async_pq
xor                    12890  1 async_xor
async_memcpy           12529  1 raid456
async_raid6_recov      12776  1 raid456
firewire_ohci          40370  0
firewire_core          62646  1 firewire_ohci
usbhid                 46956  0
hid                    91020  2 hid_a4tech,usbhid
r8169                  48022  0
crc_itu_t              12707  1 firewire_core
mptsas                 59148  4
mptscsih               44457  1 mptsas
mptbase               102904  2 mptsas,mptscsih
ahci                   25951  0
libahci                26642  1 ahci
floppy                 74120  0
pata_jmicron           12747  2
scsi_transport_sas     40545  1 mptsas
sky2                   58509  0
raid6_pq               88307  2 async_pq,async_raid6_recov
async_tx               13349  5 raid456,async_pq,async_xor,async_memcpy,async_raid6_recov
raid1                  30596  0
raid0                  17271  0
multipath              13187  0
linear                 12966  0

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
iface eth0 inet dhcp


auto bond0
 iface bond0 inet static
 address  192.168.0.31
 gateway  192.168.0.1
 netmask  255.255.255.0
 bond-slaves eth1
# LACP configuration
 bond_mode balance-rr
 bond_miimon  100
 bond_lacp_rate 1

```


dmesg | egrep 'eth0|eth1'
```



[    2.269040] sky2 0000:02:00.0: eth0: addr 00:1b:fc:6a:d1:00
[    2.279180] r8169 0000:05:04.0: eth1: RTL8169sc/8110sc at 0xffffc90000c7ac00, 00:1b:fc:6a:c2:79, XID 18000000 IRQ 16
[    7.755707] sky2 0000:02:00.0: eth0: enabling interface
[    7.756446] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   10.484309] sky2 0000:02:00.0: eth0: Link is up at 1000 Mbps, full duplex, flow control both
[   10.485003] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   21.192013] bonding: bond0: Adding slave eth1.
[   21.195289] r8169 0000:05:04.0: eth1: link down
[   21.196387] r8169 0000:05:04.0: eth1: link up
[   21.197415] r8169 0000:05:04.0: eth1: link down
[   21.198590] bonding: bond0: enslaving eth1 as an active interface with a down link.
[   21.230012] eth0: no IPv6 routers present
[   23.514182] r8169 0000:05:04.0: eth1: link up
[   23.610586] bonding: bond0: link status definitely up for interface eth1, 1000 Mbps full duplex.

```


cat /etc/udev/rules.d/70-persistent-net.rules
```

# This file was automatically generated by the /lib/udev/write_net_rules
# program, run by the persistent-net-generator.rules rules file.
#
# You can modify it, as long as you keep each rule on a single
# line, and change only the value of the NAME= key.


# PCI device 0x10ec:0x8167 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:1b:fc:6a:c2:79", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"


# PCI device 0x11ab:0x4364 (sky2)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:1b:fc:6a:d1:00", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


# USB device 0x0bda:0x8187 (usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:15:af:19:ec:28", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

```

rounte -n
```



Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 bond0
0.0.0.0         192.168.0.1     0.0.0.0         UG    100    0        0 bond0
0.0.0.0         192.168.0.1     0.0.0.0         UG    100    0        0 eth0



```

Thanks again.
M

---

### Post by praseodym on 2013-06-09
What about the eth1 config?

---

### Post by MarcusL on 2013-06-09
Sorry praseodym, I do not understand the question. 

Are you referring to "eth1:link down" above? The last message on eth1 is "link status definitely up" on the bond0 statement.

Sorry, but I am not an experienced Linux person, but learning fast!

By the way, I have another thread going for an issue where the server has poor performance and timeouts on RAID6 array. I am sure these two issues are not related, but just in case! [http://ubuntuforums.org/showthread.php?t=2152585](http://ubuntuforums.org/showthread.php?t=2152585)

Thanks!
M

---

### Post by praseodym on 2013-06-10
Are the following packages installed?
```

sudo apt-get install ifenslave-2.6 net-tools ethtool bmon
```
Please show:
```

sudo mii-tools
modprobe --list | grep -i bonding 
find /lib/modules/`uname -r` -iname bonding* 
```
Please google-translate the following page:

[http://wiki.ubuntuusers.de/Netzwerkkarten_b%C3%BCndeln?highlight=bond0](http://wiki.ubuntuusers.de/Netzwerkkarten_b%C3%BCndeln?highlight=bond0)

You can find config examples there in the grey boxes. Obviously, the eth0 config is not necessary.

Or here in english:
[https://help.ubuntu.com/community/UbuntuBonding](https://help.ubuntu.com/community/UbuntuBonding)

---

