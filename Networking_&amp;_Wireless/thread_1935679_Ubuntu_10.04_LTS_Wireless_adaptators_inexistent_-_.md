---
title: "Ubuntu 10.04 LTS Wireless adaptators inexistent - Realtek would be the controller"
date: 2012-03-04
forum: Networking &amp; Wireless
---

### Post by Masanoko on 2012-03-04
Hello, I'm new to the Ubuntu OS and I've been learning a bit about it, however, I've come to an issue recently, probably due to clearing some space in the disk. Upon a reboot of the laptop (it's an OLPC laptop with Ubuntu 10.04 LTS, 8 GB, tried to fix this in their forums, but the only solution was to wipe the disk, but it wouldn't let me wipe it), the wireless connection would function no more. I've tried a lot of fixes (a lot of which I don't even remember anymore, sadly).

Next, the ten steps shown in the help thread:

Machine brand and model:
```
Magalhaes Model MG10T
```Wireless Brand, Model & Wireless Chipset
```
00:00.0 Host bridge: Intel Corporation N10 Family DMI Bridge
00:02.0 VGA compatible controller: Intel Corporation N10 Family Integrated Graphics Controller
00:02.1 Display controller: Intel Corporation N10 Family Integrated Graphics Controller
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation NM10 Family LPC Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation N10/ICH7 Family SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
04:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8172 (rev 10)

-----

Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0bda:0138 Realtek Semiconductor Corp. 
Bus 001 Device 002: ID 5986:02a8 Acer, Inc 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```Interface:
```
eth0      Link encap:Ethernet  direcciónHW 44:87:fc:25:f6:87  
          Direc. inet:192.168.0.102  Difus.:192.168.0.255  Másc:255.255.255.0
          Dirección inet6: fe80::4687:fcff:fe25:f687/64 Alcance:Enlace
          ACTIVO DIFUSIÓN FUNCIONANDO MULTICAST  MTU:1460  Métrica:1
          Paquetes RX:13038 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:11417 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:1000 
          Bytes RX:11896431 (11.8 MB)  TX bytes:1930060 (1.9 MB)
          Interrupción:27 Dirección base: 0x8000 

lo        Link encap:Bucle local  
          Direc. inet:127.0.0.1  Másc:255.0.0.0
          Dirección inet6: ::1/128 Alcance:Anfitrión
          ACTIVO BUCLE FUNCIONANDO  MTU:16436  Métrica:1
          Paquetes RX:48981 errores:0 perdidos:0 overruns:0 frame:0
          Paquetes TX:48981 errores:0 perdidos:0 overruns:0 carrier:0
          colisiones:0 long.colaTX:0 
          Bytes RX:4067117 (4.0 MB)  TX bytes:4067117 (4.0 MB)

---

lo        no wireless extensions.

eth0      no wireless extensions.
```Modules:
```
binfmt_misc             6587  1 
ppdev                   5259  0 
tpm_tis                 7351  1 
tpm                    13484  1 tpm_tis
tpm_bios                5266  1 tpm
snd_hda_codec_realtek   203168  1 
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
joydev                  8708  0 
snd_hda_intel          21877  2 
snd_hda_codec          74201  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70662  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
i915                  282354  2 
uvcvideo               56990  0 
drm_kms_helper         29297  1 i915
rt2870sta             461811  0 
videodev               34361  1 uvcvideo
v4l1_compat            13251  2 uvcvideo,videodev
snd                    54148  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
usb_storage            39425  0 
drm                   162471  3 i915,drm_kms_helper
i2c_algo_bit            5028  1 i915
psmouse                63245  0 
serio_raw               3978  0 
soundcore               6620  1 snd
video                  17375  1 i915
intel_agp              24177  2 i915
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
output                  1871  1 video
agpgart                31724  2 drm,intel_agp
lp                      7028  0 
parport                32635  2 ppdev,lp
ahci                   32008  2 
r8169                  33884  0 
mii                     4381  1 r8169
```Network:
```
  *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 44:87:fc:25:f6:87
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.0.102 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:27 ioport:2000(size=256) memory:f0520000-f0520fff(prefetchable) memory:f0510000-f051ffff(prefetchable) memory:f0540000-f055ffff(prefetchable)
  *-network UNCLAIMED
       description: Network controller
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 10
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: ioport:3000(size=256) memory:f0100000-f0103fff

```Scan:
```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

```Ubuntu version:
```
Description:    Ubuntu 10.04.4 LTS
```This is weird because I was able to connect to any wireless network before, but I just can't anymore, I'm only able to see wired connections in the network icon. How can I fix this? Any help will be greatly appreciated.

---

