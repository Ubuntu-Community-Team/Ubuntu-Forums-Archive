---
title: "HP G62-454EP no detect wireless on LTS 10.04 32bits"
date: 2011-11-01
forum: Networking &amp; Wireless
---

### Post by phpereira on 2011-11-01
Hello!

I've installed ubuntu lLTS10.04 32bits on my HP g62-454EP Laptop, end wireless network no work´s.

I appreciate if anyone can help me.

Thanks.

Paulo

My system.

keise@keise-laptop:~$ sudo lshw -C network
[sudo] password for keise: 
  *-network               
       description: Network controller
       product: RaLink
       vendor: RaLink
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=rt5390 latency=0
       resources: irq:16 memory:d3400000-d340ffff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 98:4b:e1:ad:6b:e3
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.200 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:26 ioport:2000(size=256) memory:d1410000-d1410fff(prefetchable) memory:d1400000-d140ffff(prefetchable) memory:d1420000-d142ffff(prefetchable)
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=RALINK WLAN multicast=yes wireless=Ralink STA

keise@keise-laptop:~$ lspci -nn | grep -e 0280 -e 0200
02:00.0 Network controller [0280]: RaLink Device [1814:5390]
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
keise@keise-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     Ralink STA  
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

keise@keise-laptop:~$ rfkill list all
none

keise@keise-laptop:~$ lsmod
Module                  Size  Used by
snd_hda_codec_intelhdmi     9559  1 
snd_hda_codec_realtek   216061  1 
fbcon                  35102  71 
tileblit                1999  1 fbcon
snd_hda_intel          20799  2 
font                    7557  1 fbcon
snd_hda_codec          87096  3 snd_hda_codec_intelhdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5668  1 snd_hda_codec
snd_pcm_oss            34603  0 
snd_mixer_oss          13929  1 snd_pcm_oss
bitblit                 4707  1 fbcon
snd_pcm                71646  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
softcursor              1189  1 bitblit
snd_seq_dummy           1498  0 
vga16fb                11385  0 
vgastate                8961  1 vga16fb
binfmt_misc             6587  1 
snd_seq_oss            27626  0 
joydev                  8740  0 
snd_seq_midi            4621  0 
snd_rawmidi            19141  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
ppdev                   5259  0 
snd_seq                48042  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              18710  2 snd_pcm,snd_seq
i915                  288963  3 
snd_seq_device          6052  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
drm_kms_helper         29329  1 i915
snd                    56687  19 snd_hda_codec_intelhdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm                   163651  4 i915,drm_kms_helper
intel_agp              24375  2 i915
i2c_algo_bit            5028  1 i915
agpgart                31724  2 drm,intel_agp
uvcvideo               57406  0 
soundcore               6620  1 snd
videodev               34425  1 uvcvideo
psmouse                63677  0 
serio_raw               3978  0 
video                  17375  1 i915
v4l1_compat            13251  2 uvcvideo,videodev
snd_page_alloc          7140  2 snd_hda_intel,snd_pcm
output                  1871  1 video
rt5390sta            1194549  0 
lp                      7028  0 
parport                32635  2 ppdev,lp
usbhid                 36110  0 
usb_storage            39841  0 
hid                    67288  1 usbhid
ahci                   32360  2 
r8169                  34140  0 
mii                     4381  1 r8169

---

