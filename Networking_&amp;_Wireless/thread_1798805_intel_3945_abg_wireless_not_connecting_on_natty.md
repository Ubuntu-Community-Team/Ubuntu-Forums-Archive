---
title: "intel 3945 abg wireless not connecting on natty"
date: 2011-07-06
forum: Networking &amp; Wireless
---

### Post by dimebagbarrett on 2011-07-06
Hello, i can't connect to my wireless network (wpa psk) with ubuntu 11.04 and my wifi card Intel 3945 ABG. i've done some search on the forums here and none of the workaround i've found works.

```
root@razor:~# cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.04
DISTRIB_CODENAME=natty
DISTRIB_DESCRIPTION="Ubuntu 11.04"

```

```
root@razor:~# uname -a
Linux razor 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 i686 i686 i386 GNU/Linux

```

```
root@razor:~# lspci | grep -i wirel
03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)

```

```
root@razor:~# lshw -C network
  *-network               
       description: Wireless interface
       product: PRO/Wireless 3945ABG [Golan] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 02
       serial: 00:13:02:bc:4f:9a
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 driverversion=2.6.38-8-generic firmware=15.32.2.9 latency=0 link=no multicast=yes wireless=IEEE 802.11abg
       resources: irq:45 memory:fe1ff000-fe1fffff
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 7
       bus info: pci@0000:06:07.0
       logical name: eth0
       version: 10
       serial: 00:18:f3:32:e6:3d
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.102 latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes port=MII speed=100Mbit/s
       resources: irq:16 ioport:d800(size=256) memory:feafe400-feafe4ff

```

```
root@razor:~# lsmod
Module                  Size  Used by
iwl3945               130113  0 
arc4                   12473  2 
iwlcore               148965  1 iwl3945
mac80211              257001  2 iwl3945,iwlcore
cfg80211              156212  3 iwl3945,iwlcore,mac80211
binfmt_misc            13213  1 
parport_pc             32111  0 
ppdev                  12849  0 
vesafb                 13449  1 
joydev                 17322  0 
snd_hda_codec_si3054    12924  1 
snd_hda_codec_analog    75442  1 
nvidia               7098106  26 
snd_hda_intel          24140  2 
snd_hda_codec          90901  3 snd_hda_codec_si3054,snd_hda_codec_analog,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80244  3 snd_hda_codec_si3054,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
video                  18951  0 
r852                   17878  0 
sm_common              16737  1 r852
nand                   49822  2 r852,sm_common
nand_ids                8547  1 nand
nand_ecc               13070  1 nand
psmouse                73312  0 
mtd                    26720  2 sm_common,nand
snd                    55295  14 snd_hda_codec_si3054,snd_hda_codec_analog,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ndiswrapper           192828  0 
asus_laptop            19298  0 
sparse_keymap          13666  1 asus_laptop
serio_raw              12990  0 
soundcore              12600  1 snd
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
coretemp               13283  0 
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
8139too                23208  0 
firewire_ohci          31504  0 
8139cp                 22497  0 
sdhci_pci              13623  0 
firewire_core          56138  1 firewire_ohci
sdhci                  22720  1 sdhci_pci
crc_itu_t              12627  1 firewire_core

```

```
root@razor:~# dmesg | grep iwl
[  128.940905] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, in-tree:s
[  128.940911] iwl3945: Copyright(c) 2003-2010 Intel Corporation
[  128.941000] iwl3945 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[  128.941016] iwl3945 0000:03:00.0: setting latency timer to 64
[  128.995129] iwl3945 0000:03:00.0: Tunable channels: 13 802.11bg, 23 802.11a channels
[  128.995134] iwl3945 0000:03:00.0: Detected Intel Wireless WiFi Link 3945ABG
[  128.995290] iwl3945 0000:03:00.0: irq 45 for MSI/MSI-X
[  129.041453] ieee80211 phy0: Selected rate control algorithm 'iwl-3945-rs'
[  129.125791] iwl3945 0000:03:00.0: loaded firmware version 15.32.2.9

```

```
root@razor:~# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:"barretta"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          

```

if i try to connect to my ap with network manager dmesg output this:

```
[ 1397.935867] wlan0: direct probe to 00:22:b0:e8:55:f2 (try 1/3)
[ 1398.132047] wlan0: direct probe to 00:22:b0:e8:55:f2 (try 2/3)
[ 1398.332084] wlan0: direct probe to 00:22:b0:e8:55:f2 (try 3/3)
[ 1398.532071] wlan0: direct probe to 00:22:b0:e8:55:f2 timed out

```
and networkmanager ask me for the connection password even if the one i've entered previously is right (i know it's right because i can connect with other 2 wireless pc's) 

i know that the hardware is ok because windows 7 / xp can connect with it.
any ideas?

---

### Post by dimebagbarrett on 2011-07-08
No one? meanwhile , i've found an old puppylinux disk with the ipw3945 driver instead of iwl3945 and worked right out of the box. 

is there a way to use ipw on natty? should i compile the driver by hand or there is some sort of back-back-backport modules with ipw for natty? i dont want to go back to outdated distros to use my wireless nic.

---

