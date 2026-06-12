---
title: "RLT819xSE &amp;  interfaces messed up!"
date: 2012-03-31
forum: Networking &amp; Wireless
---

### Post by eoliveira14 on 2012-03-31
I'm lost! Wireless stopped working out of nothing; i've read several topics about this RLT8191(driver 8192SE) but cant fix this issue. Would somebody please help? I'm posting every results I got from every codes i've read in these other topics, hahaha (Kinda newbie, so I don't know what i'd have to post :X)

```
[B] sudo lshw -C network

[/B]*-network UNCLAIMED     
       description: Network controller
       product: RTL8191SEvA Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:10:00.0
       version: 10
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list
       configuration: latency=0
       resources: ioport:6000(size=256) memory:e8000000-e8003fff
  *-network
       description: Ethernet interface
       product: 88E8042 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:30:00.0
       logical name: eth0
       version: 10
       serial: 78:e7:d1:b0:ed:fb
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.28 duplex=full firmware=N/A ip=189.61.88.162 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:44 memory:e0000000-e0003fff ioport:2000(size=256)

``````
**dmesg |grep 819**
[    0.008193] Initializing cgroup subsys devices
[    0.008195] Initializing cgroup subsys freezer
[    0.008197] Initializing cgroup subsys net_cls
[    0.158191] Time: 21:00:05  Date: 03/31/12
[    0.287819] ACPI: SSDT 7f7dba90 0027F (v01 HP      Cpu0Ist 00003000 INTL 20060317)
[    0.909434] agpgart-intel 0000:00:00.0: detected 8192K stolen memory
[   11.523784] rtl8192se 0000:10:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   11.524201] rtl8192se 0000:10:00.0: setting latency timer to 64
[   11.581716] rtl8192se: Driver for Realtek RTL8192SE/RTL8191SE
[   11.581719]            Loading firmware rtlwifi/rtl8192sefw.bin
[   12.103248] rtl8192se:rtl92s_init_sw_vars():<0-0> Failed to request firmware!
[   12.103414] rtl8192se 0000:10:00.0: PCI INT A disabled

``````
**lsmod | grep 819**

rtl8192se              94139  0 
rtlwifi                95614  1 rtl8192se
mac80211              393421  2 rtl8192se,rtlwifi

``````
**sudo modprobe r8192se_pci**
FATAL: Module r8192se_pci not found.

``````
**iwconfig**
lo        no wireless extensions.

eth0      no wireless extensions.

```I don't know what to do... =\

---

### Post by wildmanne39 on 2012-03-31
Hi, welcome to the forum! Please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:

```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
lsusb
iwconfig
rfkill list all
lsmod
```
Thanks

---

### Post by eoliveira14 on 2012-03-31
Okey dokey...

```
**cat /etc/lsb-release; uname -a**
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"
Linux emo1402 3.0.0-17-generic #30-Ubuntu SMP Thu Mar 8 17:34:21 UTC 2012 i686 i686 i386 GNU/Linux
```

```
**lspci -nnk | grep -iA2 net**
10:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8191SEvA Wireless LAN Controller [10ec:8171] (rev 10)
    Subsystem: Hewlett-Packard Company Device [103c:1467]
    Kernel modules: rtl8192se
30:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8042 PCI-E Fast Ethernet Controller [11ab:4357] (rev 10)
    Subsystem: Hewlett-Packard Company Device [103c:308a]
    Kernel driver in use: sky2

```

```
**lsusb**
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 04f2:b159 Chicony Electronics Co., Ltd 
```

```
**iwconfig**
lo        no wireless extensions.

eth0      no wireless extensions.

```

```
** rfkill list all**
0: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```

```
**lsmod**
Module                  Size  Used by
rfcomm                 38408  0 
bnep                   17923  2 
bluetooth             148839  10 rfcomm,bnep
parport_pc             32114  0 
ppdev                  12849  0 
snd_hda_codec_idt      60049  1 
joydev                 17393  0 
hp_wmi                 13652  0 
sparse_keymap          13658  1 hp_wmi
binfmt_misc            17292  1 
uvcvideo               67271  0 
psmouse                73673  0 
videodev               85626  1 uvcvideo
serio_raw              12990  0 
snd_hda_intel          24262  4 
snd_hda_codec          91859  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80435  3 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
rtl8192se              94139  0 
rtlwifi                95614  1 rtl8192se
snd_timer              28932  2 snd_pcm,snd_seq
mac80211              393421  2 rtl8192se,rtlwifi
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
wmi                    18744  1 hp_wmi
i915                  509519  3 
cfg80211              172427  2 rtlwifi,mac80211
snd                    55902  16 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm_kms_helper         32889  1 i915
drm                   192194  4 i915,drm_kms_helper
i2c_algo_bit           13199  1 i915
video                  18908  1 i915
soundcore              12600  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
usbhid                 41905  0 
hid                    77367  1 usbhid
ahci                   21634  2 
libahci                25727  1 ahci
sky2                   49317  0 

```

---

### Post by wildmanne39 on 2012-03-31
Hi, install this firmware please then reboot. After you download it just double click on the deb file in your download and it should install. 
[http://de.archive.ubuntu.com/ubuntu/pool/main/l/linux-firmware/linux-firmware_1.52_all.deb](http://de.archive.ubuntu.com/ubuntu/pool/main/l/linux-firmware/linux-firmware_1.52_all.deb)
Thanks

---

### Post by eoliveira14 on 2012-03-31
In the software center it is already marked and also: A later version is already installed

---

### Post by wildmanne39 on 2012-03-31
Hi, I suspect that firmware is bad that is what broke your wireless I think. 

So remove the firmware and reinstall it see if that helps if not remove it and install the one I gave you and we will see if that helps.
Thanks

---

### Post by eoliveira14 on 2012-03-31
> **wildmanne39 said:**
> Hi, I suspect that firmware is bad that is what broke your wireless I think. 

So remove the firmware and reinstall it see if that helps if not remove it and install the one I gave you and we will see if that helps.
Thanks

Silly question : how can I remove it? :-k hehe

---

### Post by eoliveira14 on 2012-03-31
Nevermind :P I found out... I thought I'd have to specify the current version, wich I didn't know...
I'll reply as soon as i reboot

---

### Post by eoliveira14 on 2012-03-31
Wildmanne39, thank you VERY much! The later version worked when reinstalled. :))

---

### Post by wildmanne39 on 2012-03-31
Hi, your welcome! I had to leave a few minutes sorry for that.
Thanks

---

