---
title: "Wifi stopped working suddenly - unable to pass authentication"
date: 2012-07-18
forum: Networking &amp; Wireless
---

### Post by austinap on 2012-07-18
Hello, 

I'm running Ubuntu 12.04, and last night my wireless started to tweak out and disconnected a few times.  By the end of the night was unable to connect at all.  It gets stuck at authentication, and keeps asking for a username/password every 2 minutes or so until I cancel.  I spoke to IT here, and they told me they haven't rolled out any changes on their end for several weeks.  I'm able to connect with the same info on Windows and OS X, and haven't updated my system in the last week or so (except for install QTikz yesterday).   

My system info:
lspci:
```

00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b5)
00:1c.1 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 (rev b5)
00:1c.4 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 5 (rev b5)
00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation H61 Express Chipset Family LPC Controller (rev 05)
00:1f.2 IDE interface: Intel Corporation 6 Series/C200 Series Chipset Family 4 port SATA IDE Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 05)
00:1f.5 IDE interface: Intel Corporation 6 Series/C200 Series Chipset Family 2 port SATA IDE Controller (rev 05)
01:00.0 VGA compatible controller: NVIDIA Corporation GF108 [GeForce GT 420] (rev a1)
01:00.1 Audio device: NVIDIA Corporation GF108 High Definition Audio Controller (rev a1)
03:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)

```
iwconfig:
```

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"athens"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:24:6C:AB:8F:A0   
          Bit Rate=52 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=52/70  Signal level=-58 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:16   Missed beacon:0

eth0      no wireless extensions.

```
lsmod:
```

Module                  Size  Used by
isofs                  40257  1 
nls_utf8               12557  2 
udf                    94317  1 
crc_itu_t              12707  1 udf
nfnetlink_queue        17882  1 
nfnetlink              14327  2 nfnetlink_queue
nf_conntrack_ipv4      19716  3 
nf_defrag_ipv4         12729  1 nf_conntrack_ipv4
ipt_REJECT             12576  1 
xt_tcpudp              12603  4 
iptable_filter         12810  1 
ip_tables              27473  1 iptable_filter
xt_iprange             12541  0 
xt_state               12578  3 
nf_conntrack           81926  2 nf_conntrack_ipv4,xt_state
xt_mark                12563  6 
xt_NFQUEUE             12726  3 
x_tables               29846  8 ipt_REJECT,xt_tcpudp,iptable_filter,ip_tables,xt_iprange,xt_state,xt_mark,xt_NFQUEUE
rfcomm                 47604  0 
parport_pc             32866  0 
ppdev                  17113  0 
bnep                   18281  2 
bluetooth             180104  10 rfcomm,bnep
binfmt_misc            17540  1 
nls_iso8859_1          12713  2 
nls_cp437              16991  2 
vfat                   17585  2 
fat                    61512  1 vfat
vesafb                 13844  1 
snd_hda_codec_hdmi     32474  4 
snd_hda_codec_conexant    62311  1 
psmouse                87692  0 
dcdbas                 14490  0 
arc4                   12529  2 
nvidia              12319264  42 
snd_hda_intel          33773  5 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                97188  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
serio_raw              13211  0 
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
ath9k                 132390  0 
mac80211              506816  1 ath9k
ath9k_common           14053  1 ath9k
ath9k_hw              411112  2 ath9k,ath9k_common
ath                    24067  3 ath9k,ath9k_common,ath9k_hw
cfg80211              205544  3 ath9k,mac80211,ath
snd                    78855  20 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
mac_hid                13253  0 
mei                    41616  0 
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
usbhid                 47199  0 
hid                    99559  1 usbhid
r8169                  62099  0 
usb_storage            49198  3 

```sudo lshw -C network
```

  *-network               
       description: Wireless interface
       product: AR9285 Wireless Network Adapter (PCI-Express)
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 01
       serial: c0:f8:da:5f:14:89
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath9k driverversion=3.2.0-26-generic firmware=N/A latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:17 memory:fb100000-fb10ffff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 06
       serial: f0:4d:a2:f4:c9:7d
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8168e-3_0.0.4 03/27/12 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:44 ioport:d000(size=256) memory:da104000-da104fff memory:da100000-da103fff

```iwlist scan:
```

lo        Interface doesn't support scanning.

wlan0     No scan results

eth0      Interface doesn't support scanning.

```Any ideas?  Thanks!

---

### Post by austinap on 2012-07-18
Bump. 

Any help?  This is really frustrating, and I have no idea what would have changed to make this happen so suddenly.

---

### Post by steeldriver on 2012-07-18
Well I'm not really up on the wireless stuff but I don't think it will do any harm to try

```
sudo modprobe -r ath9k
sudo modprobe ath9k nohwcrypt=1
```

Post back if it helps and we can make it persistent

---

### Post by austinap on 2012-07-18
> **steeldriver said:**
> Well I'm not really up on the wireless stuff but I don't think it will do any harm to try

```
sudo modprobe -r ath9k
sudo modprobe ath9k nohwcrypt=1
```Post back if it helps and we can make it persistent


Didn't seem to make any difference, thanks for the idea though.

---

### Post by steeldriver on 2012-07-19
been doing some more searching - does this sound familiar?

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/945379](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/945379)

no resolution yet unfortunately...

---

### Post by austinap on 2012-07-19
> **steeldriver said:**
> been doing some more searching - does this sound familiar?

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/945379](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/945379)

no resolution yet unfortunately...


Yes, that sounds familiar and my setup has previously been known to drop the connection, but in the past it has always been able to connect again within a few minutes.  At this point, it's been two days since I've been able to connect to the network.

Anything I could try to see if I can reconnect again?  I've rebooted multiple times, cycled ifconfig wlan0 down/up a few times, and restarted the network manager a few times, all to no avail.

---

### Post by austinap on 2012-07-20
Any ideas at all?  Would a new, non-atheros wifi card likely fix things?  If so, can anyone give me a recommendation on cards that have worked well with ubuntu?

---

