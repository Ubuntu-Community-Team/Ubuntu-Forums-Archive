---
title: "Dell XPS 1530 wireless problem"
date: 2010-05-17
forum: Networking &amp; Wireless
---

### Post by hyuecn on 2010-05-17
Dear All,

Like a few other n00bs I am having a problem with my wireless connection. I am using Ubuntu 10.04 installed using Wubi. When I first installed Ubuntu I was able to connect to my wireless network but subsequently my wireless appears to be disabled, indeed when I click on the network icon the wireless is greyed out. Any advice would be much appreciated

My laptop is a Dell XPS 1530

When I enter lspci into terminal I get > 00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation G84 [GeForce 8600M GT] (rev a1)
03:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
03:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
03:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
03:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
03:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
09:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller (rev 12)
0b:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)


When I enter ifconfig into terminal I get > eth0      Link encap:Ethernet  HWaddr 00:1d:09:55:90:8a  
          inet addr:192.168.2.13  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: 2002:520c:4a68:1234:21d:9ff:fe55:908a/64 Scope:Global
          inet6 addr: fe80::21d:9ff:fe55:908a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3167 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1840 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2411816 (2.4 MB)  TX bytes:357145 (357.1 KB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:332 errors:0 dropped:0 overruns:0 frame:0
          TX packets:332 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:25824 (25.8 KB)  TX bytes:25824 (25.8 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1f:3b:d9:c6:11  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


When I enter lsmod > Module                  Size  Used by
nls_utf8                1421  1 
udf                    85529  1 
crc_itu_t               1715  1 udf
fbcon                  39270  71 
tileblit                2487  1 fbcon
font                    8053  1 fbcon
bitblit                 5811  1 fbcon
softcursor              1565  1 bitblit
vga16fb                12757  0 
vgastate                9857  1 vga16fb
rfcomm                 40329  4 
binfmt_misc             7960  1 
sco                     9617  2 
bridge                 53152  0 
stp                     2171  1 bridge
bnep                   11820  2 
l2cap                  34774  16 rfcomm,bnep
ppdev                   6375  0 
joydev                 11072  0 
snd_hda_codec_idt      61418  1 
arc4                    1473  2 
snd_hda_intel          25645  2 
snd_hda_codec          85727  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep               6924  1 snd_hda_codec
snd_pcm_oss            41394  0 
snd_mixer_oss          16299  1 snd_pcm_oss
snd_pcm                87850  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1782  0 
snd_seq_oss            31219  0 
snd_seq_midi            5829  0 
snd_rawmidi            23388  1 snd_seq_midi
snd_seq_midi_event      7267  2 snd_seq_oss,snd_seq_midi
snd_seq                57417  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
iwlagn                121577  0 
dell_wmi                2177  0 
iwlcore               124955  1 iwlagn
nouveau               515131  2 
snd_timer              23553  2 snd_pcm,snd_seq
snd_seq_device          6824  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
dell_laptop             7941  0 
uvcvideo               62403  0 
ttm                    60815  1 nouveau
drm_kms_helper         30742  1 nouveau
usbhid                 40988  0 
mac80211              238128  2 iwlagn,iwlcore
btusb                  12969  2 
video                  20623  0 
hid                    83376  1 usbhid
bluetooth              58621  9 rfcomm,sco,bnep,l2cap,btusb
output                  2503  1 video
videodev               40486  1 uvcvideo
v4l1_compat            15495  2 uvcvideo,videodev
v4l2_compat_ioctl32    12020  1 videodev
dcdbas                  6886  1 dell_laptop
snd                    70978  16 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
sdhci_pci               6700  0 
sdhci                  17928  1 sdhci_pci
ricoh_mmc               3416  0 
led_class               3732  2 iwlcore,sdhci
psmouse                64608  0 
serio_raw               4918  0 
drm                   198770  4 nouveau,ttm,drm_kms_helper
i2c_algo_bit            6024  1 nouveau
cfg80211              148386  3 iwlagn,iwlcore,mac80211
soundcore               8052  1 snd
snd_page_alloc          8500  2 snd_hda_intel,snd_pcm
intel_agp              29225  0 
lp                      9336  0 
parport                37160  2 ppdev,lp
ohci1394               30260  0 
sky2                   48803  0 
ieee1394               94675  1 ohci1394
ahci                   37646  1 


When I enter lshw -C network >       description: Ethernet interface
       product: 88E8040 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 12
       serial: 00:1d:09:55:90:8a
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.25 duplex=full firmware=N/A ip=192.168.2.13 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:29 memory:f1ffc000-f1ffffff ioport:de00(size=256)
  *-network
       description: Wireless interface
       product: PRO/Wireless 4965 AG or AGN [Kedron] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0b:00.0
       logical name: wlan0
       version: 61
       serial: 00:1f:3b:d9:c6:11
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:30 memory:f1efe000-f1efffff


the kernel architecture is 2.6.32-21-generic x86_64

If any more info is needed I'll do my best to assist

Thanks

I did an update, and the wireless worked. I also installed wicd. However it connect for a few minutes, and indicated it was still working but I had no internet access. I tried turning my wireless off and turning it back on, but it wasn't able to detect any wireless networks at all.

---

