---
title: "no wired or wireless"
date: 2011-06-26
forum: Networking &amp; Wireless
---

### Post by dog-soldier on 2011-06-26
i just installed Ubuntu notebook remix on my Fujitsu T4210 convertable tablet pc. i was running 10.04 on it and all was good except the stylus didnt work, it now works. 
i tried to connect wireless and wired and neither work. can anyone help me getting wireless to work. i will be wireless more then wired.

---

### Post by josephmills on 2011-06-26
> **dog-soldier said:**
> i just installed Ubuntu notebook remix on my Fujitsu T4210 convertable tablet pc. i was running 10.04 on it and all was good except the stylus didnt work, it now works. 
i tried to connect wireless and wired and neither work. can anyone help me getting wireless to work. i will be wireless more then wired.

hi there could you open  your terminal(ctrl+alt+t) and type in ```
lspci -nn 
``` aand the this one takes some time to load ```
sudo lshw -C network 
``` then some how put them here for us to see.

---

### Post by dog-soldier on 2011-06-26
dogsoldier@dogs:~$ lspci -nn 
00:00.0 Host bridge [0600]: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub [8086:27a0] (rev 03) 
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller [8086:27a2] (rev 03) 
00:02.1 Display controller [0380]: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller [8086:27a6] (rev 03) 
00:1b.0 Audio device [0403]: Intel Corporation N10/ICH 7 Family High Definition Audio Controller [8086:27d8] (rev 02) 
00:1c.0 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 1 [8086:27d0] (rev 02) 
00:1c.1 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 2 [8086:27d2] (rev 02) 
00:1c.2 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 3 [8086:27d4] (rev 02) 
00:1d.0 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 [8086:27c8] (rev 02) 
00:1d.1 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 [8086:27c9] (rev 02) 
00:1d.2 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 [8086:27ca] (rev 02) 
00:1d.3 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 [8086:27cb] (rev 02) 
00:1d.7 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller [8086:27cc] (rev 02) 
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e2) 
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge [8086:27b9] (rev 02) 
00:1f.1 IDE interface [0101]: Intel Corporation 82801G (ICH7 Family) IDE Controller [8086:27df] (rev 02) 
00:1f.2 SATA controller [0106]: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller [8086:27c5] (rev 02) 
00:1f.3 SMBus [0c05]: Intel Corporation N10/ICH 7 Family SMBus Controller [8086:27da] (rev 02) 
02:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8055 PCI-E Gigabit Ethernet Controller [11ab:4363] (rev 12) 
05:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR5001 Wireless Network Adapter
[168c:001c] (rev 01) 
08:03.0 CardBus bridge [0607]: O2 Micro, Inc. OZ711MP1/MS1 MemoryCardBus Controller [1217:7134] (rev 20) 
08:03.1 CardBus bridge [0607]: O2 Micro, Inc. OZ711MP1/MS1 MemoryCardBus Controller [1217:7134] (rev 20) 
08:03.2 SD Host controller [0805]: O2 Micro, Inc. Integrated MMC/SD Controller [1217:7120] 
08:03.3 Bridge [0680]: O2 Micro, Inc. Integrated MS/xD Controller [1217:7130] 
dogsoldier@dogs:~$ 


dogsoldier@dogs:~$ sudo lshw -C network 
[sudo] password for dogsoldier: 
  *-network               
       description: Ethernet interface 
       product: 88E8055 PCI-E Gigabit Ethernet Controller 
       vendor: Marvell Technology Group Ltd. 
       physical id: 0 
       bus info: pci@0000:02:00.0 
       logical name: eth0 
       version: 12 
       serial: 00:17:42:1b:0c:3a 
       size: 100MB/s 
       capacity: 1GB/s 
       width: 64 bits 
       clock: 33MHz 
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation 
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.28 duplex=full firmware=N/A latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s 
       resources: irq:43 memory:f0100000-f0103fff ioport:2000(size=256) memory:28000000-2801ffff 
  *-network 
       description: Wireless interface 
       product: AR5001 Wireless Network Adapter 
       vendor: Atheros Communications Inc. 
       physical id: 0 
       bus info: pci@0000:05:00.0 
       logical name: wlan0 
       version: 01 
       serial: 00:16:e3:84:d0:46 
       width: 64 bits 
       clock: 33MHz 
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless 
       configuration: broadcast=yes driver=ath5k driverversion=2.6.35-22-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11abg 
       resources: irq:18 memory:28600000-2860ffff 
dogsoldier@dogs:~$ 

hope i got what you need

---

### Post by josephmills on 2011-06-26
lets see a ```
lsmod 
``` also try a ```
sudo modprobe ath5k
``` and could I also see a ```
rfkill list all 
``` thanks

---

### Post by dog-soldier on 2011-06-26
dogsoldier@dogs:~$ lsmod 
Module                  Size  Used by 
nls_iso8859_1           3261  1 
nls_cp437               4931  1 
vfat                    9201  1 
fat                    48240  1 vfat 
usb_storage            40172  1 
parport_pc             26058  0 
ppdev                   5556  0 
joydev                  8735  0 
binfmt_misc             6599  1 
arc4                    1165  2 
i915                  290938  4 
drm_kms_helper         30200  1 i915 
snd_hda_codec_idt      54887  1 
snd_hda_intel          22107  2 
snd_hda_codec          87552  2 snd_hda_codec_idt,snd_hda_intel 
snd_hwdep               5040  1 snd_hda_codec 
snd_pcm                71475  2 snd_hda_intel,snd_hda_codec 
snd_seq_midi            4588  0 
snd_rawmidi            17783  1 snd_seq_midi 
snd_seq_midi_event      6047  1 snd_seq_midi 
ath5k                 130051  0 
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event 
pcmcia                 35973  0 
mac80211              231541  1 ath5k 
snd_timer              19067  2 snd_pcm,snd_seq 
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq 
drm                   168054  5 i915,drm_kms_helper 
ath                     8153  1 ath5k 
snd                    49006  13 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device 
irda                  178938  0 
cfg80211              144470  3 ath5k,mac80211,ath 
intel_agp              26360  2 i915 
psmouse                59033  0 
serio_raw               4022  0 
crc_ccitt               1351  1 irda 
yenta_socket           21518  0 
pcmcia_rsrc            10566  1 yenta_socket 
fujitsu_laptop         10923  0 
i2c_algo_bit            5168  1 i915 
video                  18712  1 i915 
soundcore                880  1 snd 
pcmcia_core            14657  3 pcmcia,yenta_socket,pcmcia_rsrc 
agpgart                32011  2 drm,intel_agp 
snd_page_alloc          7120  2 snd_hda_intel,snd_pcm 
output                  1883  1 video 
lp                      7342  0 
parport                31492  3 parport_pc,ppdev,lp 
sdhci_pci               6339  0 
sdhci                  15890  1 sdhci_pci 
led_class               2633  3 ath5k,fujitsu_laptop,sdhci 
sky2                   45127  0 
ahci                   19013  0 
libahci                21667  3 ahci 
dogsoldier@dogs:~$ 



for sudo modprobe ath5k i got nothing





dogsoldier@dogs:~$ rfkill list all 
0: phy0: Wireless LAN 
	Soft blocked: no 
	Hard blocked: no 
dogsoldier@dogs:~$

---

### Post by josephmills on 2011-06-26
looks good try ```
sudo modprobe sky2
``` then plug in the ethernet cable and then ```
ifup eth0
```is it working ? if not could we see a ```
uname -a 
```  thanks

---

### Post by dog-soldier on 2011-06-26
got nothing for sudo modprobe sky2

dogsoldier@dogs:~$ ifup eth0 
ifup: failed to open statefile /var/run/network/ifstate: Permission denied 
dogsoldier@dogs:~$ 

dogsoldier@dogs:~$ uname -a 
Linux dogs 2.6.35-22-generic #33-Ubuntu SMP Sun Sep 19 20:34:50 UTC 2010 i686 GNU/Linux 
dogsoldier@dogs:~$ 



i got thinking that when i installed it today i put i didnt have internet , would that have done something?

---

### Post by josephmills on 2011-06-26
yes that would be why this is happening the iso image only hold the bear-min it uses the internet to go and get packages for your computer. If you want to re-install that would be the easy way out and it would work. Just make sure you have the cat5 cable plugged in or do a ```
sudo modprobe ath5k
``` and that will start your wireless then install

---

### Post by dog-soldier on 2011-06-27
josephmills thanks for all your help \\:D/
i tried 2 times this morning with the cat5 cable hooked up and nogo. 
what i had to do is shut down the router and modem and reboot them and now all is good both with cat5 and wireless.
thanks again

---

