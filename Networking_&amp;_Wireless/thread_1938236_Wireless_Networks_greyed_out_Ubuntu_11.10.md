---
title: "Wireless Networks greyed out Ubuntu 11.10"
date: 2012-03-09
forum: Networking &amp; Wireless
---

### Post by jscherer26 on 2012-03-09
I've read many suggestions online but haven't figured this out. The hardware is from ThinkPenguin Wireless N PCIe card for GNU/Linux and says it is compatible. 

cat /etc/lsb-release; uname -a
```

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"
Linux Southfork 3.0.0-16-generic-pae #29-Ubuntu SMP Tue Feb 14 13:56:31 UTC 2012 i686 i686 i386 GNU/Linux

```
lspci -nnk | grep -iA2 net
```
03:00.0 Network controller [0280]: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
	Subsystem: AzureWave Device [1a3b:1089]
	Kernel driver in use: ath9k
--
05:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 02)
	Subsystem: Giga-byte Technology GA-EP45-DS5 Motherboard [1458:e000]
	Kernel driver in use: r8169
--
06:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 02)
	Subsystem: Giga-byte Technology GA-EP45-DS5 Motherboard [1458:e000]
	Kernel driver in use: r8169

```
iwconfig
```
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=14 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

```
rfkill list all
```

0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

```
lsmod
```

Module                  Size  Used by
bnep                   17923  2 
rfcomm                 38408  0 
bluetooth             148839  10 bnep,rfcomm
pci_stub               12550  1 
vboxpci                22882  0 
vboxnetadp             13328  0 
vboxnetflt             27211  0 
vboxdrv               251814  3 vboxpci,vboxnetadp,vboxnetflt
vesafb                 13489  1 
binfmt_misc            17292  1 
arc4                   12473  2 
ath9k                 112612  0 
mac80211              393421  1 ath9k
ath9k_common           13599  1 ath9k
ath9k_hw              293933  2 ath9k,ath9k_common
ath                    19387  2 ath9k,ath9k_hw
snd_hda_codec_realtek   254163  1 
snd_hda_intel          28358  2 
snd_hda_codec          91859  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80435  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
cfg80211              172427  3 ath9k,mac80211,ath
nvidia              10941445  42 
ppdev                  12849  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
parport_pc             32114  1 
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    55902  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12600  1 snd
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
firewire_ohci          35846  0 
usbhid                 41905  0 
ums_realtek            13096  0 
firewire_core          56937  1 firewire_ohci
usb_storage            44173  1 ums_realtek
hid                    77367  1 usbhid
uas                    17699  0 
crc_itu_t              12627  1 firewire_core
floppy                 60310  0 
ahci                   21634  2 
libahci                25761  1 ahci
pata_jmicron           12651  0 
r8169                  47200  0 
dm_raid45              76451  0 
xor                    21860  1 dm_raid45
dm_mirror              21822  1 
dm_region_hash         16065  1 dm_mirror
dm_log                 18193  4 dm_raid45,dm_mirror,dm_region_hash

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
#iface eth0 inet dhcp

```
sudo iwlist scan
```

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Interface doesn't support scanning.

wlan0     No scan results

```
ifconfig
```

eth0      Link encap:Ethernet  HWaddr 6c:f0:49:01:8b:6f  
          inet addr:192.168.11.201  Bcast:192.168.11.255  Mask:255.255.255.0
          inet6 addr: fe80::6ef0:49ff:fe01:8b6f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8659 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8912 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6128084 (6.1 MB)  TX bytes:1593418 (1.5 MB)
          Interrupt:46 Base address:0xe000 

eth1      Link encap:Ethernet  HWaddr 00:24:1d:80:06:88  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:47 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:110 errors:0 dropped:0 overruns:0 frame:0
          TX packets:110 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:12644 (12.6 KB)  TX bytes:12644 (12.6 KB)

wlan0     Link encap:Ethernet  HWaddr 74:f0:6d:92:e5:b3  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```
dmesg | grep -i 'wlan0'
```

[   25.953495] ADDRCONF(NETDEV_UP): wlan0: link is not ready

```

---

