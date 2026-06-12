---
title: "OSD notifications reversed"
date: 2011-12-02
forum: Networking &amp; Wireless
---

### Post by Rebelli0us on 2011-12-02
Normally when the machine resumes from S3 there’s an OSD message, “wired network connected”. Now it’s reversed, the machine resumes from S3, the networks connect normally BUT the OSD notification says, “wired network disconnected -- you are now offline”. &#373;TF.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=208387&stc=1&d=1322846673[/IMG]

Is there a fix for this?

---

### Post by praseodym on 2011-12-02
Hi,

what hardware is that? Pleade show:

```
sudo apt-get install ethtool
lspci -nnk | grep -iA2 net
lsmod
sudo ethtool eth0
ifconfig eth0
```

---

### Post by Rebelli0us on 2011-12-02
ok

```
 lspci -nnk | grep -iA2 net
02:00.0 Network controller [0280]: Atheros Communications Inc. AR5008 Wireless Network Adapter [168c:0024] (rev 01)
	Subsystem: D-Link System Inc Device [1186:3a70]
	Kernel driver in use: ath9k
--
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 03)
	Subsystem: Giga-byte Technology GA-EP45-DS5 Motherboard [1458:e000]
	Kernel driver in use: r8169

```

```
lsmod
Module                  Size  Used by
nls_utf8                1453  0 
isofs                  34218  0 
cryptd                  8140  0 
aes_x86_64              7936  1 
aes_generic            27631  1 aes_x86_64
joydev                 11395  0 
rfcomm                 40819  4 
binfmt_misc             7984  1 
sco                     9986  2 
bnep                   11985  2 
l2cap                  42336  20 rfcomm,bnep
pci_stub                1622  1 
vboxpci                15608  0 
vboxnetadp              5838  0 
vboxnetflt             16638  1 
vboxdrv              1854941  4 vboxpci,vboxnetadp,vboxnetflt
parport_pc             30086  0 
ppdev                   6804  0 
snd_hda_codec_atihdmi     3079  1 
snd_hda_codec_realtek   300109  1 
arc4                    1497  2 
snd_hda_intel          26147  4 
snd_hda_codec         100919  3 snd_hda_codec_atihdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               6660  1 snd_hda_codec
snd_pcm                89104  3 snd_hda_intel,snd_hda_codec
snd_seq_midi            5932  0 
snd_rawmidi            22207  1 snd_seq_midi
snd_seq_midi_event      7291  1 snd_seq_midi
snd_seq                57512  2 snd_seq_midi,snd_seq_midi_event
radeon                910771  2 
btusb                  12961  4 
bluetooth              59245  9 rfcomm,sco,bnep,l2cap,btusb
ath9k                 101858  0 
snd_timer              23850  2 snd_pcm,snd_seq
snd_seq_device          6912  3 snd_seq_midi,snd_rawmidi,snd_seq
ttm                    68212  1 radeon
drm_kms_helper         32836  1 radeon
ath9k_common            6874  1 ath9k
it87                   35308  0 
snd                    64277  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ath9k_hw              314654  2 ath9k,ath9k_common
hwmon_vid               3154  1 it87
ath                    10413  2 ath9k,ath9k_hw
mac80211              267099  2 ath9k,ath9k_common
drm                   206198  4 radeon,ttm,drm_kms_helper
i2c_algo_bit            6208  1 radeon
serio_raw               4910  0 
i2c_piix4              10047  0 
soundcore               1240  1 snd
snd_page_alloc          8588  2 snd_hda_intel,snd_pcm
k10temp                 3535  0 
cfg80211              170581  4 ath9k,ath9k_common,ath,mac80211
led_class               3393  1 ath9k
edac_core              46822  0 
shpchp                 34910  0 
edac_mce_amd            9387  0 
lp                     10201  0 
parport                37032  3 parport_pc,ppdev,lp
usbhid                 42030  0 
hid                    84710  1 usbhid
pata_jmicron            2771  0 
r8169                  42286  0 
firewire_ohci          24839  0 
firewire_core          54327  1 firewire_ohci
crc_itu_t               1739  1 firewire_core
mii                     5261  1 r8169
ahci                   22370  6 
libahci                26148  1 ahci

```

```
sudo ethtool eth0
Settings for eth0:
	Supported ports: [ TP MII ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Half 1000baseT/Full 
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Half 1000baseT/Full 
	Advertised pause frame use: No
	Advertised auto-negotiation: Yes
	Link partner advertised link modes:  10baseT/Half 10baseT/Full 
	                                     100baseT/Half 100baseT/Full 
	Link partner advertised pause frame use: No
	Link partner advertised auto-negotiation: Yes
	Speed: 100Mb/s
	Duplex: Full
	Port: MII
	PHYAD: 0
	Transceiver: internal
	Auto-negotiation: on
	Supports Wake-on: pumbg
	Wake-on: g
	Current message level: 0x00000033 (51)
	Link detected: yes

```


```
 ifconfig eth0
eth0      Link encap:Ethernet  HWaddr 6c:f0:49:e8:53:d6  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::6ef0:49ff:fee8:53d6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2490358 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1858659 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3286818861 (3.2 GB)  TX bytes:786050918 (786.0 MB)
          Interrupt:44 Base address:0x4000 

```

---

### Post by praseodym on 2011-12-02
You can unload the driver(s) during SUSPEND/HIBERNATE and load them during "wake-up":

```
gksu gedit /etc/pm/config.d/00sleep_module
```
Insert:
```
SUSPEND_MODULES="$SUSPEND_MODULES r8169 ath9k" 
```
save, and close **gedit**. Set the executable flag:
```
sudo chmod +x /etc/pm/config.d/00sleep_module
```
Which Ubuntu-version is that? From 11.04 you can (should) replace the driver r816[COLOR="Red"]9[/COLOR] with the "right" one r816[COLOR="Red"]8[/COLOR]. See [here]("http://ubuntuforums.org/showpost.php?p=11504239&postcount=11"). Replace the driver in that file, too, if any problems occur again.

Alternatively/additionally you can deactivate the auto-negotiation:

```
sudo ethtool -s eth0 speed 100 autoneg off
```

---

