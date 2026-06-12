---
title: "No sound, jumpy video."
date: 2008-04-12
forum: Multimedia &amp; Video
---

### Post by skeetwood-mac on 2008-04-12
I finally got my mouse working properly. And I was going to startfiguring out the video card driver.Then I booted up today and the sound was  gone?!?!? Whats that all about. I've heard ubuntu is supposed to be  so easy your  grandma  can use it. Well this has been harder than anything I've done with windows.

---

### Post by jameswillmer on 2008-04-12
please can you post results of 

> lspci 

and

> lshw -short

---

### Post by skeetwood-mac on 2008-04-12
ok the sound is back. I booted in windows and turned the volume up and its fine now. But the video is still not right. When you try to play a movie full screen its all jumpy. And when you drag a window around fast it makes a trail. My video card is a radeon all in wonder 7500.

heres the result for lspci

> 00:00.0 Host bridge: VIA Technologies, Inc. VT8377 [KT400/KT600 AGP] Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8235 PCI Bridge
00:0a.0 FireWire (IEEE 1394): NEC Corporation IEEE 1394 Host Controller (rev 01)
00:0d.0 Multimedia audio controller: Rockwell International Riptide PCI Audio Controller
00:0d.1 Communication controller: Rockwell International Riptide HCF 56k PCI Modem
00:0d.2 Input device controller: Rockwell International Riptide PCI Game Controller
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV200 QW [Radeon 7500]


and lshw-short

> H/W path             Device     Class          Description
==========================================================
                                system         System Name
/0                              bus            A7V8X-X
/0/0                            memory         64KB BIOS
/0/4                            processor      AMD Athlon(TM) XP 2600+
/0/4/9                          memory         128KB L1 cache
/0/4/a                          memory         512KB L2 cache
/0/28                           memory         512MB System Memory
/0/28/0                         memory         512MB DIMM DRAM Synchronous
/0/28/1                         memory         DIMM DRAM Synchronous [empty]
/0/28/2                         memory         DIMM DRAM Synchronous [empty]
/0/100                          bridge         VT8377 [KT400/KT600 AGP] Host Bri
/0/100/1                        bridge         VT8235 PCI Bridge
/0/100/1/0                      display        Radeon RV200 QW [Radeon 7500]
/0/100/a                        bus            IEEE 1394 Host Controller
/0/100/d                        multimedia     Riptide PCI Audio Controller
/0/100/d.1                      communication  Riptide HCF 56k PCI Modem
/0/100/d.2                      input          Riptide PCI Game Controller
/0/100/10                       bus            VT82xxxxx UHCI USB 1.1 Controller
/0/100/10.1                     bus            VT82xxxxx UHCI USB 1.1 Controller
/0/100/10.2                     bus            VT82xxxxx UHCI USB 1.1 Controller
/0/100/10.3                     bus            USB 2.0
/0/100/11                       bridge         VT8235 ISA Bridge
/0/100/11.1                     storage        VT82C586A/B/VT82C686/A/B/VT823x/A
/0/100/11.1/0        ide0       bus            IDE Channel 0
/0/100/11.1/0/0      /dev/hda   disk           74GB SAMSUNG SP0802N
/0/100/11.1/0/0/1    /dev/hda1  volume         56GB HPFS/NTFS partition
/0/100/11.1/0/0/2    /dev/hda2  volume         16GB HPFS/NTFS partition
/0/100/11.1/0/0/3    /dev/hda3  volume         768MB Extended partition
/0/100/11.1/0/0/3/5  /dev/hda5  volume         768MB Linux swap / Solaris partit
/0/100/11.1/0/1      /dev/hdb   disk           19GB MAXTOR 4K020H1
/0/100/11.1/0/1/1    /dev/hdb1  volume         18GB Linux filesystem partition
/0/100/11.1/0/1/2    /dev/hdb2  volume         855MB Extended partition
/0/100/11.1/0/1/2/5  /dev/hdb5  volume         854MB Linux swap / Solaris partit
/0/100/11.1/1        ide1       bus            IDE Channel 1
/0/100/11.1/1/0      /dev/hdc   disk           LITE-ON LTR-52327S
/0/100/11.5                     multimedia     VT8233/A/8235/8237 AC97 Audio Con
/0/100/12            eth0       network        VT6102 [Rhine-II]


none of that really means anything to me

---

