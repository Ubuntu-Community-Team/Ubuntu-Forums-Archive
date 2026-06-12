---
title: "Wireless -network UNCLAIMED"
date: 2011-09-06
forum: Networking &amp; Wireless
---

### Post by xkang on 2011-09-06
My wireless wont work. So i followed this guide:

[https://help.ubuntu.com/10.04/internet/C/troubleshooting-wireless.html#troubleshooting-wireless-ndiswrapper](https://help.ubuntu.com/10.04/internet/C/troubleshooting-wireless.html#troubleshooting-wireless-ndiswrapper)

I installed the .inf according to the guide (i think its the right .inf?!). When i open "wireless network drivers" it says "hardware present: yes" 

But i cant start my wireless!  
Here is the output of ```
lshw -C network
```


*-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: eth0
       version: 06
       serial: 2c:27:d7:b3:67:a9
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.0.11 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:29 ioport:4000(size=256) memory:c0404000-c0404fff(prefetchable) memory:c0400000-c0403fff(prefetchable)
  *-network UNCLAIMED
       description: Network controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0d:00.0
       version: 34
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:c4500000-c4501fff

---

### Post by xkang on 2011-09-06
...and im using 10.04 on this computer

---

### Post by wildmanne39 on 2011-09-06
Hi, post the results of these commands here please:
```
lsb_release -a
```
```
lspci -nn | grep 0280
```
```
iwconfig
```
```
rfkill list all
```
```
lsmod
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by xkang on 2011-09-06
```
lsb_release -a
```

No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 10.04.3 LTS
Release:	10.04
Codename:	lucid

```
lspci -nn | grep 0280
```
0d:00.0 Network controller [0280]: Intel Corporation Device [8086:008b] (rev 34)
```
iwconfig
```
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.
```
rfkill list all
```
0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no

```
lsmod
```
Module                  Size  Used by
rfcomm                 33421  4 
sco                     7917  2 
bridge                 45582  0 
stp                     1655  1 bridge
binfmt_misc             6587  1 
bnep                    9436  2 
l2cap                  30624  16 rfcomm,bnep
ppdev                   5259  0 
snd_hda_codec_idt      52042  1 
btusb                  11053  2 
ndiswrapper           184867  0 
bluetooth              49892  9 rfcomm,sco,bnep,l2cap,btusb
snd_hda_intel          22165  2 
snd_hda_codec          74201  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70918  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
fbcon                  35102  71 
psmouse                63677  0 
snd                    54244  16 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
tileblit                1999  1 fbcon
uvcvideo               57406  0 
hp_accel               11144  0 
lis3lv02d               6096  1 hp_accel
input_polldev           2482  1 lis3lv02d
led_class               2864  1 hp_accel
serio_raw               3978  0 
font                    7557  1 fbcon
video                  17375  0 
bitblit                 4707  1 fbcon
soundcore               6620  1 snd
softcursor              1189  1 bitblit
xhci                   37576  0 
snd_page_alloc          7172  2 snd_hda_intel,snd_pcm
output                  1871  1 video
videodev               34361  1 uvcvideo
v4l1_compat            13251  2 uvcvideo,videodev
vga16fb                11385  1 
lp                      7028  0 
vgastate                8961  1 vga16fb
parport                32635  2 ppdev,lp
r8169                  34396  0 
mii                     4381  1 r8169
ahci                   32392  2 




Thanks in advance!:)

---

### Post by wildmanne39 on 2011-09-06
Delete I post in the wrong thread, I had to many windows opened, part of the instructions was for this thread and part for another, I will not have that many tabs opened again

---

### Post by bkratz on 2011-09-06
@wildmanne39 does the OP have an Intel wireless card? Is that the right driver?

0d:00.0 Network controller [0280]: Intel Corporation Device [8086:008b] (rev 34)

---

### Post by praseodym on 2011-09-06
```
0d:00.0 Network controller [0280]: Intel Corporation Device [8086:008b] (rev 34)
```

Imho this device is only supported from Kernel 3 and on with the module **iwlagn**. The Broadcom STA driver is not suitable, but uninstalling **ndiswrapper** is a good idea.

---

### Post by wildmanne39 on 2011-09-06
Hi, you are correct I posted this in the wrong thread.
Thank you

---

### Post by wildmanne39 on 2011-09-06
Hi, I checked with the stock kernel in 10.04 and the driver for your card is not there, but I checked this kernel 2.6.38-11-generic in 11.04 and it is present.

I would suggest upgrading, or run these commands so we can see if it is present with your kernel which I doubt but it might be.
```
uname -a
```
```
modinfo iwlagn
```
Thank you

---

### Post by xkang on 2011-09-07
```
uname -a
```
Linux xkang-laptop 2.6.32-33-generic-pae #72-Ubuntu SMP Fri Jul 29 22:06:29 UTC 2011 i686 GNU/Linux

```
modinfo iwlagn
```
filename:       /lib/modules/2.6.32-33-generic-pae/kernel/drivers/net/wireless/iwlwifi/iwlagn.ko
alias:          iwl4965
license:        GPL
author:         Copyright(c) 2003-2009 Intel Corporation <ilw@linux.intel.com>
version:        1.3.27k
description:    Intel(R) Wireless WiFi Link AGN driver for Linux
firmware:       iwlwifi-4965-2.ucode
firmware:       iwlwifi-5150-2.ucode
firmware:       iwlwifi-5000-2.ucode
firmware:       iwlwifi-6050-4.ucode
firmware:       iwlwifi-6000-4.ucode
srcversion:     AFA2F2178A034C79AF40B8A
alias:          pci:v00008086d00000084sv*sd*bc*sc*i*
alias:          pci:v00008086d00000083sv*sd*bc*sc*i*
alias:          pci:v00008086d00000089sv*sd*bc*sc*i*
alias:          pci:v00008086d00000088sv*sd*bc*sc*i*
alias:          pci:v00008086d00000087sv*sd*bc*sc*i*
alias:          pci:v00008086d00000086sv*sd*bc*sc*i*
alias:          pci:v00008086d00004239sv*sd*bc*sc*i*
alias:          pci:v00008086d00004238sv*sd*bc*sc*i*
alias:          pci:v00008086d0000422Csv*sd*bc*sc*i*
alias:          pci:v00008086d0000422Bsv*sd*bc*sc*i*
alias:          pci:v00008086d0000008Esv*sd*bc*sc*i*
alias:          pci:v00008086d0000008Dsv*sd*bc*sc*i*
alias:          pci:v00008086d0000423Dsv*sd00001316bc*sc*i*
alias:          pci:v00008086d0000423Dsv*sd00001216bc*sc*i*
alias:          pci:v00008086d0000423Dsv*sd00001311bc*sc*i*
alias:          pci:v00008086d0000423Dsv*sd00001211bc*sc*i*
alias:          pci:v00008086d0000423Csv*sd00001321bc*sc*i*
alias:          pci:v00008086d0000423Csv*sd00001221bc*sc*i*
alias:          pci:v00008086d0000423Csv*sd00001306bc*sc*i*
alias:          pci:v00008086d0000423Csv*sd00001206bc*sc*i*
alias:          pci:v00008086d0000423Csv*sd00001301bc*sc*i*
alias:          pci:v00008086d0000423Csv*sd00001201bc*sc*i*
alias:          pci:v00008086d0000423Bsv*sd00001011bc*sc*i*
alias:          pci:v00008086d0000423Asv*sd00001021bc*sc*i*
alias:          pci:v00008086d0000423Asv*sd00001001bc*sc*i*
alias:          pci:v00008086d00004236sv*sd00001114bc*sc*i*
alias:          pci:v00008086d00004236sv*sd00001014bc*sc*i*
alias:          pci:v00008086d00004236sv*sd00001111bc*sc*i*
alias:          pci:v00008086d00004236sv*sd00001011bc*sc*i*
alias:          pci:v00008086d00004235sv*sd00001104bc*sc*i*
alias:          pci:v00008086d00004235sv*sd00001004bc*sc*i*
alias:          pci:v00008086d00004235sv*sd00001101bc*sc*i*
alias:          pci:v00008086d00004235sv*sd00001001bc*sc*i*
alias:          pci:v00008086d00004235sv*sd00001124bc*sc*i*
alias:          pci:v00008086d00004235sv*sd00001024bc*sc*i*
alias:          pci:v00008086d00004235sv*sd00001121bc*sc*i*
alias:          pci:v00008086d00004235sv*sd00001021bc*sc*i*
alias:          pci:v00008086d00004237sv*sd00001316bc*sc*i*
alias:          pci:v00008086d00004237sv*sd00001216bc*sc*i*
alias:          pci:v00008086d00004237sv*sd00001315bc*sc*i*
alias:          pci:v00008086d00004237sv*sd00001215bc*sc*i*
alias:          pci:v00008086d00004237sv*sd00001314bc*sc*i*
alias:          pci:v00008086d00004237sv*sd00001214bc*sc*i*
alias:          pci:v00008086d00004237sv*sd00001311bc*sc*i*
alias:          pci:v00008086d00004237sv*sd00001211bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001326bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001226bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001325bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001225bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001324bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001224bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001321bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001221bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001306bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001206bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001305bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001205bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001304bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001204bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001301bc*sc*i*
alias:          pci:v00008086d00004232sv*sd00001201bc*sc*i*
alias:          pci:v00008086d00004230sv*sd*bc*sc*i*
alias:          pci:v00008086d00004229sv*sd*bc*sc*i*
depends:        iwlcore,mac80211,cfg80211
vermagic:       2.6.32-33-generic-pae SMP mod_unload modversions 586TSC 
parm:           swcrypto50:using software crypto engine (default 0 [hardware])
 (bool)
parm:           queues_num50:number of hw queues in 50xx series (int)
parm:           11n_disable50:disable 50XX 11n functionality (int)
parm:           amsdu_size_8K50:enable 8K amsdu size in 50XX series (int)
parm:           fw_restart50:restart firmware in case of error (int)
parm:           antenna:select antenna (1=Main, 2=Aux, default 0 [both]) (int)
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           disable_hw_scan:disable hardware scanning (default 0) (int)
parm:           queues_num:number of hw queues. (int)
parm:           11n_disable:disable 11n functionality (int)
parm:           amsdu_size_8K:enable 8K amsdu size (int)
parm:           fw_restart4965:restart firmware in case of error (int)

---

### Post by wildmanne39 on 2011-09-07
Hi, your card is not supported in 10.04 I would suggest to upgrade to 11.04 unless you have a real old computer since it is support in 11.04, You can always use classic mode but it will be gone in the next release.
Thank you

---

### Post by xkang on 2011-09-22
well, i recently upgraded to 11,04, but my wifi still wont work, Why?!:confused:

---

### Post by wildmanne39 on 2011-09-22
Hi, post the results of these commands please:
```
sudo lshw -C network
```
```
cat /etc/lsb-release; uname -a
```
```
iwconfig
```
```
rfkill list all
```
```
lsmod
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by xkang on 2011-09-23
```
sudo lshw -C network
```
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: eth0
       version: 06
       serial: 2c:27:d7:b3:67:a9
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.0.10 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:42 ioport:4000(size=256) memory:c0404000-c0404fff memory:c0400000-c0403fff
  *-network UNCLAIMED
       description: Network controller
       product: Centrino Wireless-N 1030
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0d:00.0
       version: 34
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:c4500000-c4501fff

```
cat /etc/lsb-release; uname -a
```
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.04
DISTRIB_CODENAME=natty
DISTRIB_DESCRIPTION="Ubuntu 11.04"
Linux xkang-laptop 2.6.38-11-generic-pae #50-Ubuntu SMP Mon Sep 12 22:21:04 UTC 2011 i686 i686 i386 GNU/Linux

```
iwconfig
```
lo        no wireless extensions.

eth0      no wireless extensions.

```
rfkill list all
```
0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
```
lsmod
```
Module                  Size  Used by
parport_pc             32111  0 
ppdev                  12849  0 
snd_hda_codec_hdmi     27535  1 
snd_hda_codec_idt      60537  1 
rfcomm                 38125  8 
binfmt_misc            13213  1 
sco                    17827  2 
bnep                   17785  2 
l2cap                  48656  16 rfcomm,bnep
joydev                 17322  0 
snd_hda_intel          28209  4 
snd_hda_codec          90901  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80042  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
i915                  451068  2 
snd_seq_midi_event     14475  1 snd_seq_midi
btusb                  18160  2 
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
fglrx                2434640  0 
snd_timer              28659  2 snd_pcm,snd_seq
hp_wmi                 13418  0 
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
sparse_keymap          13666  1 hp_wmi
bluetooth              65493  9 rfcomm,sco,bnep,l2cap,btusb
snd                    55295  17 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ndiswrapper           192828  0 
rts_pstor             348243  0 
soundcore              12600  1 snd
drm_kms_helper         40745  1 i915
psmouse                59039  0 
serio_raw              12990  0 
uvcvideo               66851  0 
videodev               75143  1 uvcvideo
drm                   184164  3 i915,drm_kms_helper
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
i2c_algo_bit           13184  1 i915
video                  18951  1 i915
hp_accel               21632  0 
lis3lv02d              19285  1 hp_accel
input_polldev          13735  1 lis3lv02d
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
r8169                  46630  0 
ahci                   21591  2 
xhci_hcd               72190  0 
libahci                25548  1 ahci

---

### Post by wildmanne39 on 2011-09-23
Hi, please run this command:
```
sudo apt-get install linux-backports-modules-wireless-natty-generic
```
then restart your computer after you unplug your wired connection.
Thank you

---

### Post by xkang on 2011-09-24
> **wildmanne39 said:**
> Hi, please run this command:
```
sudo apt-get install linux-backports-modules-wireless-natty-generic
```
then restart your computer after you unplug your wired connection.
Thank you


xkang@xkang-laptop:~$ sudo apt-get install linux-backports-modules-wireless-natty-generic
[sudo] password for xkang: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package linux-backports-modules-wireless-natty-generic

Im guessing that i must add some repostory or something right?
Thanks for your time!

---

### Post by praseodym on 2011-09-24
Hi,

in Natty the filename is

linux-backports-modules-cw-2.6.39-natty-generic

---

