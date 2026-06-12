---
title: "Wireless suddenly stopped working Toshiba A505"
date: 2011-03-07
forum: Networking &amp; Wireless
---

### Post by gloria0227 on 2011-03-07
Hello,

Today my wireless suddenly stopped working on me.  The software center does not report any updates being installed around the time it stopped working.  Wireless card is switched on (physically) on the computer but Ubuntu is not seeing the card.

lspci:
```
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.3 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 4 (rev 05)
00:1c.4 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 (rev 05)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
02:00.0 SD Host controller: Ricoh Co Ltd Device e822 (rev 01)
02:00.1 System peripheral: Ricoh Co Ltd Device e230 (rev 01)
02:00.2 System peripheral: Ricoh Co Ltd Device e852 (rev 01)
3f:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
3f:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
3f:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
3f:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
3f:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
3f:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)

```iwconfig wlan0:
```
wlan0     No such device

```I am running Ubuntu 10.10 on a Toshiba Satellite A505-S6005.  I have tried kernels 2.6.35-23, 2.6.35-25, and 2.6.35-27.

How can I begin to figure out why my wireless card is suddenly not working?

Thank you for your help

========================================

ifconfig:
```
eth0      Link encap:Ethernet  HWaddr 00:26:6c:45:58:f1  
          inet addr:192.168.1.5  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::226:6cff:fe45:58f1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:39248 errors:0 dropped:0 overruns:0 frame:0
          TX packets:26175 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:52299064 (52.2 MB)  TX bytes:2808922 (2.8 MB)
          Interrupt:43 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:268 errors:0 dropped:0 overruns:0 frame:0
          TX packets:268 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:20064 (20.0 KB)  TX bytes:20064 (20.0 KB)

```lsmod:
```
Module                  Size  Used by
cryptd                  8140  0 
aes_x86_64              7936  659 
aes_generic            27631  1 aes_x86_64
binfmt_misc             7984  1 
parport_pc             30086  0 
ppdev                   6804  0 
dm_crypt               13381  0 
joydev                 11395  0 
snd_hda_codec_intelhdmi    11032  1 
snd_hda_codec_realtek   300173  1 
snd_hda_intel          26147  2 
snd_hda_codec         100951  3 snd_hda_codec_intelhdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               6660  1 snd_hda_codec
snd_pcm                89104  2 snd_hda_intel,snd_hda_codec
snd_seq_midi            5932  0 
snd_rawmidi            22207  1 snd_seq_midi
snd_seq_midi_event      7291  1 snd_seq_midi
snd_seq                57512  2 snd_seq_midi,snd_seq_midi_event
snd_timer              23850  2 snd_pcm,snd_seq
psmouse                62080  0 
snd_seq_device          6912  3 snd_seq_midi,snd_rawmidi,snd_seq
serio_raw               4910  0 
snd                    64181  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               1240  1 snd
snd_page_alloc          8588  2 snd_hda_intel,snd_pcm
uvcvideo               62379  0 
videodev               49359  1 uvcvideo
v4l1_compat            15519  2 uvcvideo,videodev
v4l2_compat_ioctl32    12614  1 videodev
intel_ips              13252  0 
lp                     10201  0 
parport                37032  3 parport_pc,ppdev,lp
i915                  334721  10 
drm_kms_helper         32836  1 i915
drm                   206198  5 i915,drm_kms_helper
ahci                   22210  3 
sdhci_pci               7765  0 
sdhci                  18400  1 sdhci_pci
led_class               3393  1 sdhci
libahci                26148  1 ahci
i2c_algo_bit            6208  1 i915
r8169                  42254  0 
mii                     5261  1 r8169
video                  22176  1 i915
output                  2527  1 video
intel_agp              32334  2 i915

```sudo lshw -C network:
```
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eth0
       version: 02
       serial: 00:26:6c:45:58:f1
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.5 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:43 ioport:3000(size=256) memory:d0410000-d0410fff memory:d0400000-d040ffff memory:d0420000-d043ffff
```

---

### Post by Nawar99 on 2011-03-07
**Hi**
 
**gloria0227**
 
**i have the same problem in ubuntu**
 
**and in windows 7**
 
**but in windows disable the driver then enable it**
 
**and will it work :) i do it every time i start up my laptop :(**
 
**sorry for my english **

---

### Post by Nawar99 on 2011-03-07
try this

system > administration > additional driver

then choose the driver for wireless and activate it 

like in the picture 

[IMG]http://store3.up-00.com/Mar11/N2I55517.png[/IMG]

---

### Post by ndstate on 2011-03-14
I have heard of this issue for A505 laptops.  Try updating your bios.  Go to thosiba's website and you should be able to find a link to update your bios and this should resolve your issue.

---

