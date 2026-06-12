---
title: "[solved] Internal card reader do not mount 16Gb SDHC (Class 10) Sandisk Card"
date: 2013-04-11
forum: Multimedia Software
---

### Post by leogagliardi on 2013-04-11
As the title says, the Internal Card reader of my Toshiba Satellite P855-S5200 laptop running Ubuntu 12.04 does not mount 16Gb SDHC Class 10 Sandisk cards. 
Ive got this problem also in a Sony Vaio VPC-F23JFX/BN running a Debian 6 Squeeze. I tried with two similar SDHC cards, one from my Gopro Hero2 and another from my Canon EOS T3i with same results. In both cases restarting on the Win partition the cards are mounted and used perfectly.
In other post I've seen they can see the card and it is only not mounted. In my case I don't see anything. Here you are info about my system after inserting the SDHC:

dmesg | tail
[   17.420517] [drm:gen6_sanitize_pm] *ERROR* Power management discrepancy: GEN6_RP_INTERRUPT_LIMITS expected 16000000, was 12060000
[   19.358152] wlan0: authenticate with 54:e6:fc:b1:3b:42 (try 1)
[   19.360492] wlan0: authenticated
[   19.368407] wlan0: associate with 54:e6:fc:b1:3b:42 (try 1)
[   19.374347] wlan0: RX AssocResp from 54:e6:fc:b1:3b:42 (capab=0x431 status=0 aid=1)
[   19.374355] wlan0: associated
[   19.397009] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   28.413081] [drm:gen6_sanitize_pm] *ERROR* Power management discrepancy: GEN6_RP_INTERRUPT_LIMITS expected 16070000, was 16000000
[   30.592076] wlan0: no IPv6 routers present
[   45.350018] iwlwifi 0000:02:00.0: Tx aggregation enabled on ra = 54:e6:fc:b1:3b:42 tid = 0

sudo fdisk -lu   (sorry, is in spanish but just note there is nothing about /sdb)
[sudo] password for "myuser": 

Disco /dev/sda: 750.2 GB, 750156374016 bytes
255 cabezas, 63 sectores/pista, 91201 cilindros, 1465149168 sectores en total
Unidades = sectores de 1 * 512 = 512 bytes
Tamaño de sector (lógico / físico): 512 bytes / 4096 bytes
Tamaño E/S (mínimo/óptimo): 4096 bytes / 4096 bytes
Identificador del disco: 0x35a7ca87
Dispositivo Inicio    Comienzo      Fin      Bloques  Id  Sistema
/dev/sda1   *        2048     3074047     1536000   27  WinRE NTFS oculto
/dev/sda2         3074048   194970532    95948242+   7  HPFS/NTFS/exFAT
/dev/sda3      1435205632  1465147391    14970880   17  HPFS/NTFS oculta
/dev/sda4       194971646  1435205631   620116993    5  Extendida
La partición 4 no se inició en el limite físico del sector
/dev/sda5       194971648   243798015    24413184   83  Linux
/dev/sda6       243800064  1415673855   585936896   83  Linux
/dev/sda7      1415675904  1435205631     9764864   82  Linux swap / Solaris

lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 04f2:b307 Chicony Electronics Co., Ltd 

lspci
00:00.0 Host bridge: Intel Corporation Ivy Bridge DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation Ivy Bridge Graphics Controller (rev 09)
00:14.0 USB controller: Intel Corporation Panther Point USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation Panther Point MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation Panther Point USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation Panther Point High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 1 (rev c4)
00:1c.1 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 2 (rev c4)
00:1c.3 PCI bridge: Intel Corporation Panther Point PCI Express Root Port 4 (rev c4)
00:1d.0 USB controller: Intel Corporation Panther Point USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation Panther Point LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation Panther Point 6 port SATA Controller [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation Panther Point SMBus Controller (rev 04)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)
02:00.0 Network controller: Intel Corporation Centrino Wireless-N 2200 (rev c4)
03:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. Device 5229 (rev 01)

uname -r
3.2.0-40-generic

Any help is welcome

---

### Post by mswoon on 2013-05-09
Yesterday I was not able to mount my Sony 16GB Class 10 SDHC, and googled and found your article. Then I tried with a Wintex Class10 SDHC that I knew worked, and for some reason, it did not mount as well! So I applied the tried-and-true solution that Microsoft taught, i.e. reboot. And indeed it worked after the laptop rebooted. I use a HP though. Still, sometimes it does not hurt to reboot :-).

---

### Post by leogagliardi on 2013-06-18
As I explained before, any of my laptops, running debian 6 (kernels 2.6.x) or ubuntu 12.04 (running kernel 3.x), are mounting my sandisk SDHC Class 10, while win mount the cards on both. My problem came from march 2012 and its mid-2013, many reboots and even kernel updates, but nothing changed...

---

### Post by leogagliardi on 2013-08-01
It was easy. The OS do not have drivers for the internal card reader (as the last line says: Realtek Semiconductor Co., Ltd. Device 5229). Maybe I overestimated Ubuntu expecting the option to install the propietary drivers, as it usually do with some video cards.
Enter [www.Realtek.com](www.Realtek.com), go to the Card Reader drivers:
[http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=15&PFid=25&Level=4&Conn=3&DownTypeID=3&GetDown=false#2](http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=15&PFid=25&Level=4&Conn=3&DownTypeID=3&GetDown=false#2)
mine is 5229, but chose yours
download, unzip, and follow the README instructions  (as root or with sudo configure, make, make install, depmode, reboot)
Keep the folder because you will have to do it again after each kernel upgrade...

---

