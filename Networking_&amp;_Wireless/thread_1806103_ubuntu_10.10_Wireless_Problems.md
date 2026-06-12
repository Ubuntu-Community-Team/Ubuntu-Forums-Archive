---
title: "ubuntu 10.10 Wireless Problems"
date: 2011-07-17
forum: Networking &amp; Wireless
---

### Post by Cooldude170 on 2011-07-17
Hello, I am running Ubuntu 10.10 on this laptop: [http://www.bestbuy.com/site/Toshiba+-+Satellite+Laptop+/+Intel&%23174%3B+Core&%23153%3B+i3+Processor+/+15.6%22+Display+-+Black/2833077.p?id=1218354609804&skuId=2833077&ref=25&loc=SHP&srccode=cii_45538312&cpncode=22-141737695-2]("http://www.bestbuy.com/site/Toshiba+-+Satellite+Laptop+/+Intel&%23174%3B+Core&%23153%3B+i3+Processor+/+15.6%22+Display+-+Black/2833077.p?id=1218354609804&skuId=2833077&ref=25&loc=SHP&srccode=cii_45538312&cpncode=22-141737695-2") and it does **not** scan for wireless networks. Any idea why?

---

### Post by wildmanne39 on 2011-07-17
> **Cooldude170 said:**
> Hello, I am running Ubuntu 10.10 on this laptop: [http://www.bestbuy.com/site/Toshiba+-+Satellite+Laptop+/+Intel&%23174%3B+Core&%23153%3B+i3+Processor+/+15.6%22+Display+-+Black/2833077.p?id=1218354609804&skuId=2833077&ref=25&loc=SHP&srccode=cii_45538312&cpncode=22-141737695-2]("http://www.bestbuy.com/site/Toshiba+-+Satellite+Laptop+/+Intel&%23174%3B+Core&%23153%3B+i3+Processor+/+15.6%22+Display+-+Black/2833077.p?id=1218354609804&skuId=2833077&ref=25&loc=SHP&srccode=cii_45538312&cpncode=22-141737695-2") and it does **not** scan for wireless networks. Any idea why?
Hi, you need to install the wireless card driver for it. Run these commands in a terminal 
```
sudo lshw -C network
``` 
```
lsmod
```
```
lspci -nn
```
```
rfkill list All
```
```
iwconfig
```
and post the outcome  here by clicking on new reply and click # and paste the information between the brackets.

---

### Post by Cooldude170 on 2011-07-17
sudo lshw -C network:
```

*-network               
       description: Ethernet interface
       product: AR8152 v2.0 Fast Ethernet
       vendor: Atheros Communications
       physical id: 0*-network               
       description: Ethernet interface
       product: AR8152 v2.0 Fast Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: c1
       serial: 00:26:6c:c3:1e:36
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.0.2-NAPI firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:45 memory:c0500000-c053ffff ioport:3000(size=128)
  *-network UNCLAIMED
       description: Network controller
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: ioport:2000(size=256) memory:c0400000-c0403fff

       bus info: pci@0000:01:00.0
       logical name: eth0
       version: c1
       serial: 00:26:6c:c3:1e:36
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.0.2-NAPI firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:45 memory:c0500000-c053ffff ioport:3000(size=128)
  *-network UNCLAIMED
       description: Network controller
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: ioport:2000(size=256) memory:c0400000-c0403fff

```
lsmod:
```

Module                  Size  Used by
binfmt_misc             7984  1 
parport_pc             30086  0 
ppdev                   6804  0 
joydev                 11363  0 
snd_hda_intel          26019  2 
snd_hda_codec         100919  1 snd_hda_intel
snd_hwdep               6660  1 snd_hda_codec
snd_pcm                89104  2 snd_hda_intel,snd_hda_codec
snd_seq_midi            5932  0 
snd_rawmidi            22207  1 snd_seq_midi
i915                  330089  2 
snd_seq_midi_event      7291  1 snd_seq_midi
snd_seq                57512  2 snd_seq_midi,snd_seq_midi_event
uvcvideo               62379  0 
videodev               49359  1 uvcvideo
snd_timer              23850  2 snd_pcm,snd_seq
drm_kms_helper         32836  1 i915
snd_seq_device          6912  3 snd_seq_midi,snd_rawmidi,snd_seq
v4l1_compat            15519  2 uvcvideo,videodev
v4l2_compat_ioctl32    12646  1 videodev
snd                    64117  12 snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm                   206161  3 i915,drm_kms_helper
psmouse                62080  0 
serio_raw               4910  0 
soundcore               1240  1 snd
snd_page_alloc          8588  2 snd_hda_intel,snd_pcm
intel_agp              32080  2 i915
i2c_algo_bit            6208  1 i915
video                  22176  1 i915
output                  2527  1 video
lp                     10201  0 
parport                37032  3 parport_pc,ppdev,lp
ahci                   21857  0 
libahci                26167  2 ahci
atl1c                  34955  0 

```

lspci -nn:
```

00:00.0 Host bridge [0600]: Intel Corporation Sandy Bridge DRAM Controller [8086:0104] (rev 09)
00:02.0 VGA compatible controller [0300]: Intel Corporation Sandy Bridge Integrated Graphics Controller [8086:0116] (rev 09)
00:16.0 Communication controller [0780]: Intel Corporation Cougar Point HECI Controller #1 [8086:1c3a] (rev 04)
00:1a.0 USB Controller [0c03]: Intel Corporation Cougar Point USB Enhanced Host Controller #2 [8086:1c2d] (rev 04)
00:1b.0 Audio device [0403]: Intel Corporation Cougar Point High Definition Audio Controller [8086:1c20] (rev 04)
00:1c.0 PCI bridge [0604]: Intel Corporation Cougar Point PCI Express Root Port 1 [8086:1c10] (rev b4)
00:1c.1 PCI bridge [0604]: Intel Corporation Cougar Point PCI Express Root Port 2 [8086:1c12] (rev b4)
00:1d.0 USB Controller [0c03]: Intel Corporation Cougar Point USB Enhanced Host Controller #1 [8086:1c26] (rev 04)
00:1f.0 ISA bridge [0601]: Intel Corporation Cougar Point LPC Controller [8086:1c49] (rev 04)
00:1f.2 SATA controller [0106]: Intel Corporation Cougar Point 6 port SATA AHCI Controller [8086:1c03] (rev 04)
00:1f.3 SMBus [0c05]: Intel Corporation Cougar Point SMBus Controller [8086:1c22] (rev 04)
01:00.0 Ethernet controller [0200]: Atheros Communications AR8152 v2.0 Fast Ethernet [1969:2062] (rev c1)
02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:8176] (rev 01)

```
rfkill list All:
```

Bogus list argument 'All'.

```
iwconfig:
```

lo        no wireless extensions.

eth0      no wireless extensions.

```

---

### Post by bkratz on 2011-07-17
You might want to look here, esp. the last three posts

[https://answers.launchpad.net/ubuntu/+source/gnome-nettool/+question/132667](https://answers.launchpad.net/ubuntu/+source/gnome-nettool/+question/132667)

---

### Post by wildmanne39 on 2011-07-17
Hi, that link should fix your problem, please let us know if you need more help and if your problem is resolved,would you please go to the top of the page and mark this thread solved be clicking on thread tools. Thank you so much.

---

### Post by Cooldude170 on 2011-07-17
Thank you, that worked perfectly!

---

### Post by bkratz on 2011-07-18
> **Cooldude170 said:**
> Thank you, that worked perfectly!



Glad to have helped, enjoy your wireless!

---

