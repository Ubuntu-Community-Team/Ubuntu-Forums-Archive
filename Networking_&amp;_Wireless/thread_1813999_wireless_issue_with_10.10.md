---
title: "wireless issue with 10.10"
date: 2011-07-28
forum: Networking &amp; Wireless
---

### Post by Fshamri on 2011-07-28
I have installed Ubuntu ver. 10.10 but the wireless icon on the top is disabled.
the kernel have is:**2.6.35-22-generic i686**.
i tried to connect my wireless router as wired with no luck,i want to download the required files from windows and then install it on Ubuntu but i don't know the files reqiured

the **_ipconfig_** output is:
[COLOR="DimGray"]eth0      Link encap:Ethernet  HWaddr 00:23:8b:6d:dc:c4  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:46 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:108 errors:0 dropped:0 overruns:0 frame:0
          TX packets:108 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 

the output of*** iwconfig is***;
[COLOR="rgb(105, 105, 105)"][COLOR="rgb(105, 105, 105)"]wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

          RX bytes:8304 (8.3 KB)  TX bytes:8304 (8.3 KB)
[/COLOR]

**_lsmod:_**
[COLOR="rgb(105, 105, 105)"]
Module                  Size  Used by
nls_utf8                1069  1 
isofs                  30022  1 
parport_pc             26058  0 
ppdev                   5556  0 
binfmt_misc             6599  1 
snd_hda_codec_intelhdmi     9812  1 
snd_hda_codec_idt      54887  1 
arc4                    1165  2 
snd_hda_intel          22107  2 
snd_hda_codec          87552  3 snd_hda_codec_intelhdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep               5040  1 snd_hda_codec
snd_pcm                71475  2 snd_hda_intel,snd_hda_codec
snd_seq_midi            4588  0 
snd_rawmidi            17783  1 snd_seq_midi
i915                  290938  3 
joydev                  8735  0 
snd_seq_midi_event      6047  1 snd_seq_midi
b43                   168681  0 
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
drm_kms_helper         30200  1 i915
mac80211              231541  1 b43
snd_timer              19067  2 snd_pcm,snd_seq
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
uvcvideo               55847  0 
lirc_ene0100            6835  0 
drm                   168054  4 i915,drm_kms_helper
hp_wmi                  5191  0 
videodev               43098  1 uvcvideo
cfg80211              144470  2 b43,mac80211
v4l1_compat            13359  2 uvcvideo,videodev
lirc_dev                9393  1 lirc_ene0100
hp_accel               12532  0 
lis3lv02d               8524  1 hp_accel
input_polldev           3491  1 lis3lv02d
intel_agp              26360  2 i915
psmouse                59033  0 
i2c_algo_bit            5168  1 i915
snd                    49006  13 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
video                  18712  1 i915
led_class               2633  2 b43,hp_accel
serio_raw               4022  0 
output                  1883  1 video
agpgart                32011  2 drm,intel_agp
soundcore                880  1 snd
snd_page_alloc          7120  2 snd_hda_intel,snd_pcm
lp                      7342  0 
parport                31492  3 parport_pc,ppdev,lp
usb_storage            40172  0 
ahci                   19013  0 
r8169                  36489  0 
ssb                    39288  1 b43
mii                     4425  1 r8169
libahci                21667  4 ahci
[/COLOR]

**_Network:_**
[COLOR="rgb(105, 105, 105)"]
  *-network
       description: Network controller
       product: BCM4312 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:16 memory:db600000-db603fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:23:8b:6d:dc:c4
       size: 10MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:46 ioport:6000(size=256) memory:d1410000-d1410fff memory:d1400000-d140ffff memory:d1420000-d142ffff
  *-network DISABLED
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:21:00:aa:78:98
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=2.6.35-22-generic firmware=N/A link=yes multicast=yes wireless=IEEE 802.11bg
[/COLOR]

---

### Post by wildmanne39 on 2011-07-28
Hi, it looks like you have the wrong driver installed.

You do not have internet with a wired connection? If you do not then you can use this link to install the drivers for your 4312 wireless card.

Just make sure you do not install bcmwl-kerrnel-source.
[http://ubuntuforums.org/showpost.php?p=10796508&postcount=44](http://ubuntuforums.org/showpost.php?p=10796508&postcount=44)
Thank you

---

### Post by Fshamri on 2011-07-28
how can in uninstall this wrong driver?
Thanks for help

---

### Post by wildmanne39 on 2011-07-28
Hi, open synaptic and type bcm in the search box then you will see broadcom drivers the ones that have a little green box are installed click on them on remove.

Do you have a wired connection?

---

