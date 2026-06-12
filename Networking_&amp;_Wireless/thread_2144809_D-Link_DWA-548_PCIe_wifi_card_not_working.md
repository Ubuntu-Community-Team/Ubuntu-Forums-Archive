---
title: "D-Link DWA-548 PCIe wifi card not working"
date: 2013-05-13
forum: Networking &amp; Wireless
---

### Post by Vpc on 2013-05-13
I just followed the instructions here:
[http://ubuntuforums.org/showthread.php?t=2071830](http://ubuntuforums.org/showthread.php?t=2071830)
I also have a "Custom Desktop PC with onboard lan (working) and a D-Link DWA-548 PCIe wi-Fi card that doesn't work and has no proprietary driver shown in the additional drivers tool." I was able to connect with my old wireless g D-Link network card but this new card I cannot see any wireless networks. 

Output of: sudo lshw -C network
```
  *-network               
       description: Ethernet interface
       product: 82579V Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth1
       version: 05
       serial: 38:60:77:d5:9b:27
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.5.1-k duplex=full firmware=0.13-4 ip=192.168.0.100 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:49 memory:fe700000-fe71ffff memory:fe728000-fe728fff ioport:f040(size=32)
  *-network DISABLED
       description: Wireless interface
       product: Ralink corp.
       vendor: Ralink corp.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: ra0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=RALINK WLAN latency=0 multicast=yes wireless=Ralink STA
       resources: irq:18 memory:fe500000-fe50ffff 

```

output of: iwconfig
```

lo        no wireless extensions.

eth1      no wireless extensions.

ra0       Ralink STA 

```

outut of: ifconfig
```

eth1      Link encap:Ethernet  HWaddr 38:60:77:d5:9b:27  
          inet addr:192.168.0.100  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::3a60:77ff:fed5:9b27/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1587 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1574 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1552453 (1.5 MB)  TX bytes:238681 (238.6 KB)
          Interrupt:20 Memory:fe700000-fe720000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:28 errors:0 dropped:0 overruns:0 frame:0
          TX packets:28 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2064 (2.0 KB)  TX bytes:2064 (2.0 KB)

```

output of: ls /etc/modprobe.d
```

alsa-base.conf          blacklist-firewire.conf     blacklist-modem.conf         blacklist-watchdog.conf  vmwgfx-fbdev.conf
blacklist-ath_pci.conf  blacklist-firewire.conf~    blacklist-oss.conf           dkms.conf
blacklist.conf          blacklist-framebuffer.conf  blacklist-rare-network.conf  fglrx.conf
```

output of: lsmod
```

Module                  Size  Used by
rt5390sta            1376719  0  
```

output of: lspci
```
 04:00.0 Network controller: Ralink corp. Device 5392
```

I also added 'blacklist rt2800pci' to the end of /etc/modprobe.d/blacklist.conf but still had the same problem.

---

### Post by praseodym on 2013-05-13
Please show:
```

lspci -nnk | grep -iA2 net
lsmod
modinfo rt5390sta
dmesg | egrep 'rt2|rt5'
sudo iwlist scan
ifconfig -a
iwlist chan
```

---

### Post by chili555 on 2013-05-13
> *-network [COLOR="#FF0000"]DISABLED[/COLOR]
       description: Wireless interface
       product: Ralink corp.
       vendor: Ralink corp.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: ra0We'd also love to see:```
dmesg | grep -e ra0 -e rt5 -e 04:00
```

---

### Post by Vpc on 2013-05-13
```
lspci -nnk | grep -iA2 net
00:19.0 Ethernet controller [0200]: Intel Corporation 82579V Gigabit Network Connection [8086:1503] (rev 05)
	Subsystem: Intel Corporation Device [8086:2006]
	Kernel driver in use: e1000e
--
04:00.0 Network controller [0280]: Ralink corp. Device [1814:5392]
	Subsystem: D-Link System Inc Device [1186:3c06]
	Kernel driver in use: rt2860
```


```
lsmod 
Module                  Size  Used by
parport_pc             32114  0 
ppdev                  12849  0 
rfcomm                 38139  0 
bnep                   17830  2 
bluetooth             158479  10 rfcomm,bnep
binfmt_misc            17292  1 
vesafb                 13516  1 
joydev                 17393  0 
hid_microsoft          12760  0 
usbhid                 41937  0 
hid                    77428  2 hid_microsoft,usbhid
snd_hda_codec_hdmi     31775  1 
snd_hda_codec_realtek   174313  1 
ip6t_LOG               16846  4 
xt_hl                  12465  6 
snd_hda_intel          32719  5 
snd_hda_codec         109562  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
ip6t_rt                12473  3 
snd_hwdep              13276  1 snd_hda_codec
nf_conntrack_ipv6      13581  7 
nf_defrag_ipv6         13175  1 nf_conntrack_ipv6
rt5390sta            1376719  0 
ipt_REJECT             12512  1 
snd_pcm                80916  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
ipt_LOG                12783  5 
xt_limit               12541  12 
xt_tcpudp              12531  24 
xt_addrtype            12596  4 
snd_seq_midi           13132  0 
xt_state               12514  14 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51592  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
ip6table_filter        12711  1 
ip6_tables             18432  3 ip6t_LOG,ip6t_rt,ip6table_filter
psmouse                86520  0 
serio_raw              13027  0 
nf_conntrack_netbios_ns    12585  0 
nf_conntrack_broadcast    12541  1 nf_conntrack_netbios_ns
nf_nat_ftp             12595  0 
nf_nat                 24959  1 nf_nat_ftp
nf_conntrack_ipv4      19084  9 nf_nat
nf_defrag_ipv4         12649  1 nf_conntrack_ipv4
nf_conntrack_ftp       13183  1 nf_nat_ftp
nf_conntrack           73847  8 nf_conntrack_ipv6,xt_state,nf_conntrack_netbios_ns,nf_conntrack_broadcast,nf_nat_ftp,nf_nat,nf_conntrack_ipv4,nf_conntrack_ftp
iptable_filter         12706  1 
ip_tables              18106  1 iptable_filter
x_tables               22011  13 ip6t_LOG,xt_hl,ip6t_rt,ipt_REJECT,ipt_LOG,xt_limit,xt_tcpudp,xt_addrtype,xt_state,ip6table_filter,ip6_tables,iptable_filter,ip_tables
fglrx                4323676  162 
snd                    62218  20 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
mac_hid                13077  0 
mei                    36570  0 
lp                     17455  0 
soundcore              14635  1 snd
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
parport                40930  3 parport_pc,ppdev,lp
firewire_ohci          40172  0 
firewire_core          56940  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
e1000e                140131  0 

```

```
modinfo rt5390sta
filename:       /lib/modules/3.2.0-41-generic-pae/kernel/drivers/net/wireless/rt5390sta.ko
version:        2.6.0.0
srcversion:     82742A8318611B38963E45B
alias:          pci:v00001186d00003C05sv*sd*bc*sc*i*
alias:          pci:v00001814d00005362sv*sd*bc*sc*i*
alias:          pci:v00001814d00005392sv*sd*bc*sc*i*
alias:          pci:v00001814d0000539Fsv*sd*bc*sc*i*
alias:          pci:v00001814d00005390sv*sd*bc*sc*i*
alias:          pci:v00001814d00003390sv*sd*bc*sc*i*
alias:          pci:v00001814d00003092sv*sd*bc*sc*i*
alias:          pci:v00001814d00003091sv*sd*bc*sc*i*
alias:          pci:v00001814d00003090sv*sd*bc*sc*i*
depends:        
vermagic:       3.2.0-41-generic-pae SMP mod_unload modversions 686 
parm:           mac:rt28xx: wireless mac addr (charp)

```

```
dmesg | egrep 'rt2|rt5'
[   15.537476] register rt2860
[   15.537502] rt2860 0000:04:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   15.537526] rt2860 0000:04:00.0: setting latency timer to 64

```

```
sudo iwlist scan
lo        Interface doesn't support scanning.

eth1      Interface doesn't support scanning.

ra0       Interface doesn't support scanning : Network is down

```

```
ifconfig -a
eth1      Link encap:Ethernet  HWaddr 38:60:77:d5:9b:27  
          inet addr:192.168.0.100  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::3a60:77ff:fed5:9b27/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2525 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2261 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2307334 (2.3 MB)  TX bytes:544372 (544.3 KB)
          Interrupt:20 Memory:fe700000-fe720000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:28 errors:0 dropped:0 overruns:0 frame:0
          TX packets:28 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2064 (2.0 KB)  TX bytes:2064 (2.0 KB)

ra0       Link encap:Ethernet  HWaddr 00:00:00:00:00:00  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 

```

```
 iwlist chan
lo        no frequency information.

eth1      no frequency information.

ra0       0 channels

```

```
dmesg | grep -e ra0 -e rt5 -e 04:00
[    0.532917] pci 0000:04:00.0: [1814:5392] type 0 class 0x000280
[    0.532937] pci 0000:04:00.0: reg 10: [mem 0xfe500000-0xfe50ffff]
[    0.628140] pci 0000:04:00.0: Signaling PME through PCIe PME interrupt
[   15.537502] rt2860 0000:04:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   15.537526] rt2860 0000:04:00.0: setting latency timer to 64

```

---

### Post by praseodym on 2013-05-13
```
ra0       Interface doesn't support scanning : Network is down
```
Any button, switch, key combination? Check
```

rfkill list
```
What model is that computer?

---

### Post by Vpc on 2013-05-13
> **praseodym said:**
> ```
ra0       Interface doesn't support scanning : Network is down
```
Any button, switch, key combination? Check
```

rfkill list
```
What model is that computer?

I'm not aware of "any button, switch, key combination" for scanning.
'rfkill list' returns no output.
As stated, it's custom built desktop computer. It has an Intel DP67DE motherboard with Intel Pentium G840 processor.

---

### Post by Vpc on 2013-05-14
```
lspci -nnk | grep -iA2 net
00:19.0 Ethernet controller [0200]: Intel Corporation 82579V Gigabit Network Connection [8086:1503] (rev 05)
	Subsystem: Intel Corporation Device [8086:2006]
	Kernel driver in use: e1000e
--
04:00.0 Network controller [0280]: Ralink corp. Device [1814:5392]
	Subsystem: D-Link System Inc Device [1186:3c06]
	Kernel driver in use: rt2860
```

Shouldn't the driver for Network controller be rt5390sta (which shows in the outputs above) instead of rt2860? How can I fix that?

I also added to the end of /etc/modprobe.d/blacklist.conf
```
# Blacklist conflicting kernel modules
blacklist rt2800pci
blacklist rt2800lib
blacklist rt2x00usb
blacklist rt2x00pci
blacklist rt2x00lib
blacklist rt2860sta
blacklist rt3090sta
```
and re-booted. But I still have the same problem.

---

### Post by praseodym on 2013-05-14
rt2860 is the "alias" of the driver, which is loaded. Try the additional installation of the config file:
```

wget media.cdn.ubuntu-de.org/forum/attachments/08/18/3473742-RT2860STA.dat.tar.gz
sudo mkdir -p /etc/Wireless/RT2860STA
sudo tar xvf 3473742-RT2860STA.dat.tar.gz -C /etc/Wireless/RT2860STA 
sudo modprobe -rfv rt5390sta
sudo modprobe -v rt5390sta
```

From here:

[http://forum.ubuntuusers.de/post/3473742/](http://forum.ubuntuusers.de/post/3473742/)

---

### Post by Vpc on 2013-05-14
> **praseodym said:**
> rt2860 is the "alias" of the driver, which is loaded. Try the additional installation of the config file:
```

wget media.cdn.ubuntu-de.org/forum/attachments/08/18/3473742-RT2860STA.dat.tar.gz
sudo mkdir -p /etc/Wireless/RT2860STA
sudo tar xvf 3473742-RT2860STA.dat.tar.gz -C /etc/Wireless/RT2860STA 
sudo modprobe -rfv rt5390sta
sudo modprobe -v rt5390sta
```

From here:

[http://forum.ubuntuusers.de/post/3473742/](http://forum.ubuntuusers.de/post/3473742/)

Tried the above and I still do not have wireless.

---

### Post by praseodym on 2013-05-14
Try to reset the BIOS. Please show:

```
sudo lshw -html > ~/System.html  
```

and upload the file System.html

---

