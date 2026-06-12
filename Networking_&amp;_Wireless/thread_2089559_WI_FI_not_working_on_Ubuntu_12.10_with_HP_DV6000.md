---
title: "WI FI not working on Ubuntu 12.10 with HP DV6000"
date: 2012-11-29
forum: Networking &amp; Wireless
---

### Post by robyer8 on 2012-11-29
Hi, i just recently got ubuntu 12.10,everything works perfect except for the wireless internet that does not work. The orange light of wifi button keeps orange in on and off mode.
The wired connections work, i have been trying to fix it but i can't. I made alot of experiment reading all post , but nothing seams to work.
I have an hp dv6000 laptop and im running sta broadcom driver. 
Please Help me
Thanks

Some Info:
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.10
DISTRIB_CODENAME=quantal
DISTRIB_DESCRIPTION="Ubuntu 12.10"
Linux ubuntu 3.5.0-17-generic #28-Ubuntu SMP Tue Oct 9 19:32:08 UTC 2012 i686 i686 i686 GNU/Linux

**ubuntu@ubuntu:~$ sudo lshw -C network**
  *-network               
       description: Network controller
       product: BCM4312 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:16 memory:f4000000-f4003fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth1
       version: 01
       serial: 00:1e:68:5a:87:62
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half ip=192.168.1.104 latency=0 link=yes multicast=yes port=MII speed=10Mbit/s
       resources: irq:45 ioport:c000(size=256) memory:f8000000-f8000fff memory:c0000000-c001ffff
[B]
ubuntu@ubuntu:~$ sudo lshw -C network[/B]
  *-network               
       description: Network controller
       product: BCM4312 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:16 memory:f4000000-f4003fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth1
       version: 01
       serial: 00:1e:68:5a:87:62
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half ip=192.168.1.104 latency=0 link=yes multicast=yes port=MII speed=10Mbit/s
       resources: irq:45 ioport:c000(size=256) memory:f8000000-f8000fff memory:c0000000-c001ffff
ubuntu@ubuntu:~$ ^C
ubuntu@ubuntu:~$ ^C
ubuntu@ubuntu:~$ lspci -nn | grep -e 0280 -e 0200
02:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
06:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 01)

**ubuntu@ubuntu:~$ iwconfig**
lo        no wireless extensions.

eth1      no wireless extensions.

**ubuntu@ubuntu:~$ rfkill list all**
0: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
1: hp-bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: yes

**ubuntu@ubuntu:~$ lsmod**
Module                  Size  Used by
dm_crypt               22402  0 
joydev                 17161  0 
snd_hda_codec_si3054    12864  1 
snd_hda_codec_realtek    63356  1 
snd_hda_intel          32515  3 
snd_hda_codec         111547  3 snd_hda_codec_si3054,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13272  1 snd_hda_codec
snd_pcm                80163  3 snd_hda_codec_si3054,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
coretemp               13168  0 
snd_rawmidi            25382  1 snd_seq_midi
b43                   347284  0 
uvcvideo               71277  0 
r852                   17905  0 
videobuf2_core         32070  1 uvcvideo
snd_seq_midi_event     14475  1 snd_seq_midi
sm_common              16737  1 r852
videodev               95841  2 uvcvideo,videobuf2_core
nand                   49496  2 r852,sm_common
snd_seq                51255  2 snd_seq_midi,snd_seq_midi_event
videobuf2_vmalloc      12756  1 uvcvideo
videobuf2_memops       13184  1 videobuf2_vmalloc
mac80211              461161  1 b43
kvm                   357806  0 
nand_ids                8547  1 nand
snd_timer              24411  2 snd_pcm,snd_seq
hp_wmi                 13616  0 
mtd                    38602  2 sm_common,nand
snd_seq_device         14137  3 snd_seq_midi,snd_rawmidi,snd_seq
nand_bch               13003  1 nand
bch                    17199  1 nand_bch
r592                   17707  0 
dm_multipath           22365  0 
sparse_keymap          13658  1 hp_wmi
nand_ecc               13070  1 nand
scsi_dh                14178  1 dm_multipath
psmouse                84843  0 
cfg80211              175375  2 b43,mac80211
memstick               15842  1 r592
serio_raw              13031  0 
microcode              18209  0 
snd                    61991  16 snd_hda_codec_si3054,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
mac_hid                13037  0 
bcma                   34483  1 b43
lpc_ich                16925  0 
soundcore              14599  1 snd
bnep                   17707  2 
snd_page_alloc         14036  2 snd_hda_intel,snd_pcm
parport_pc             31968  0 
rfcomm                 37276  0 
ppdev                  12817  0 
bluetooth             183228  10 bnep,rfcomm
lp                     13299  0 
parport                40753  3 parport_pc,ppdev,lp
ext2                   67204  1 
squashfs               35834  1 
overlayfs              27233  1 
nls_iso8859_1          12617  1 
dm_raid45              75357  0 
xor                    26090  1 dm_raid45
dm_mirror              21665  0 
dm_region_hash         15977  1 dm_mirror
dm_log                 18137  3 dm_raid45,dm_mirror,dm_region_hash
hid_generic            12445  0 
usbhid                 41702  0 
hid                    82142  2 hid_generic,usbhid
firewire_ohci          35521  0 
nouveau               823577  4 
firewire_core          57492  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
sdhci_pci              18155  0 
sdhci                  27830  1 sdhci_pci
ttm                    75534  1 nouveau
drm_kms_helper         45271  1 nouveau
drm                   230463  6 nouveau,ttm,drm_kms_helper
i2c_algo_bit           13197  1 nouveau
mxm_wmi                12859  1 nouveau
r8169                  55976  0 
ssb                    50087  1 b43
video                  18847  1 nouveau
wmi                    18590  3 hp_wmi,nouveau,mxm_wmi
usb_storage            39350  1 

**ubuntu@ubuntu:~$ sudo iwlist scan**
lo        Interface doesn't support scanning.

eth1      Interface doesn't support scanning.

THANKYOU FOR HELP

---

### Post by robyer8 on 2012-11-30
Please Help me :(

---

### Post by Abhinav Kumar on 2012-11-30
> **robyer8 said:**
> Hi, i just recently got ubuntu 12.10,everything works perfect except for the wireless internet that does not work. The orange light of wifi button keeps orange in on and off mode.
Hi robyer8,
To do this, run the following code in terminal
```

sudo rfkill unblock all
sudo rfkill list all

```Regards,
Abhinav

---

