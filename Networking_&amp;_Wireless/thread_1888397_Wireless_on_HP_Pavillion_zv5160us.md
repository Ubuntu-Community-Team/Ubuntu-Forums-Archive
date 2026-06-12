---
title: "Wireless on HP Pavillion zv5160us"
date: 2011-11-29
forum: Networking &amp; Wireless
---

### Post by noelcasidy on 2011-11-29
I am new to Ubuntu and have installed it on my laptop (hp pavillion zv5160us). I looked a another thread about the same problem, so I am pasting the results of 3 terminal commands that were asked for.

```
00:00.0 Host bridge: ATI Technologies Inc Radeon 9100 IGP Host Bridge (rev 02)
00:01.0 PCI bridge: ATI Technologies Inc Radeon 9100 IGP AGP Bridge
00:13.0 USB Controller: ATI Technologies Inc OHCI USB Controller #1 (rev 01)
00:13.1 USB Controller: ATI Technologies Inc OHCI USB Controller #2 (rev 01)
00:14.0 SMBus: ATI Technologies Inc SMBus (rev 16)
00:14.1 IDE interface: ATI Technologies Inc Dual Channel Bus Master PCI IDE Controller
00:14.3 ISA bridge: ATI Technologies Inc Device 434c
00:14.4 PCI bridge: ATI Technologies Inc IXP200 3COM 3C920B Ethernet Controller
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP150 AC'97 Audio Controller
00:14.6 Modem: ATI Technologies Inc IXP AC'97 Modem (rev 01)
01:05.0 VGA compatible controller: ATI Technologies Inc RS300M AGP [Radeon Mobility 9100IGP]
02:02.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
02:03.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:04.0 CardBus bridge: Texas Instruments PCI1520 PC card Cardbus Controller (rev 01)
02:04.1 CardBus bridge: Texas Instruments PCI1520 PC card Cardbus Controller (rev 01)
02:07.0 USB Controller: NEC Corporation USB (rev 43)
02:07.1 USB Controller: NEC Corporation USB (rev 43)
02:07.2 USB Controller: NEC Corporation USB 2.0 (rev 04)
noel@noel-Pavilion-zv5000-DZ330U-ABA:~$ 
```

```
WARNING: you should run this program as super-user.
  *-network:0             
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 2
       bus info: pci@0000:02:02.0
       version: 03
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64
       resources: irq:18 memory:d0200000-d0201fff
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 3
       bus info: pci@0000:02:03.0
       logical name: eth0
       version: 10
       serial: 00:02:3f:6f:c8:e2
       size: 100Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.1.111 latency=128 maxlatency=64 mingnt=32 multicast=yes port=MII speed=100Mbit/s
       resources: irq:19 ioport:a000(size=256) memory:d0204000-d02040ff
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:90:4b:4f:19:6e
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=3.0.0-13-generic firmware=N/A multicast=yes wireless=IEEE 802.11bg
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.
noel@noel-Pavilion-zv5000-DZ330U-ABA:~$ 

```
```
oel@noel-Pavilion-zv5000-DZ330U-ABA:~$ lsmod
Module                  Size  Used by
bnep                   17923  2 
rfcomm                 38408  0 
bluetooth             148839  10 bnep,rfcomm
joydev                 17393  0 
ppdev                  12849  0 
snd_atiixp             19337  2 
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
arc4                   12473  2 
snd_seq_midi_event     14475  1 snd_seq_midi
b43                   318816  0 
pcmcia                 39822  0 
snd_atiixp_modem       18604  5 
snd_ac97_codec        106082  2 snd_atiixp,snd_atiixp_modem
ac97_bus               12642  1 snd_ac97_codec
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
mac80211              393459  1 b43
snd_pcm                80468  5 snd_atiixp,snd_atiixp_modem,snd_ac97_codec
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd_timer              28932  2 snd_seq,snd_pcm
cfg80211              172392  2 b43,mac80211
psmouse                73673  0 
yenta_socket           27428  0 
pcmcia_rsrc            18367  1 yenta_socket
snd                    55902  20 snd_atiixp,snd_rawmidi,snd_atiixp_modem,snd_ac97_codec,snd_seq,snd_pcm,snd_seq_device,snd_timer
serio_raw              12990  0 
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
soundcore              12600  1 snd
snd_page_alloc         14115  3 snd_atiixp,snd_atiixp_modem,snd_pcm
radeon                925094  2 
ttm                    65224  1 radeon
drm_kms_helper         32889  1 radeon
drm                   192226  4 radeon,ttm,drm_kms_helper
parport_pc             32114  1 
video                  18908  0 
i2c_algo_bit           13199  1 radeon
binfmt_misc            17292  1 
wmi                    18744  0 
i2c_piix4              13093  0 
ati_agp                13242  1 , thanks
shpchp                 32356  0 
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
8139too                23283  0 
8139cp                 22636  0 
pata_atiixp            12967  2 
ssb                    50682  1 b43
noel@noel-Pavilion-zv5000-DZ330U-ABA:~$ 

```
any help appreciated

---

### Post by nothingspecial on 2011-11-29
Can you get a wired connection and update your system?

---

### Post by noelcasidy on 2011-11-29
I can get a wired connection and did update. Still no wireless connection. Says firmware missing.

---

### Post by trundlenut on 2011-11-30
Try installing the b43-fwcutter package.

---

### Post by mörgæs on 2011-11-30
Moved to Wireless and Networking, title changed.

---

### Post by praseodym on 2011-11-30
Hi,

install the packages **b43-fwcutter** and **firmware-b43-installer** via software center and reboot.

---

### Post by ANROKI on 2013-01-03
Hello,
This is my first post in a linux forum, and my first time using Linux. Forgive my ignorance. But I have the same wireless problem with my HP Pavillion zv5000. I'm currently plugged in with an ethernet cable. Anyway, I typed **b43-fwcutter** and **firmware-b43-installer **into the search bar in the software center and nothing came up. Is that the correct place to look?

---

### Post by mörgæs on 2013-01-04
Welcome to the fora.

Best is to use Software Centre as little as possible. Better to install using the command

```
sudo apt-get install b43-fwcutter
```

and

```
sudo apt-get install firmware-b43-installer
```

You might need a reboot after installing.

---

