---
title: "Wifi Card not Working TP-LINK TL-WN951N &quot;UNCLAIMED&quot; ath9k"
date: 2012-09-19
forum: Networking &amp; Wireless
---

### Post by crazycheetah on 2012-09-19
Hello,

I've been running my system for a while using ethernet, but just recently moved to a location that I am unable to access the ethernet at all. I did have another wifi card but was consistently having issues with it (just very spotty--kept disconnecting every 30min or so), and got my hands on a TP-LINK TL-WN951N card to try out instead. However, I'm not able to get this going at all and was hoping I could possibly find some help on here.

Of note, this is in a desktop, and I'm reaching this forum through a laptop that has a good, solid, working connection, so my copy/paste is being done through a USB thumb drive.

According to here [https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsTP-Link]("https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsTP-Link") I need to use the ath9k driver for this card. I added "ath9k" to the /etc/modules file and have tried using modprobe to unload and load the ath9k driver several times as I ran some searches looking for answers, but it doesn't seem to make any differences.

Here's several commands to try and give you a good idea of everything that I've got going so far:

```
derek@BlackBoxen:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04 LTS"
Linux BlackBoxen 3.2.0-24-generic #37-Ubuntu SMP Wed Apr 25 08:43:22 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
```

```
derek@BlackBoxen:~$ lspci -nnk | grep -iA2 net
01:08.0 Network controller [0280]: Atheros Communications Inc. Device [168c:0003] (rev 01)
        Subsystem: Atheros Communications Inc. Device [168c:3051]
02:00.0 VGA compatible controller [0300]: NVIDIA Corporation G86 [GeForce 8400 GS] [10de:0422] (rev a1)
--
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 01)
        Subsystem: Biostar Microtech Int'l Corp Device [1565:2305]
        Kernel driver in use: r8169
```

```
derek@BlackBoxen:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

```

```
derek@BlackBoxen:~$ rfkill list all
derek@BlackBoxen:~$ 
```

```
derek@BlackBoxen:~$ lsmod
Module                  Size  Used by
ath9k                 132390  0 
mac80211              506816  1 ath9k
ath9k_common           14053  1 ath9k
ath9k_hw              411112  2 ath9k,ath9k_common
ath                    24067  3 ath9k,ath9k_common,ath9k_hw
cfg80211              205544  3 ath9k,mac80211,ath
snd_hrtimer            12744  1 
dm_crypt               23125  0 
pci_stub               12622  1 
vboxpci                23200  0 
vboxnetadp             13382  0 
vboxnetflt             23441  0 
vboxdrv               287082  3 vboxpci,vboxnetadp,vboxnetflt
snd_hda_codec_hdmi     32474  1 
rfcomm                 47604  0 
bnep                   18281  2 
bluetooth             180104  10 rfcomm,bnep
binfmt_misc            17540  1 
snd_hda_codec_realtek   223867  1 
ppdev                  17113  0 
nvidia              12319264  42 
snd_hda_intel          33773  3 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
psmouse                87692  0 
snd_pcm                97188  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
serio_raw              13211  0 
edac_core              53746  0 
k8temp                 13057  0 
edac_mce_amd           23709  0 
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
parport_pc             32866  1 
snd_seq_midi_event     14899  1 snd_seq_midi
wmi                    19256  0 
snd_seq                61896  3 snd_seq_midi,snd_seq_midi_event
snd_timer              29990  3 snd_hrtimer,snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    78855  17 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
mac_hid                13253  0 
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
i2c_nforce2            13058  0 
lp                     17799  0 
parport                46562  3 ppdev,parport_pc,lp
vesafb                 13844  1 
usbhid                 47199  0 
hid                    99559  1 usbhid
r8169                  62099  0 
pata_amd               14118  1 
floppy                 70365  0 
```

```
derek@BlackBoxen:~$ lsmod | grep ath
ath9k                 132390  0 
mac80211              506816  1 ath9k
ath9k_common           14053  1 ath9k
ath9k_hw              411112  2 ath9k,ath9k_common
ath                    24067  3 ath9k,ath9k_common,ath9k_hw
cfg80211              205544  3 ath9k,mac80211,ath
```

```
derek@BlackBoxen:~$ sudo lshw -C network
[sudo] password for derek: 
  *-network UNCLAIMED     
       description: Network controller
       product: Atheros Communications Inc.
       vendor: Atheros Communications Inc.
       physical id: 8
       bus info: pci@0000:01:08.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0
       resources: memory:fde00000-fde0ffff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 01
       serial: 00:e0:4d:3a:1f:d1
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=N/A latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:47 ioport:ac00(size=256) memory:fddff000-fddfffff memory:fdc00000-fdc1ffff
```

```
derek@BlackBoxen:~$ cat /etc/modprobe.d/ath9k.conf
options ath9k nohwcrypt=1
```

```
derek@BlackBoxen:~$ nm-tool

NetworkManager Tool

State: disconnected

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        00:E0:4D:3A:1F:D1

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off
```

```
derek@BlackBoxen:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

```


I appreciate any help or even just any further ideas of where to start looking for a good solution to this.

---

