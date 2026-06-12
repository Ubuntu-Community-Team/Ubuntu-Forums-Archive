---
title: "B43 Driver not displaying"
date: 2011-06-25
forum: Networking &amp; Wireless
---

### Post by DarkAvneger1337 on 2011-06-25
In the past, I've remove the STA driver that doesnt work in favor of the b43 driver.

However, after the normal route of installing b43-fwcutter failed to display any setup, I manually installed the firmware using the offline method. However, when I open 'additional drivers' the only driver I see is STA. I have tried using the firmware-b43-installer (nothing happened) and the lpphy alternative (failed to install)

help?

---

### Post by Bucky Ball on 2011-06-25
You have access to internet cable and have gotten updates then checked additional drivers with cable plugged in? May seem like silly question but just in case ...

---

### Post by DarkAvneger1337 on 2011-06-25
Yes I have updated, Im tethering from my android via usb.

---

### Post by josephmills on 2011-06-25
open you termianl and type in  ```
lspci -nn
``` and ```
 lsmod 
``` and ```
 rfkill list all 
``` then paste here

---

### Post by nm_geo on 2011-06-25
> **DarkAvneger1337 said:**
> In the past, I've remove the STA driver that doesnt work in favor of the b43 driver.

However, after the normal route of installing b43-fwcutter failed to display any setup, I manually installed the firmware using the offline method. However, when I open 'additional drivers' the only driver I see is STA. I have tried using the firmware-b43-installer (nothing happened) and the lpphy alternative (failed to install)

help?

I have to tell you .. I have flavors Lucid, Maverick, Natty & Oneiric running on this laptop.  The only ones I can see the b43 driver in Additional Driver are Lucid and Maverick, but I run all Lucid, Natty and Oneiric with the b43 driver.  Maverick at present is on the STA driver just for testing purposes.

Natty and the STA driver has been a huge problem.. 
Now if you will give the results of 
 Hi Joseph LOL I will just watch..

---

### Post by DarkAvneger1337 on 2011-06-25
####@####-Latitude-D620:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub [8086:27a0] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller [8086:27a2] (rev 03)
00:02.1 Display controller [0380]: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller [8086:27a6] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation N10/ICH 7 Family High Definition Audio Controller [8086:27d8] (rev 01)
00:1c.0 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 1 [8086:27d0] (rev 01)
00:1c.1 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 2 [8086:27d2] (rev 01)
00:1c.2 PCI bridge [0604]: Intel Corporation N10/ICH 7 Family PCI Express Port 3 [8086:27d4] (rev 01)
00:1d.0 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 [8086:27c8] (rev 01)
00:1d.1 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 [8086:27c9] (rev 01)
00:1d.2 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 [8086:27ca] (rev 01)
00:1d.3 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 [8086:27cb] (rev 01)
00:1d.7 USB Controller [0c03]: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller [8086:27cc] (rev 01)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev e1)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge [8086:27b9] (rev 01)
00:1f.2 IDE interface [0101]: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller [8086:27c4] (rev 01)
00:1f.3 SMBus [0c05]: Intel Corporation N10/ICH 7 Family SMBus Controller [8086:27da] (rev 01)
03:01.0 CardBus bridge [0607]: O2 Micro, Inc. OZ601/6912/711E0 CardBus/SmartCardBus Controller [1217:6972] (rev 40)
09:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5752 Gigabit Ethernet PCI Express [14e4:1600] (rev 02)
0c:00.0 Network controller [0280]: Broadcom Corporation BCM4311 802.11a/b/g [14e4:4312] (rev 01)
####@####-Latitude-D620:~$ lsmod
Module                  Size  Used by
parport_pc             32111  0 
ppdev                  12849  0 
snd_hda_codec_idt      60537  1 
arc4                   12473  2 
binfmt_misc            13213  1 
b43                   296610  0 
joydev                 17322  0 
snd_hda_intel          24140  2 
snd_hda_codec          90901  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80244  2 snd_hda_intel,snd_hda_codec
i915                  450944  3 
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
drm_kms_helper         40745  1 i915
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
mac80211              257001  1 b43
dell_wmi               12601  0 
dell_laptop            13515  0 
dcdbas                 14054  1 dell_laptop
pcmcia                 39671  0 
sparse_keymap          13666  1 dell_wmi
snd_timer              28659  2 snd_pcm,snd_seq
drm                   180037  4 i915,drm_kms_helper
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
cdc_acm                22150  0 
psmouse                73312  0 
yenta_socket           27230  0 
snd                    55295  13 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
pcmcia_rsrc            18292  1 yenta_socket
serio_raw              12990  0 
cfg80211              156212  2 b43,mac80211
pcmcia_core            21505  3 pcmcia,yenta_socket,pcmcia_rsrc
i2c_algo_bit           13184  1 i915
soundcore              12600  1 snd
video                  18951  1 i915
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
usb_storage            43946  0 
uas                    17676  0 
tg3                   131476  0 
ssb                    45942  1 b43
####@####-Latitude-D620:~$ rfkill list all
0: dell-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

---

### Post by nm_geo on 2011-06-25
Run this too please
```

dmesg | egrep 'ound|irmware|eth|ath|wl|ipw|b43|witch|ndiswrapper'
```and ```
sudo lshw -C network
```

---

### Post by DarkAvneger1337 on 2011-06-25
####@####-Latitude-D620:~$ dmesg | egrep 'ound|irmware|eth|ath|wl|ipw|b43|witch|ndiswrapper'
[    0.270850] ACPI: ACPI Dock Station Driver: 2 docks/bays found
[    0.270855] HEST: Table not found.
[    0.308213] Switching to clocksource hpet
[    0.311307] Switched to NOHz mode on CPU #0
[    0.311440] Switched to NOHz mode on CPU #1
[    0.348808] pnp: PnP ACPI: found 13 devices
[    0.404309] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input0
[    0.472039] ACPI: Lid Switch [LID]
[    0.577653] ERST: Table is not found!
[    0.931817] isapnp: No Plug & Play device found
[    0.984073] i2c-core: driver [adp5520] using legacy suspend method
[    0.984075] i2c-core: driver [adp5520] using legacy resume method
[    0.987026] ehci_hcd 0000:00:1d.7: using broken periodic workaround
[    1.004196] hub 1-0:1.0: USB hub found
[    1.004611] hub 2-0:1.0: USB hub found
[    1.004969] hub 3-0:1.0: USB hub found
[    1.008214] hub 4-0:1.0: USB hub found
[    1.008562] hub 5-0:1.0: USB hub found
[    1.012443] device-mapper: multipath: version 1.2.0 loaded
[    1.012446] device-mapper: multipath round-robin: version 1.0.0 loaded
[    1.015656] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.357709] b43-pci-bridge 0000:0c:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.357721] b43-pci-bridge 0000:0c:00.0: setting latency timer to 64
[    1.376156] ssb: Core 0 found: ChipCommon (cc 0x800, rev 0x11, vendor 0x4243)
[    1.376172] ssb: Core 1 found: IEEE 802.11 (cc 0x812, rev 0x0A, vendor 0x4243)
[    1.376181] ssb: Core 2 found: USB 1.1 Host (cc 0x817, rev 0x03, vendor 0x4243)
[    1.376191] ssb: Core 3 found: PCI-E (cc 0x820, rev 0x01, vendor 0x4243)
[    1.420167] ssb: Sonics Silicon Backplane found on PCI device 0000:0c:00.0
[    1.424404] tg3 0000:09:00.0: eth0: Tigon3 [partno(BCM5752KFBG) rev 6002] (PCI Express) MAC address 00:15:c5:46:8a:9e
[    1.424410] tg3 0000:09:00.0: eth0: attached PHY is 5752 (10/100/1000Base-T Ethernet) (WireSpeed[1])
[    1.424414] tg3 0000:09:00.0: eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] TSOcap[1]
[    1.424417] tg3 0000:09:00.0: eth0: dma_rwctrl[76180000] dma_mask[64-bit]
[    1.456838] hub 1-2:1.0: USB hub found
[    1.880961] hub 1-2.3:1.0: USB hub found
[   14.602175] lp: driver loaded but no devices found
[   14.652332] [Firmware Bug]: Duplicate ACPI video bus devices for the same VGA controller, please try module parameter "video.allow_duplicates=1"if the current driver doesn't work.
[   14.734301] leds_ss4200: no LED devices found
[   14.940214] yenta_cardbus 0000:03:01.0: CardBus bridge found [1028:01c2]
[   15.280293] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   15.734463] b43-phy0: Broadcom 4311 WLAN found (core revision 10)
[   15.865606] Registered led device: b43-phy0::tx
[   15.865693] Registered led device: b43-phy0::rx
[   15.865774] Registered led device: b43-phy0::radio
[   15.865802] Broadcom 43xx driver loaded [ Features: PNL, Firmware-ID: FW13 ]
[   16.056738] Console: switching to colour frame buffer device 180x56
[   16.173175] input: HDA Intel Mic at Ext Left Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
[   16.173450] input: HDA Intel HP Out at Ext Left Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[   16.512079] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[   16.604764] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   16.889477] tg3 0000:09:00.0: eth0: Link is up at 100 Mbps, full duplex
[   16.889482] tg3 0000:09:00.0: eth0: Flow control is off for TX and off for RX
[   16.889657] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   27.484046] eth0: no IPv6 routers present
[   96.144038] easytether0: no IPv6 routers present
####@####-Latitude-D620:~$ sudo lshw -C network
[sudo] password for ####: 
  *-network               
       description: Network controller
       product: BCM4311 802.11a/b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:17 memory:efdfc000-efdfffff
  *-network
       description: Ethernet interface
       product: NetXtreme BCM5752 Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 02
       serial: 00:15:c5:46:8a:9e
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.116 duplex=full firmware=5752-v3.19 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:43 memory:efcf0000-efcfffff
  *-network:0
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:16:cf:29:71:22
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=2.6.38-8-generic firmware=410.2160 link=no multicast=yes wireless=IEEE 802.11bg
  *-network:1
       description: Ethernet interface
       physical id: 2
       logical name: easytether0
       serial: 02:00:54:74:68:72
       size: 10Mbit/s
       capabilities: ethernet physical
       configuration: autonegotiation=off broadcast=yes driver=tun driverversion=1.6 duplex=full firmware=N/A ip=192.168.117.2 link=yes multicast=yes port=twisted pair speed=10Mbit/s

---

### Post by nm_geo on 2011-06-25
Wow we are running the same laptop..

```
uname -a
``````
cat /etc/lsb-release
```Just wondering what we are working with!

---

### Post by DarkAvneger1337 on 2011-06-25
####@####-Latitude-D620:~$ uname -a
Linux ####-Latitude-D620 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 i686 i686 i386 GNU/Linux
####@####-Latitude-D620:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.04
DISTRIB_CODENAME=natty
DISTRIB_DESCRIPTION="Ubuntu 11.04"

---

### Post by nm_geo on 2011-06-25
> **DarkAvneger1337 said:**
> ####@####-Latitude-D620:~$ uname -a
Linux ####-Latitude-D620 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 i686 i686 i386 GNU/Linux
####@####-Latitude-D620:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.04
DISTRIB_CODENAME=natty
DISTRIB_DESCRIPTION="Ubuntu 11.04"

Ok I see our firmwares have different dates mine is newer.
Have you updated and upgraded the Natty yet?
we may need to 
```
sudo apt-get update
``````
sudo apt-get upgrade
```then re-install the correct firmware maybe not.. we will see

---

### Post by nm_geo on 2011-06-25
Mia copa.. 
I was looking at my Oneiric install ... Sorry

Have you tried to boot without your ethernet connection?

It looks like you have the right driver and the right firmware?

---

### Post by DarkAvneger1337 on 2011-06-25
seems like its mostly working(after checking network manager) but still doesnt show up in 'additional drivers'

strange

---

### Post by nm_geo on 2011-06-25
> **DarkAvneger1337 said:**
> seems like its mostly working(after checking network manager) but still doesnt show up in 'additional drivers'

strange

Yeah that was what I thought as well.  It does not show up in my Additional Drivers either even after installing and it working just fine... Not in Natty or Oneiric (which I am testing)... Glad it works.. Later

---

### Post by josephmills on 2011-06-25
> **nm_geo said:**
> Yeah that was what I thought as well.  It does not show up in my Additional Drivers either even after installing and it working just fine... Not in Natty or Oneiric (which I am testing)... Glad it works.. Later
I think that the jockey is on the horse the wrong way . what I mean by that is jockey controls additional drivers . its a joke not aimed at anyone please do not take it that way

---

