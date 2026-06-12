---
title: "Intel Centrino 6230 woes"
date: 2012-08-29
forum: Networking &amp; Wireless
---

### Post by Westcoastchemist on 2012-08-29
Have done as many fixes of the net as I can find but still can't get my Intel 6230 claimed.  Help please.  Here are some hopefully helpful outputs from my setup.

Best wishes,
Dale

```
sudo lshw -c network
  *-network               
       description: Ethernet interface
       product: JMC250 PCI Express Gigabit Ethernet Controller
       vendor: JMicron Technology Corp.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 05
       serial: 00:90:f5:c4:26:d4
       size: 1GB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm pciexpress msix msi bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=jme driverversion=1.0.5 duplex=full ip=10.77.4.132 latency=0 link=yes multicast=yes port=MII speed=1GB/s
       resources: irq:30 memory:f6320000-f6323fff ioport:d100(size=128) ioport:d000(size=256) memory:f6310000-f631ffff memory:f6300000-f630ffff(prefetchable)
  *-network UNCLAIMED
       description: Network controller
       product: Centrino Advanced-N 6230
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 34
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:f6200000-f6201fff
sudo modprobe iwlagn

dmesg | grep iwl
[   65.047038] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[   65.047040] iwlagn: Copyright(c) 2003-2010 Intel Corporation

cat /etc/lsb-release; uname -a

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.4 LTS"
Linux ubuntu 2.6.32-42-generic #95-Ubuntu SMP Wed Jul 25 15:56:09 UTC 2012 x86_64 GNU/Linux

lspci -nnk | grep -iA2 net

03:00.0 Ethernet controller [0200]: JMicron Technology Corp. JMC250 PCI Express Gigabit Ethernet Controller [197b:0250] (rev 05)
    Kernel driver in use: jme
    Kernel modules: jme
--
04:00.0 Network controller [0280]: Intel Corporation Centrino Advanced-N 6230 [8086:0091] (rev 34)
05:00.0 FireWire (IEEE 1394) [0c00]: JMicron Technology Corp. IEEE 1394 Host Controller [197b:2380] (rev 30)
    Kernel driver in use: ohci1394

iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

lsmod

Module                  Size  Used by
hidp                   14359  0 
hid                    83888  1 hidp
rfcomm                 39594  4 
sco                     9551  2 
bridge                 53280  0 
stp                     2171  1 bridge
bnep                   11655  2 
l2cap                  35315  17 hidp,rfcomm,bnep
btusb                  12969  2 
bluetooth              59384  10 hidp,rfcomm,sco,bnep,l2cap,btusb
binfmt_misc             7960  1 
ppdev                   6375  0 
fbcon                  39270  71 
tileblit                2487  1 fbcon
font                    8053  1 fbcon
bitblit                 5811  1 fbcon
softcursor              1565  1 bitblit
joydev                 11104  0 
nvidia              11234557  42 
snd_hda_codec_realtek   279104  0 
vga16fb                12757  1 
vgastate                9857  1 vga16fb
snd_hda_intel          25805  2 
snd_hda_codec          85791  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               6924  1 snd_hda_codec
snd_pcm_oss            41394  0 
snd_mixer_oss          16299  1 snd_pcm_oss
snd_pcm                87946  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1782  0 
snd_seq_oss            31191  0 
snd_seq_midi            5829  0 
snd_rawmidi            23420  1 snd_seq_midi
snd_seq_midi_event      7267  2 snd_seq_oss,snd_seq_midi
snd_seq                57481  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23681  2 snd_pcm,snd_seq
snd_seq_device          6888  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    71283  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
nouveau               515227  0 
soundcore               8052  1 snd
ttm                    61039  1 nouveau
sdhci_pci               6700  0 
drm_kms_helper         30742  1 nouveau
sdhci                  17960  1 sdhci_pci
snd_page_alloc          8500  2 snd_hda_intel,snd_pcm
video                  20623  0 
drm                   200448  3 nouveau,ttm,drm_kms_helper
led_class               3764  1 sdhci
output                  2503  1 video
psmouse                65040  0 
i2c_algo_bit            6024  1 nouveau
xhci                   43105  0 
serio_raw               4918  0 
uvcvideo               62915  0 
videodev               40614  1 uvcvideo
jme                    31557  0 
lp                      9336  0 
v4l1_compat            15495  2 uvcvideo,videodev
mii                     5237  1 jme
v4l2_compat_ioctl32    11892  1 videodev
parport                37160  2 ppdev,lp
ohci1394               30260  0 
ahci                   38350  1 
ieee1394               94771  1 ohci1394

```

---

