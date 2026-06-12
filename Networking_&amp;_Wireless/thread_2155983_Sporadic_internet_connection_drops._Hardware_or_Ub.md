---
title: "Sporadic internet connection drops. Hardware or Ubuntu OS?"
date: 2013-06-20
forum: Networking &amp; Wireless
---

### Post by roses100 on 2013-06-20
Hello,

Since this morning I have been experiencing sporadic drops in network connection, where I am unable to mount local drives and connect to the internet. To begin with the connection would be fine for about 5 minutes, then drop again, then fine again for another 5 minutes, culminating to a permanant drop after about 15 minutes. I then proceeded to reboot and found it wouldn't connect at all. I then rebooted into recovery mode to see if I could connect to the network, and it failed with a message along the lines of Errror 101 network could not be found.

I then proceeded to boot into an older version of Ubuntu on the same computer and was able to connect to the internet fine and the connection was stable. I then booted out and back into the version I'm having problems with 12.04 LTS and now it is working again, the connection seems to be stable for now. Unfortunately I was unable to capture the ifconfig output to paste into this post when it wasn't working.

The current ifconfig output with working internet connection:

eth1      Link encap:Ethernet  HWaddr 00:17:31:e9:cd:fd  
          inet addr:192.168.0.199  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::217:31ff:fee9:cdfd/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:11785 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8698 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:11697908 (11.6 MB)  TX bytes:1173993 (1.1 MB)
          Interrupt:44 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:764 errors:0 dropped:0 overruns:0 frame:0
          TX packets:764 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:72975 (72.9 KB)  TX bytes:72975 (72.9 KB)

I have been using Ubuntu 12.04 LTS for about a year and have had no problems untill now. I have not installed any updates since fresh install and I haven't installed any new programs either in the last week, so nothing really has changed.

I am certain that this is a software issue, due to the fact I am able to mount local network drives and connect to the internet on a previous Ubuntu version which I can boot into from the same computer.

I am connecting via a wired connection, the cable seems fine and there are lights where there should be. Other people on the same network hasn't been having the same issue, so I am certain it's not to do with my local area network set up.

Could this be a sign of the hardware failing? Or is there something I can do in Ubuntu to stop this from happening again, or would it be better to just install a new version of Ubuntu?

UPDATE: Actually it's started dropping again not long after this post, but the drops only last for a few seconds before it connects again. When it does drop it does it multiple times in quick succession, and doesn't seem to have a pattern.

UPDATE: Here is the output of ifconfig when the connection does drop:

ifconfig
eth1      Link encap:Ethernet  HWaddr 00:17:31:e9:cd:fd  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:64224 errors:0 dropped:0 overruns:0 frame:0
          TX packets:53731 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:61051339 (61.0 MB)  TX bytes:18827337 (18.8 MB)
          Interrupt:44 Base address:0x8000 


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4012 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4012 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:358213 (358.2 KB)  TX bytes:358213 (358.2 KB)



Thanks!

---

### Post by praseodym on 2013-06-20
Please show these outputs:
```

lspci -nnk | grep -iA2 net
lsusb
lsmod
ifconfig -a
iwconfig
cat /etc/udev/rules.d/70-persistent-net.rules
cat /etc/resolv.conf
route -n
```

---

### Post by roses100 on 2013-06-20
Thanks for responding, here are the outputs (connection working at the time). I'm not quick enough to grab the outputs when the connection drops. Please view the original post to see the output of ifconfig when the connection drops.


**lspci -nnk | grep -iA2 net**
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 01)
    Subsystem: ASUSTeK Computer Inc. Device [1043:8168]
    Kernel driver in use: r8169


**lsusb**
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 0424:2504 Standard Microsystems Corp. USB 2.0 Hub
Bus 002 Device 003: ID 058f:6254 Alcor Micro Corp. USB Hub
Bus 002 Device 004: ID 046d:c245 Logitech, Inc. 
Bus 002 Device 005: ID 0b38:0010 Gear Head 107-Key Keyboard


**lsmod**
Module                  Size  Used by
des_generic            21415  0 
md4                    12595  0 
pci_stub               12622  1 
vboxpci                23200  0 
vboxnetadp             13382  0 
vboxnetflt             23441  0 
vboxdrv               287082  3 vboxpci,vboxnetadp,vboxnetflt
bnep                   18281  2 
rfcomm                 47604  0 
bluetooth             180104  10 bnep,rfcomm
nls_utf8               12557  1 
cifs                  287317  2 
binfmt_misc            17540  1 
vesafb                 13844  1 
snd_hda_codec_analog    97987  1 
joydev                 17693  0 
ppdev                  17113  0 
snd_hda_intel          33773  2 
snd_hda_codec         127706  2 snd_hda_codec_analog,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                97188  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
nvidia              11257276  54 
asus_atk0110           18078  0 
parport_pc             32866  1 
mac_hid                13253  0 
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
psmouse                87692  0 
serio_raw              13211  0 
snd                    78855  13 snd_hda_codec_analog,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
lp                     17799  0 
parport                46562  3 ppdev,parport_pc,lp
usbhid                 47199  0 
hid                    99559  1 usbhid
pata_jmicron           12747  0 
floppy                 70365  0 
r8169                  62099  0


**ifconfig -a**
eth1      Link encap:Ethernet  HWaddr 00:17:31:e9:cd:fd  
          inet addr:192.168.0.199  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::217:31ff:fee9:cdfd/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:41974 errors:0 dropped:0 overruns:0 frame:0
          TX packets:35290 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:37653766 (37.6 MB)  TX bytes:16182434 (16.1 MB)
          Interrupt:44 Base address:0x8000 


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3237 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3237 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:282124 (282.1 KB)  TX bytes:282124 (282.1 KB)


**iwconfig**
lo        no wireless extensions.


eth1      no wireless extensions.


**cat /etc/udev/rules.d/70-persistent-net.rules**
# This file was automatically generated by the /lib/udev/write_net_rules
# program, run by the persistent-net-generator.rules rules file.
#
# You can modify it, as long as you keep each rule on a single
# line, and change only the value of the NAME= key.


# PCI device 0x8086:/sys/devices/pci0000:00/0000:00:03.0 (e1000)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="08:00:27:c8:95:48", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:1c.3/0000:03:00.0 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:17:31:e9:cd:fd", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"


**cat /etc/resolv.conf**
# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN
nameserver 127.0.0.1


**route -n**
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.18    0.0.0.0         UG    0      0        0 eth1
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth1
192.168.0.0     0.0.0.0         255.255.255.0   U     1      0        0 eth1

---

### Post by praseodym on 2013-06-20
Replace the driver:
```

sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic build-essential dkms
wget http://media.cdn.ubuntu-de.org/forum/attachments/11/02/3005217-r8168-dkms-8.035.00.tar.gz
sudo tar xvf 3005217-r8168-dkms-8.035.00.tar.gz -C /usr/src
sudo dkms add -m r8168-dkms -v 8.035.00
sudo dkms build -m r8168-dkms -v 8.035.00
sudo dkms install -m r8168-dkms -v 8.035.00 
echo "blacklist r8169" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
Reboot.

---

### Post by roses100 on 2013-06-20
I've followed your instructions but unfortunately the connection drops are still happening :( They only last a few seconds but it's quite frequent in the space of every 10/15 minutes when it does happen, although still sporadic, so I may sometimes have half an hour with a stable connection.

---

### Post by praseodym on 2013-06-20
Ok, lets check:
```

sudo apt-get install ethtool
sudo ethtool eth1
ifconfig -a
dmesg | grep r8
```

---

### Post by roses100 on 2013-06-20
Here are the outputs following your suggestion:

**sudo ethtool eth1**
Settings for eth1:
    Supported ports: [ TP MII ]
    Supported link modes:   10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Half 1000baseT/Full 
    Supported pause frame use: No
    Supports auto-negotiation: Yes
    Advertised link modes:  10baseT/Half 10baseT/Full 
                            100baseT/Half 100baseT/Full 
                            1000baseT/Half 1000baseT/Full 
    Advertised pause frame use: Symmetric Receive-only
    Advertised auto-negotiation: Yes
    Link partner advertised link modes:  10baseT/Half 10baseT/Full 
                                         100baseT/Half 100baseT/Full 
                                         1000baseT/Half 1000baseT/Full 
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

**ifconfig -a**
eth1      Link encap:Ethernet  HWaddr 00:17:31:e9:cd:fd  
          inet addr:192.168.0.199  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::217:31ff:fee9:cdfd/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:75119 errors:0 dropped:0 overruns:0 frame:0
          TX packets:63924 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:89876128 (89.8 MB)  TX bytes:9013361 (9.0 MB)
          Interrupt:44 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4886 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4886 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:474795 (474.7 KB)  TX bytes:474795 (474.7 KB)
[B]
dmesg | grep r8[/B]
[    0.000000] PERCPU: Embedded 28 pages/cpu @ffff8801ffc00000 s83072 r8192 d23424 u524288
[    0.000000] pcpu-alloc: s83072 r8192 d23424 u524288 alloc=1*2097152
[    3.283817] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    3.283839] r8169 0000:03:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    3.283869] r8169 0000:03:00.0: setting latency timer to 64
[    3.283938] r8169 0000:03:00.0: irq 44 for MSI/MSI-X
[    3.284371] r8169 0000:03:00.0: eth0: RTL8168b/8111b at 0xffffc90000c64000, 00:17:31:e9:cd:fd, XID 10000000 IRQ 44
[    3.284374] r8169 0000:03:00.0: eth0: jumbo features [frames: 4080 bytes, tx checksumming: ko]
[   26.092178] r8169 0000:03:00.0: eth1: link down
[   26.092185] r8169 0000:03:00.0: eth1: link down
[   28.454969] r8169 0000:03:00.0: eth1: link up
[  178.737684] r8169 0000:03:00.0: eth1: link down
[  181.963197] r8169 0000:03:00.0: eth1: link up
[  202.489320] r8169 0000:03:00.0: eth1: link down
[  205.548427] r8169 0000:03:00.0: eth1: link up
[  293.485678] r8169 0000:03:00.0: eth1: link down
[  296.599172] r8169 0000:03:00.0: eth1: link up
[  337.920328] r8169 0000:03:00.0: eth1: link down
[  341.074202] r8169 0000:03:00.0: eth1: link up
[  344.718499] r8169 0000:03:00.0: eth1: link down
[  351.652055] r8169 0000:03:00.0: eth1: link up
[  489.119316] r8169 0000:03:00.0: eth1: link down
[  492.158566] r8169 0000:03:00.0: eth1: link up
[  561.816735] r8169 0000:03:00.0: eth1: link down
[  564.847671] r8169 0000:03:00.0: eth1: link up
[  658.402174] r8169 0000:03:00.0: eth1: link down
[  661.577816] r8169 0000:03:00.0: eth1: link up
[  663.652922] r8169 0000:03:00.0: eth1: link down
[  666.696528] r8169 0000:03:00.0: eth1: link up
[  801.194967] r8169 0000:03:00.0: eth1: link down
[  804.345753] r8169 0000:03:00.0: eth1: link up
[  810.540403] r8169 0000:03:00.0: eth1: link down
[  813.590911] r8169 0000:03:00.0: eth1: link up
[  827.999197] r8169 0000:03:00.0: eth1: link down
[  834.771174] r8169 0000:03:00.0: eth1: link up
[  848.793119] r8169 0000:03:00.0: eth1: link down
[  851.837285] r8169 0000:03:00.0: eth1: link up
[  933.410214] r8169 0000:03:00.0: eth1: link down
[  936.470369] r8169 0000:03:00.0: eth1: link up
[  960.832490] r8169 0000:03:00.0: eth1: link down
[  963.981849] r8169 0000:03:00.0: eth1: link up
[ 1004.675125] r8169 0000:03:00.0: eth1: link down
[ 1007.734393] r8169 0000:03:00.0: eth1: link up
[ 1026.381063] r8169 0000:03:00.0: eth1: link down
[ 1029.516843] r8169 0000:03:00.0: eth1: link up
[ 1066.208611] r8169 0000:03:00.0: eth1: link down
[ 1069.231472] r8169 0000:03:00.0: eth1: link up
[ 1197.063056] r8169 0000:03:00.0: eth1: link down
[ 1200.092316] r8169 0000:03:00.0: eth1: link up
[ 1318.459348] r8169 0000:03:00.0: eth1: link down
[ 1395.249202] r8169 0000:03:00.0: eth1: link down
[ 1402.048889] r8169 0000:03:00.0: eth1: link up
[ 1428.399189] r8169 0000:03:00.0: eth1: link up
[ 1447.758868] r8169 0000:03:00.0: eth1: link down
[ 1451.053422] r8169 0000:03:00.0: eth1: link up
[ 1462.574784] r8169 0000:03:00.0: eth1: link down
[ 1465.654824] r8169 0000:03:00.0: eth1: link up
[ 1488.136128] r8169 0000:03:00.0: eth1: link down
[ 1491.167662] r8169 0000:03:00.0: eth1: link up
[ 1505.346616] r8169 0000:03:00.0: eth1: link down
[ 1508.413643] r8169 0000:03:00.0: eth1: link up
[ 1577.370049] r8169 0000:03:00.0: eth1: link down
[ 1580.726606] r8169 0000:03:00.0: eth1: link up
[ 1634.779599] r8169 0000:03:00.0: eth1: link down
[ 1637.841639] r8169 0000:03:00.0: eth1: link up
[ 1641.946616] r8169 0000:03:00.0: eth1: link down
[ 1648.732423] r8169 0000:03:00.0: eth1: link up
[ 1729.192036] r8169 0000:03:00.0: eth1: link down
[ 1732.339094] r8169 0000:03:00.0: eth1: link up
[ 1757.666125] r8169 0000:03:00.0: eth1: link down
[ 1760.859385] r8169 0000:03:00.0: eth1: link up
[ 1851.390487] r8169 0000:03:00.0: eth1: link down
[ 1854.479546] r8169 0000:03:00.0: eth1: link up
[ 1914.250012] r8169 0000:03:00.0: eth1: link down
[ 1917.357127] r8169 0000:03:00.0: eth1: link up
[ 1965.957924] r8169 0000:03:00.0: eth1: link down
[ 1969.069757] r8169 0000:03:00.0: eth1: link up
[ 1973.743603] r8169 0000:03:00.0: eth1: link down
[ 1976.870082] r8169 0000:03:00.0: eth1: link up
[ 1979.405914] r8169 0000:03:00.0: eth1: link down
[ 1982.490035] r8169 0000:03:00.0: eth1: link up
[ 1992.156603] r8169 0000:03:00.0: eth1: link down
[ 1999.059002] r8169 0000:03:00.0: eth1: link up
[ 2006.834047] r8169 0000:03:00.0: eth1: link down
[ 2009.877407] r8169 0000:03:00.0: eth1: link up
[ 2015.231083] r8169 0000:03:00.0: eth1: link down
[ 2018.311592] r8169 0000:03:00.0: eth1: link up
[ 2028.704153] r8169 0000:03:00.0: eth1: link down
[ 2031.696623] r8169 0000:03:00.0: eth1: link up

---

### Post by praseodym on 2013-06-20
Ok, try to "ignore" IPv6 in the network-manager applet. Additionally, please try
```

sudo ethtool -s eth1 speed 1000 autoneg off
```

---

### Post by roses100 on 2013-06-20
Hmmm, I'm getting this, any ideas?

sudo ethtool -s eth1 speed 1000 autoneg off
Cannot set new settings: Invalid argument
  not setting speed
  not setting autoneg

---

### Post by praseodym on 2013-06-20
Did you install the r8168 driver? r8169 is still loaded?! If yes:
```

sudo modprobe -rfv r8169
sudo modprobe -v r8168
```

---

### Post by roses100 on 2013-06-20
Cool I was able to run sudo ethtool -s eth1 speed 1000 autoneg off. Do I need to reboot?

---

### Post by praseodym on 2013-06-20
You may want to check which driver is automatically loaded at boot-up:

**lsmod**

---

### Post by roses100 on 2013-06-20
I have rebooted, and the connection dropped as soon as I logged in. Here is the output after booting back in:

**lsmod**
Module                  Size  Used by
des_generic            21415  0 
md4                    12595  0 
pci_stub               12622  1 
vboxpci                23200  0 
vboxnetadp             13382  0 
vboxnetflt             23441  0 
vboxdrv               287082  3 vboxpci,vboxnetadp,vboxnetflt
rfcomm                 47604  0 
vesafb                 13844  1 
bnep                   18281  2 
bluetooth             180104  10 rfcomm,bnep
binfmt_misc            17540  1 
nls_utf8               12557  1 
cifs                  287317  2 
snd_hda_codec_analog    97987  1 
joydev                 17693  0 
ppdev                  17113  0 
nvidia              11257276  30 
psmouse                87692  0 
serio_raw              13211  0 
snd_hda_intel          33773  2 
snd_hda_codec         127706  2 snd_hda_codec_analog,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                97188  2 snd_hda_intel,snd_hda_codec
parport_pc             32866  1 
asus_atk0110           18078  0 
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    78855  13 snd_hda_codec_analog,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
mac_hid                13253  0 
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
lp                     17799  0 
parport                46562  3 ppdev,parport_pc,lp
usbhid                 47199  0 
hid                    99559  1 usbhid
pata_jmicron           12747  0 
r8169                  62099  0 
floppy                 70365  0

---

### Post by praseodym on 2013-06-20
Open the file:
```

gksu gedit /etc/rc.local
```
and add these lines right before "exit 0":
```

modprobe -rf r8169
modprobe r8168
```
Save, close the editor and reboot.

---

### Post by roses100 on 2013-06-20
Have just rebooted after doing latest suggestion, and the connection dropped again within 5 minutes of logging in :(

---

### Post by praseodym on 2013-06-20
Now the "ethtool" command?!

---

### Post by roses100 on 2013-06-20
I ran the 'sudo ethtool -s eth1 speed 1000 autoneg off' command post boot and it's still doing it. Damn. I'm pretty much considering reinstalling Ubuntu with the latest version tomorrow if you're out of ideas. Thanks for all your help so far, I appreciate it :) I'll keep you updated.

---

### Post by praseodym on 2013-06-20
Which kernel is in use?
[B]
uname -a[/B]

---

### Post by roses100 on 2013-06-21
**uname -a**
Linux my-pc 3.2.0-29-generic #46-Ubuntu SMP Fri Jul 27 17:03:23 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

I logged into my old copy of Ubuntu for an hour and the drops are happening to that version aswell, so I'm starting to think perhaps the network card is on it's way out or someting.

---

### Post by praseodym on 2013-06-21
Or the cable...

---

### Post by roses100 on 2013-06-21
I have tried a different cable and booted into both Ubuntu 12.04 and the older version and the drops were still happening.

---

### Post by roses100 on 2013-06-24
Put in a brand new network card today and installed a fresh copy of Ubuntu, and the drops are not not happening any more. Thanks for all your help though!

---

