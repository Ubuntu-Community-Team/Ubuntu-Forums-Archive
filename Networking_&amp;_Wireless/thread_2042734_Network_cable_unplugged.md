---
title: "Network cable unplugged"
date: 2012-08-15
forum: Networking &amp; Wireless
---

### Post by nawaz1 on 2012-08-15
hi

I recently installed ubuntu **12.04**  but it gives me notification **" Disconnected u are offline" Network cable unplgged**...i tried** two or three ethernet cables** but invain

tell me how to get rid of this issue

---

### Post by newb85 on 2012-08-15
Can you give more details about your machine?  What version of Ubuntu are you running?

Also, does your machine have a button or switch that turns networking off/on?

---

### Post by nawaz1 on 2012-08-15
i am using **ubuntu 12.04 precise**

I install it on laptop **dell vostro1310**

internet is working fine on windows  for windows i install this ethernet driver
**Realtek RTL-8100C Ethernet Controller **

but on ubuntu it dont
[B]
no it dont have any switch[/B]

---

### Post by nawaz1 on 2012-08-15
i am using ubuntu 12.04 precise

I install it on laptop dell vostro1310

internet is working fine on windows  for windows i install this ethernet driver
Realtek RTL-8100C Ethernet Controller 

but on ubuntu it dont

no it dont have any switch

---

### Post by praseodym on 2012-08-15
Hi,

please show:

```
lspci -nnk
lsmod
ifconfig -a
cat /etc/network/interfaces
cat /etc/resolv.conf
```

---

### Post by nawaz1 on 2012-08-16
_**lspci -nnk**_

00:00.0 Host bridge [0600]: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub [8086:2a00] (rev 0c)
    Subsystem: Dell Device [1028:026f]
    Kernel driver in use: agpgart-intel
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (primary) [8086:2a02] (rev 0c)
    Subsystem: Dell Device [1028:026f]
    Kernel driver in use: i915
    Kernel modules: intelfb, i915
00:02.1 Display controller [0380]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (secondary) [8086:2a03] (rev 0c)
    Subsystem: Dell Device [1028:026f]
00:1a.0 USB controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 [8086:2834] (rev 03)
    Subsystem: Dell Device [1028:026f]
    Kernel driver in use: uhci_hcd
00:1a.1 USB controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 [8086:2835] (rev 03)
    Subsystem: Dell Device [1028:026f]
    Kernel driver in use: uhci_hcd
00:1a.7 USB controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 [8086:283a] (rev 03)
    Subsystem: Dell Device [1028:026f]
    Kernel driver in use: ehci_hcd
00:1b.0 Audio device [0403]: Intel Corporation 82801H (ICH8 Family) HD Audio Controller [8086:284b] (rev 03)
    Subsystem: Dell Device [1028:026f]
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd-hda-intel
00:1c.0 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 [8086:283f] (rev 03)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.1 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 [8086:2841] (rev 03)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.3 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 [8086:2845] (rev 03)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.4 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 [8086:2847] (rev 03)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1d.0 USB controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 [8086:2830] (rev 03)
    Subsystem: Dell Device [1028:026f]
    Kernel driver in use: uhci_hcd
00:1d.1 USB controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 [8086:2831] (rev 03)
    Subsystem: Dell Device [1028:026f]
    Kernel driver in use: uhci_hcd
00:1d.2 USB controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 [8086:2832] (rev 03)
    Subsystem: Dell Device [1028:026f]
    Kernel driver in use: uhci_hcd
00:1d.7 USB controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 [8086:2836] (rev 03)
    Subsystem: Dell Device [1028:026f]
    Kernel driver in use: ehci_hcd
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev f3)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801HM (ICH8M) LPC Interface Controller [8086:2815] (rev 03)
    Subsystem: Dell Device [1028:026f]
    Kernel modules: iTCO_wdt
00:1f.1 IDE interface [0101]: Intel Corporation 82801HM/HEM (ICH8M/ICH8M-E) IDE Controller [8086:2850] (rev 03)
    Subsystem: Dell Device [1028:026f]
    Kernel driver in use: ata_piix
00:1f.2 SATA controller [0106]: Intel Corporation 82801HM/HEM (ICH8M/ICH8M-E) SATA Controller [AHCI mode] [8086:2829] (rev 03)
    Subsystem: Dell Device [1028:026f]
    Kernel driver in use: ahci
00:1f.3 SMBus [0c05]: Intel Corporation 82801H (ICH8 Family) SMBus Controller [8086:283e] (rev 03)
    Subsystem: Dell Device [1028:026f]
    Kernel modules: i2c-i801
06:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
    Subsystem: Dell Wireless 1395 WLAN Mini-Card [1028:000b]
    Kernel driver in use: b43-pci-bridge
    Kernel modules: ssb
07:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 02)
    Subsystem: Dell Device [1028:026f]
    Kernel driver in use: r8169
    Kernel modules: r8169
08:05.0 FireWire (IEEE 1394) [0c00]: O2 Micro, Inc. Firewire (IEEE 1394) [1217:00f7] (rev 02)
    Subsystem: Dell Device [1028:026f]
    Kernel driver in use: firewire_ohci
    Kernel modules: firewire-ohci
08:05.2 SD Host controller [0805]: O2 Micro, Inc. Integrated MMC/SD Controller [1217:7120] (rev 02)
    Subsystem: Dell Device [1028:026f]
    Kernel driver in use: sdhci-pci
    Kernel modules: sdhci-pci
08:05.3 Mass storage controller [0180]: O2 Micro, Inc. Integrated MS/xD Controller [1217:7130] (rev 01)
    Subsystem: Dell Device [1028:026f]




_***lsmod***_

Module                  Size  Used by
nls_iso8859_1          12617  1 
nls_cp437              12751  1 
vfat                   17308  1 
fat                    55605  1 vfat
snd_hda_codec_realtek   174055  1 
rfcomm                 38139  0 
bnep                   17830  2 
bluetooth             158438  10 rfcomm,bnep
parport_pc             32114  0 
ppdev                  12849  0 
joydev                 17393  0 
dell_wmi               12601  0 
sparse_keymap          13658  1 dell_wmi
snd_hda_intel          32765  3 
snd_hda_codec         109562  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80845  2 snd_hda_intel,snd_hda_codec
arc4                   12473  2 
dell_laptop            13671  0 
dcdbas                 14098  1 dell_laptop
b43                   342643  0 
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
mac80211              436455  1 b43
i915                  414603  3 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
psmouse                72846  0 
serio_raw              13027  0 
drm_kms_helper         45466  1 i915
cfg80211              178679  2 b43,mac80211
drm                   197692  4 i915,drm_kms_helper
snd                    62064  15 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              14635  1 snd
bcma                   25651  1 b43
i2c_algo_bit           13199  1 i915
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
wmi                    18744  1 dell_wmi
video                  19068  1 i915
mac_hid                13077  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
firewire_ohci          40172  0 
sdhci_pci              18324  0 
sdhci                  28241  1 sdhci_pci
firewire_core          56906  1 firewire_ohci
crc_itu_t              12627  1 firewire_core
ssb                    50691  1 b43
r8169                  56321  0 
usb_storage            39646  1 

_***ifconfig -a***_

eth0      Link encap:Ethernet  HWaddr 00:00:00:00:00:00  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:45 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:96 errors:0 dropped:0 overruns:0 frame:0
          TX packets:96 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:7744 (7.7 KB)  TX bytes:7744 (7.7 KB)

wlan0     Link encap:Ethernet  HWaddr 00:22:5f:42:ed:ef  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

_***cat /etc/network/interfaces***_

auto lo
iface lo inet loopback


_***cat /etc/resolv.conf***_

# Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
#     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN

---

### Post by Cheesehead on 2012-08-16
Is Network Manager set up for DHCP? Is the network's DHCP server working? Do other systems on the network have similar trouble connecting?

If it is a switch/router, then have you tried different ports? Power-cycle the switch? Do other systems connect properly on that port?

Are you connecting to a switch or router, or to another desktop/laptop?
Older (and cheaper) equipment lacks TX/RX autosense, so if you are trying to connect to a non-switch/router, you may need a crossover cable instead.

Once you have ruled out network settings, a stuck port, or the wrong cable, what's left is bad news: Bad hardware.

---

### Post by praseodym on 2012-08-16
Install the package "linux-firmware-nonfree":

[http://de.archive.ubuntu.com/ubuntu/pool/multiverse/l/linux-firmware-nonfree/linux-firmware-nonfree_1.11_all.deb](http://de.archive.ubuntu.com/ubuntu/pool/multiverse/l/linux-firmware-nonfree/linux-firmware-nonfree_1.11_all.deb)

Now wireless should work. After that you can install the driver "r8169" for the LAN device:

```
sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic build-essential dkms
wget http://media.cdn.ubuntu-de.org/forum/attachments/24/23/3005217-r8168-dkms-8.031.00.tar.gz
sudo tar xvf 3005217-r8168-dkms-8.031.00.tar.gz -C /usr/src
sudo dkms add -m r8168-dkms -v 8.031.00
sudo dkms build -m r8168-dkms -v 8.031.00
sudo dkms install -m r8168-dkms -v 8.031.00 
echo "blacklist r8169" | sudo tee -a /etc/modprobe.d/blacklist.conf
sudo modprobe -rfv r8169
sudo mv /lib/modules/$(uname -r)/kernel/drivers/net/r8169.ko /lib/modules/$(uname -r)/kernel/drivers/net/r8169.bak
sudo modprobe -v r8168
```

From here:

[http://forum.ubuntuusers.de/topic/lan-karte-funktioniert-nicht/#post-3005217](http://forum.ubuntuusers.de/topic/lan-karte-funktioniert-nicht/#post-3005217)

---

### Post by nawaz1 on 2012-08-17
plz tell me how to install this firmware 
[http://de.archive.ubuntu.com/ubuntu/...e_1.11_all.deb]("http://de.archive.ubuntu.com/ubuntu/pool/multiverse/l/linux-firmware-nonfree/linux-firmware-nonfree_1.11_all.deb")
any command needed in terminal or what i do

---

### Post by nawaz1 on 2012-08-17
i dnt have wireless net with me plz tell me alternate way to dowload drivers for wired network plz

---

### Post by praseodym on 2012-08-17
Double click the .deb file and install it with the software center. Alternatively, save the file in "Downloads" and install via:

> sudo dpkg -i ~/Downloads/*.deb
Reboot and check

> iwconfig
lsmod
dmesg | grep b43

---

### Post by newb85 on 2012-08-20
> **nawaz1 said:**
> plz tell me how to install this firmware 
[http://de.archive.ubuntu.com/ubuntu/...e_1.11_all.deb]("http://de.archive.ubuntu.com/ubuntu/pool/multiverse/l/linux-firmware-nonfree/linux-firmware-nonfree_1.11_all.deb")
any command needed in terminal or what i do

Once you have that file in your system, try opening it with the Software Center.  (Right-click, Open With Ubuntu Software Center)  Installing should be straight-forward from there.

---

### Post by nawaz1 on 2012-08-20
nawaz@nawaz-desktop:~$ sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic build-essential dkms
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reinstallation of linux-headers-2.6.20-15-generic is not possible, it cannot be downloaded.
Reinstallation of build-essential is not possible, it cannot be downloaded.
E: Couldn't find package dkms


tell me what i do

---

### Post by praseodym on 2012-08-20
2.6.20???? Please show:
> 
uname -a
lsb_release -a
Which Ubuntuversion do you use?

---

### Post by nawaz1 on 2012-08-20
[FONT=&quot]nawazbaig@ubuntu:~$ cat /etc/lsb-release
[B]DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04 LTS"[/B][/FONT]
[FONT=&quot]
[/FONT]
[FONT=&quot]
[/FONT]
[FONT=&quot]nawazbaig@ubuntu:~$[/FONT] uname -r
[FONT=&quot] **3.2.0-23-generic-pae**
[/FONT]

---

### Post by praseodym on 2012-08-20
Ok, it needs to be:
> 
sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic-pae build-essential dkms

---

### Post by cozski on 2013-01-20
> **praseodym said:**
> Hi,

please show:

```
lspci -nnk
lsmod
ifconfig -a
cat /etc/network/interfaces
cat /etc/resolv.conf
```


Hello, I've just done a clean install of the latest version of Ubuntu on a Dell Inspiron 6400 and I have the same problem. Ethernet cable is showing as unplugged. I have taken the liberty of following your advice here and I'm posting the output. I did try jumping straight to installing the .deb package you linked to further down but when it opens in Package Manager it remains greyed out so I can't install; so I presume it's not the solution to my problem. Any help appreciated.

  
   
  **lspci  -nnk**
     
   
  00:00.0 Host bridge [0600]: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub [8086:27a0] (rev 03)
          Subsystem: Dell Device [1028:01bd]
          Kernel driver in use: agpgart-intel
    00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller [8086:27a2] (rev 03)
          Subsystem: Dell Device [1028:01bd]
          Kernel driver in use: i915
          Kernel modules: intelfb, i915
    00:02.1 Display controller [0380]: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller [8086:27a6] (rev 03)
          Subsystem: Dell Device [1028:01bd]
    00:1b.0 Audio device [0403]: Intel Corporation NM10/ICH7 Family High Definition Audio Controller [8086:27d8] (rev 01)
          Subsystem: Dell Device [1028:01bd]
          Kernel driver in use: snd_hda_intel
          Kernel modules: snd-hda-intel
    00:1c.0 PCI bridge [0604]: Intel Corporation NM10/ICH7 Family PCI Express Port 1 [8086:27d0] (rev 01)
          Kernel driver in use: pcieport
          Kernel modules: shpchp
    00:1c.3 PCI bridge [0604]: Intel Corporation NM10/ICH7 Family PCI Express Port 4 [8086:27d6] (rev 01)
          Kernel driver in use: pcieport
          Kernel modules: shpchp
    00:1d.0 USB controller [0c03]: Intel Corporation NM10/ICH7 Family USB UHCI Controller #1 [8086:27c8] (rev 01)
          Subsystem: Dell Device [1028:01bd]
          Kernel driver in use: uhci_hcd
    00:1d.1 USB controller [0c03]: Intel Corporation NM10/ICH7 Family USB UHCI Controller #2 [8086:27c9] (rev 01)
          Subsystem: Dell Device [1028:01bd]
          Kernel driver in use: uhci_hcd
    00:1d.2 USB controller [0c03]: Intel Corporation NM10/ICH7 Family USB UHCI Controller #3 [8086:27ca] (rev 01)
          Subsystem: Dell Device [1028:01bd]
          Kernel driver in use: uhci_hcd
    00:1d.3 USB controller [0c03]: Intel Corporation NM10/ICH7 Family USB UHCI Controller #4 [8086:27cb] (rev 01)
          Subsystem: Dell Device [1028:01bd]
          Kernel driver in use: uhci_hcd
    00:1d.7 USB controller [0c03]: Intel Corporation NM10/ICH7 Family USB2 EHCI Controller [8086:27cc] (rev 01)
          Subsystem: Dell Device [1028:01bd]
          Kernel driver in use: ehci_hcd
    00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e1)
    00:1f.0 ISA bridge [0601]: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge [8086:27b9] (rev 01)
          Subsystem: Dell Device [1028:01bd]
          Kernel driver in use: lpc_ich
          Kernel modules: leds-ss4200, lpc_ich, intel-rng
    00:1f.2 IDE interface [0101]: Intel Corporation 82801GBM/GHM (ICH7-M Family) SATA Controller [IDE mode] [8086:27c4] (rev 01)
          Subsystem: Dell Device [1028:01bd]
          Kernel driver in use: ata_piix
    00:1f.3 SMBus [0c05]: Intel Corporation NM10/ICH7 Family SMBus Controller [8086:27da] (rev 01)
          Subsystem: Dell Device [1028:01bd]
          Kernel modules: i2c-i801
    03:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
          Subsystem: Dell Inspiron 6400 [1028:01af]
          Kernel driver in use: b44
          Kernel modules: b44
    03:01.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832]
          Subsystem: Dell Device [1028:01bd]
          Kernel driver in use: firewire_ohci
          Kernel modules: firewire-ohci
    03:01.1 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 19)
          Subsystem: Dell Device [1028:01bd]
          Kernel driver in use: sdhci-pci
          Kernel modules: sdhci-pci
    03:01.2 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 0a)
          Subsystem: Dell Device [1028:01bd]
          Kernel driver in use: r592
          Kernel modules: r592
    03:01.3 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller [1180:0852] (rev 05)
          Subsystem: Dell Device [1028:01bd]
          Kernel driver in use: r852
          Kernel modules: r852
    0b:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11b/g WLAN [14e4:4311] (rev 01)
          Subsystem: Dell Wireless 1390 WLAN Mini-Card [1028:0007]
          Kernel driver in use: b43-pci-bridge
          Kernel modules: ssb
     
   
  **lsmod**
  
   
   
  Module                  Size  Used by
    nls_iso8859_1          12617  1 
    uas                    17556  0 
    usb_storage            39350  1 
    joydev                 17161  0 
    parport_pc             31968  0 
    ppdev                  12817  0 
    rfcomm                 37276  0 
    bnep                   17707  2 
    bluetooth             183228  10 rfcomm,bnep
    snd_hda_codec_idt      59761  1 
    coretemp               13168  0 
    dell_wmi               12601  0 
    sparse_keymap          13658  1 dell_wmi
    gpio_ich               13159  0 
    snd_hda_intel          32515  3 
    snd_hda_codec         111547  2 snd_hda_codec_idt,snd_hda_intel
    snd_hwdep              13272  1 snd_hda_codec
    dell_laptop            17161  0 
    dcdbas                 14054  1 dell_laptop
    snd_pcm                80163  2 snd_hda_intel,snd_hda_codec
    psmouse                84843  0 
    microcode              18209  0 
    snd_seq_midi           13132  0 
    snd_rawmidi            25382  1 snd_seq_midi
    serio_raw              13031  0 
    snd_seq_midi_event     14475  1 snd_seq_midi
    r852                   17905  0 
    sm_common              16737  1 r852
    nand                   49496  2 r852,sm_common
    nand_ids                8547  1 nand
    mtd                    38602  2 sm_common,nand
    nand_bch               13003  1 nand
    bch                    17199  1 nand_bch
    nand_ecc               13070  1 nand
    r592                   17707  0 
    snd_seq                51255  2 snd_seq_midi,snd_seq_midi_event
    memstick               15842  1 r592
    i915                  457161  3 
    snd_timer              24411  2 snd_pcm,snd_seq
    drm_kms_helper         45271  1 i915
    drm                   230463  4 i915,drm_kms_helper
    i2c_algo_bit           13197  1 i915
    snd_seq_device         14137  3 snd_seq_midi,snd_rawmidi,snd_seq
    mac_hid                13037  0 
    b43                   347284  0 
    wmi                    18590  1 dell_wmi
    mac80211              461161  1 b43
    snd                    61991  15 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
    lpc_ich                16925  0 
    cfg80211              175375  2 b43,mac80211
    bcma                   34483  1 b43
    ssb_hcd                12749  0 
    soundcore              14599  1 snd
    snd_page_alloc         14036  2 snd_hda_intel,snd_pcm
    video                  18847  1 i915
    lp                     13299  0 
    parport                40753  3 parport_pc,ppdev,lp
    b44                    31326  0 
    firewire_ohci          35521  0 
    firewire_core          57492  1 firewire_ohci
    crc_itu_t              12627  1 firewire_core
    sdhci_pci              18155  0 
    sdhci                  27830  1 sdhci_pci
    ssb                    50087  3 b43,ssb_hcd,b44
     
   
  **ifconfig -a**
  
   
   
  eth0      Link encap:Ethernet  HWaddr 00:1d:09:ae:6f:ed  
              UP BROADCAST MULTICAST  MTU:1500  Metric:1
              RX packets:0 errors:0 dropped:0 overruns:0 frame:0
              TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
              collisions:0 txqueuelen:1000 
              RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
              Interrupt:17 
     
   
  lo        Link encap:Local Loopback  
              inet addr:127.0.0.1  Mask:255.0.0.0
              inet6 addr: ::1/128 Scope:Host
              UP LOOPBACK RUNNING  MTU:16436  Metric:1
              RX packets:39904 errors:0 dropped:0 overruns:0 frame:0
              TX packets:39904 errors:0 dropped:0 overruns:0 carrier:0
              collisions:0 txqueuelen:0 
              RX bytes:3268336 (3.2 MB)  TX bytes:3268336 (3.2 MB)
     
   
  **cat /etc/network/interfaces**
  
  # interfaces(5) file used by ifup(8) and ifdown(8)
    auto lo
    iface lo inet loopback
     
   
  **cat /etc/resolve.conf**
  
  # Dynamic resolv.conf(5) file for glibc resolver(3) generated by resolvconf(8)
    #     DO NOT EDIT THIS FILE BY HAND -- YOUR CHANGES WILL BE OVERWRITTEN

---

### Post by praseodym on 2013-01-20
There are no nameservers in your resolv.conf. Uninstall the package "resolvconf"

```
sudo apt-get remove --purge resolvconf
```
It will also uninstall the package "ubuntu-minimal", which does not matter. Reboot after that and check again.

---

### Post by cozski on 2013-01-20
> **praseodym said:**
> There are no nameservers in your resolv.conf. Uninstall the package "resolvconf"

```
sudo apt-get remove --purge resolvconf
```It will also uninstall the package "ubuntu-minimal", which does not matter. Reboot after that and check again.

Thanks, will do.... when you say check again do you want me to post the outputs from the terminal or just check to see if the ethernet cable is recognised?

---

### Post by ZippyUbu on 2013-01-20
```
ifconfig -a

 eth0 Link encap:Ethernet **HWaddr 00:00:00:00:00:00** 
 BROADCAST MULTICAST MTU:1500 Metric:1
 RX packets:0 errors:0 dropped:0 overruns:0 frame:0
 TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
 collisions:0 txqueuelen:1000 
 RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
 Interrupt:45 Base address:0xe000
```

It looks like the driver is incorrect as the Ethernet HWaddr is all zeros?

---

### Post by jdthood on 2013-01-20
> **praseodym said:**
> There are no nameservers in your resolv.conf. Uninstall the package "resolvconf"

The reason that resolvconf lists no nameservers in resolv.conf is that no network interface is configured. Resolvconf is working properly, so don't uninstall it.

---

### Post by praseodym on 2013-01-21
Lets have a look at:

```
cat /etc/udev/rules.d/70-persistent-net.rules
```

---

### Post by cozski on 2013-01-21
> **jdthood said:**
> The reason that resolvconf lists no nameservers in resolv.conf is that no network interface is configured. Resolvconf is working properly, so don't uninstall it.

Oops, too late... already done. Just going to post the output from the code praseodym has suggested.

---

### Post by cozski on 2013-01-21
> **praseodym said:**
> Lets have a look at:

```
cat /etc/udev/rules.d/70-persistent-net.rules
```

```
# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:1e.0/0000:03:00.0/ssb1:0 (b44)
 SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:1d:09:ae:6f:ed", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
 sunonthecross@sunonthecross-MM061:~$  

```

---

### Post by jdthood on 2013-01-21
> **cozski said:**
> Oops, too late... already done.

You should reinstall resolvconf.

If you want a dynamicly updated resolv.conf then you should install resolvconf because this is the supported infrastructure for dynamic resolv.conf.

If you do not want a dynamically updated resolv.conf then you should install resolvconf because its mere presence prevents other packages from touching /etc/resolv.conf. After installing resolvconf, remove the symbolic link at /etc/resolv.conf and put your static file there. The resolvconf program won't touch it.

---

### Post by praseodym on 2013-01-21
> ```
00:1d:09:ae:6f:ed
```
There is the MAC-address. Try to reload udev:
```

sudo service udev reload
sudo service udev restart
sudo /etc/init.d/networking restart
```
Check:```

ifconfig -a
route -n
cat /etc/resolv.conf
cat /etc/network/interfaces
```

---

### Post by cozski on 2013-01-21
> **praseodym said:**
> There is the MAC-address. Try to reload udev:
```

sudo service udev reload
sudo service udev restart
sudo /etc/init.d/networking restart
```Check:```

ifconfig -a
route -n
cat /etc/resolv.conf
cat /etc/network/interfaces
```

When I run the first terminal commands, after the third one the desktop disappears only leaving the Terminal output open, which I cant copy to anything so going to type the output out. I have not run the other terminal commands yet, waiting for your opinion on the first ones output. Cheers.

[I]Rather than invoking init scripts through /etc/init.d, use the service (8) utility, e.g service networking restart

Since the script you are attempting to invoke has been converted to an Upstart job, you msy also use the stop (8) and then restart (8) utilities, e.g stop networking . The restart (8) utility is also available[/I]

Thanks.

---

### Post by praseodym on 2013-01-21
Then try

```
sudo service networking restart
```
Otherwise create new udev setups. Backup your file first:
```

sudo mv /etc/udev/rules.d/70-persistent-net.rules /etc/udev/rules.d/70-persistent-net.bak
sudo udevadm trigger
sudo service udev reload
sudo service udev restart
```

---

### Post by cozski on 2013-01-21
> **praseodym said:**
> Then try

```
sudo service networking restart
```Otherwise create new udev setups. Backup your file first:
```

sudo mv /etc/udev/rules.d/70-persistent-net.rules /etc/udev/rules.d/70-persistent-net.bak
sudo udevadm trigger
sudo service udev reload
sudo service udev restart
```

Okay, so the first terminal command had the same effect as the previous one - desktop disappeared and had to restart. Ran 2nd set of commands all seemed fine.

---

### Post by rameshandeepak on 2013-01-22
[http://de.archive.ubuntu.com/ubuntu/...e_1.11_all.deb]("http://de.archive.ubuntu.com/ubuntu/pool/multiverse/l/linux-firmware-nonfree/linux-firmware-nonfree_1.11_all.deb")
is like an .exe file.
when you click it it would take you to the software manager where you can install the same.

---

### Post by cozski on 2013-01-25
> **cozski said:**
> Okay, so the first terminal command had the same effect as the previous one - desktop disappeared and had to restart. Ran 2nd set of commands all seemed fine.

I'm not sure if I need to do something further at this point? Should I have tried to plug the cable back in to see if it now recognises it?
Thanks.

---

