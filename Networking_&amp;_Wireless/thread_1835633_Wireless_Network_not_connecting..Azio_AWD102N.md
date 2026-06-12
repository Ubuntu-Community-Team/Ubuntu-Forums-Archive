---
title: "Wireless Network not connecting..Azio AWD102N"
date: 2011-08-29
forum: Networking &amp; Wireless
---

### Post by ready_rover on 2011-08-29
Ubuntu 11.04
Total Noob to Linux...windows since 3.1...ignorant but will be educated..

Wired and wireless network options on desktop...wired works..still trying wireless card..must move to another room..can't run cable..wireless card works perfectly on WinXP...downloaded and extracted Linux driver but can't get .tar to execute and running short of daylight...I have found and will study the "baby talk guide" for Ubuntu..I LOVE THE OS! I'm just plain ignorant right now. 

What I have so far from the "offline troubleshooting suggestions":


grandsand3@grandsand3-desktop:~$ nm-tool

NetworkManager Tool

State: disconnected

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            8139too
  State:             unavailable
  Default:           no
  HW Address:        00:14:85:C8:36:B7

  Capabilities:
    Carrier Detect:  yes
    Speed:           10 Mb/s

  Wired Properties
    Carrier:         off


grandsand3@grandsand3-desktop:~$ sudo lshw -C network
[sudo] password for grandsand3: 
  *-network:0 UNCLAIMED   
       description: Network controller
       product: Ralink corp.
       vendor: Ralink corp.
       physical id: 7
       bus info: pci@0000:02:07.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=32 maxlatency=4 mingnt=2
       resources: memory:fa000000-fa00ffff
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: a
       bus info: pci@0000:02:0a.0
       logical name: eth0
       version: 10
       serial: 00:14:85:c8:36:b7
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10Mbit/s
       resources: irq:18 ioport:c000(size=256) memory:fa010000-fa0100ff
grandsand3@grandsand3-desktop:~$ sudo lsmod
Module                  Size  Used by
binfmt_misc            13213  1 
snd_intel8x0           33213  2 
snd_ac97_codec        105614  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80042  2 snd_intel8x0,snd_ac97_codec
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    55295  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i2c_ali15x3            12878  0 
soundcore              12600  1 snd
snd_page_alloc         14073  2 snd_intel8x0,snd_pcm
i2c_ali1563            12891  0 
i2c_ali1535            12777  0 
psmouse                73312  0 
ns558                  12618  0 
serio_raw              12990  0 
gameport               15027  2 ns558
nouveau               621970  2 
ttm                    65184  1 nouveau
drm_kms_helper         40745  1 nouveau
drm                   184164  4 nouveau,ttm,drm_kms_helper
k8temp                 12872  0 
i2c_algo_bit           13184  1 nouveau
ppdev                  12849  0 
video                  18951  1 nouveau
parport_pc             32111  1 
shpchp                 32345  0 
lp                     13349  0 
parport                36746  3 ppdev,parport_pc,lp
8139too                23208  0 
floppy                 60032  0 
8139cp                 22497  0 
pata_ali               13564  0 
sata_uli               12693  2 
grandsand3@grandsand3-desktop:~$ sudo iwlist
Usage: iwlist [interface] scanning [essid NNN] [last]
              [interface] frequency 
              [interface] channel 
              [interface] bitrate 
              [interface] rate 
              [interface] encryption 
              [interface] keys 
              [interface] power 
              [interface] txpower 
              [interface] retry 
              [interface] ap 
              [interface] accesspoints 
              [interface] peers 
              [interface] event 
              [interface] auth 
              [interface] wpakeys 
              [interface] genie 
              [interface] modulation 
grandsand3@grandsand3-desktop:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

grandsand3@grandsand3-desktop:~$ 


All help greatly appreciated with humility!

ready_rover

---

### Post by praseodym on 2011-08-29
Hi,

can you show the following outputs:

```
lspci -nnk | grep -iA2 net
lsusb
iwconfig
rfkill list
```

---

### Post by ready_rover on 2011-08-29
> **praseodym said:**
> Hi,

can you show the following outputs:

```
lspci -nnk | grep -iA2 net
lsusb
iwconfig
rfkill list
```


Certainly, thanks!

grandsand3@grandsand3-desktop:~$ lspci -nnk | grep -iA2 net
02:07.0 Network controller [0280]: Ralink corp. Device [1814:3062]
    Subsystem: Ralink corp. Device [1814:3062]
    Kernel modules: rt2800pci
02:0a.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
    Subsystem: Giga-byte Technology GA-7VM400M/7VT600 Motherboard [1458:e000]
    Kernel driver in use: 8139too
grandsand3@grandsand3-desktop:~$ lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
grandsand3@grandsand3-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

grandsand3@grandsand3-desktop:~$ rfkill list
grandsand3@grandsand3-desktop:~$

---

### Post by praseodym on 2011-08-29
For this device the driver has to be installed by hand:

```
sudo apt-get install --reinstall linux-headers-$(uname -r) build-essential dkms 
wget http://media.cdn.ubuntu-de.org/forum/attachments/2739482/DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217_prepared.tar.gz
tar xvf DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217_prepared.tar.gz
cd DPO_RT3562_3592_3062_LinuxSTA_V2.4.1.1_20101217_prepared
sudo make
sudo make install 
echo "blacklist rt2800pci" | sudo tee -a /etc/modprobe.d/blacklist.conf 
```
and reboot. Just copy&paste the lines one by one into the terminal.

Controls:

```
uname -a
lspci -nnk | grep -iA2 net
lsmod
iwconfig
sudo iwlist scan
dmesg | egrep 'rt2|rt3'
```

---

### Post by ready_rover on 2011-08-29
Thank you, PRASEODYM!!

Works perfectly! I will pay this forward as I can. Now to my Ubuntu education! 

How do I mark this SOLVED!!!

:guitar::popcorn:

---

### Post by praseodym on 2011-08-29
Edit the first post and check the drp-down-menu left of the title

---

### Post by praseodym on 2011-08-30
P.S.: You may want to install the metapackage of the headers for them being updated automatically:

```
sudo apt-get install linux-headers-generic
```

---

