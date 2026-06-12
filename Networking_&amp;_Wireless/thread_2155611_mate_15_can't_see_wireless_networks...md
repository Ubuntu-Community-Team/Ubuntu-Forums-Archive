---
title: "mate 15 can't see wireless networks.."
date: 2013-06-18
forum: Networking &amp; Wireless
---

### Post by Bryant777 on 2013-06-18
I've installed Mate 15 on HP Pavilion dv5000.  No locks are on.  I installed b43 and can't get it to work.

Help please.

---

### Post by Bryant777 on 2013-06-18
typing 

lspci -n | grep 0280 rfkill list lsmod
in terminal

---

### Post by Bryant777 on 2013-06-18
house@house-Pavilion-dv5000-EP411UA-ABA ~ $ lspci -n | grep 0280
06:02.0 0280: 14e4:4318 (rev 02)
house@house-Pavilion-dv5000-EP411UA-ABA ~ $ rfkill list
0: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
house@house-Pavilion-dv5000-EP411UA-ABA ~ $ lsmod
Module                  Size  Used by
parport_pc             27504  0 
ppdev                  12817  0 
rfcomm                 37420  0 
bnep                   17669  2 
bluetooth             202069  10 bnep,rfcomm
hp_wmi                 17712  0 
joydev                 17097  0 
sparse_keymap          13658  1 hp_wmi
snd_atiixp             19309  2 
snd_atiixp_modem       18585  0 
b43                   351918  0 
snd_ac97_codec        105692  2 snd_atiixp_modem,snd_atiixp
ac97_bus               12670  1 snd_ac97_codec
snd_pcm                80890  3 snd_ac97_codec,snd_atiixp_modem,snd_atiixp
bcma                   39645  1 b43
snd_page_alloc         14230  3 snd_pcm,snd_atiixp_modem,snd_atiixp
snd_seq_midi           13132  0 
mac80211              526519  1 b43
snd_seq_midi_event     14475  1 snd_seq_midi
snd_rawmidi            25114  1 snd_seq_midi
snd_seq                51280  2 snd_seq_midi_event,snd_seq_midi
cfg80211              436177  2 b43,mac80211
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
dm_multipath           22402  0 
mac_hid                13037  0 
snd_timer              24411  2 snd_pcm,snd_seq
scsi_dh                14427  1 dm_multipath
k8temp                 12842  0 
psmouse                81038  0 
snd                    56485  12 snd_ac97_codec,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_seq_device,snd_atiixp_modem,snd_atiixp
shpchp                 32129  0 
serio_raw              13031  0 
i2c_piix4              13066  0 
soundcore              12600  1 snd
lp                     13299  0 
parport                40753  3 lp,ppdev,parport_pc
btrfs                 774622  0 
zlib_deflate           26445  1 btrfs
libcrc32c              12543  1 btrfs
dm_raid45              75357  0 
xor                    26062  1 dm_raid45
dm_mirror              21621  0 
dm_region_hash         16012  1 dm_mirror
dm_log                 18137  3 dm_region_hash,dm_mirror,dm_raid45
pata_acpi              12886  0 
radeon                870822  2 
i2c_algo_bit           13197  1 radeon
ttm                    71289  1 radeon
ssb                    50628  1 b43
drm_kms_helper         47545  1 radeon
8139too                23071  0 
8139cp                 26557  0 
wmi                    18590  1 hp_wmi
pata_atiixp            13058  2 
drm                   228750  4 ttm,drm_kms_helper,radeon
video                  18894  0 
ati_agp                13177  0 
house@house-Pavilion-dv5000-EP411UA-ABA ~ $

---

### Post by Bryant777 on 2013-06-18
Also did this:

house@house-Pavilion-dv5000-EP411UA-ABA ~ $ sudo lshw -C network
[sudo] password for house: 
Sorry, try again.
[sudo] password for house: 
  *-network:0             
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:06:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64
       resources: irq:9 memory:c0200000-c0201fff
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 6
       bus info: pci@0000:06:06.0
       logical name: eth0
       version: 10
       serial: 00:0f:b0:bf:3c:1a
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.103 latency=128 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100Mbit/s
       resources: irq:22 ioport:a000(size=256) memory:c0202000-c02020ff
house@house-Pavilion-dv5000-EP411UA-ABA ~ $

---

### Post by Bryant777 on 2013-06-18
I give up.  Can't get the wifi card to show up.

---

### Post by Hadaka on 2013-06-18
Hi, from a wired connection.
  in terminal...please do..
```
sudo apt-get update
sudo apt-get upgrade
```
boot...then disconnect your ethernet cable 
and do..
```
sudo modprobe -rf b43
sudo modprobe -v b43
dmesg | tail -n 20
```
post the results 
thanks

---

