---
title: "How to hw unblock Intel Wireless 5300 AGN, Ubuntu 9.10, 2.6.32.2 x64 no HW switch"
date: 2010-01-09
forum: Networking &amp; Wireless
---

### Post by pacsy on 2010-01-09
Hello Everyone. Can somebody help me to activate my wireless card. I tried a lots of things described on the net but I had no success so far.
 The laptop is: mySN XMG7.c (Clevo M570TU)
 No bios switch is available for wireless lan
 No hw switch button is available.
 Only way to switch it on is Fn+F11 but this does not generate any keycode or acpid event.

I cannot find any rfkill file under /sys or /proc. Maybe if I get that there than I can enable is as it is suggested on the net. Does anyone how to get rfkill file installed?

Thank you in advance for your help.

 Additional info:
Linux 2.6.32.2-custom #1 SMP Wed Jan 6 12:28:01 CET 2010 x86_64 

GNU/Linux
  *-network DISABLED      
       description: Wireless interface
       product: PRO/Wireless 5300 AGN [Shiloh] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 00
       serial: 00:21:6a:79:4a:7a
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:37 memory:a0000000-a0001fff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 03
       serial: 00:90:f5:94:d9:24
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.178.27 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:36 ioport:6000(size=256) memory:cfdff000-cfdfffff(prefetchable) memory:c8000000-c8003fff(prefetchable) memory:c8020000-c803ffff(prefetchable)

0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes


Module                  Size  Used by
binfmt_misc             7454  1 
ppdev                   6059  0 
snd_hda_codec_si3054     4124  1 
snd_hda_codec_realtek   273242  1 
snd_hda_intel          23641  2 
snd_hda_codec          79633  3 snd_hda_codec_si3054,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               6606  1 snd_hda_codec
snd_pcm_oss            39645  0 
snd_mixer_oss          16456  1 snd_pcm_oss
snd_pcm                84013  4 snd_hda_codec_si3054,snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1734  0 
snd_seq_oss            29511  0 
snd_seq_midi            5669  0 
snd_rawmidi            22557  1 snd_seq_midi
snd_seq_midi_event      6931  2 snd_seq_oss,snd_seq_midi
arc4                    1425  2 
snd_seq                54478  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
iwlagn                111656  0 
iwlcore               121210  1 iwlagn
snd_timer              22574  2 snd_pcm,snd_seq
iptable_filter          2679  0 
snd_seq_device          6450  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
sdhci_pci               6446  0 
ip_tables              17486  1 iptable_filter
mac80211              185372  2 iwlagn,iwlcore
snd                    68465  17 snd_hda_codec_si3054,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
uvcvideo               60826  0 
sdhci                  17024  1 sdhci_pci
videodev               39814  1 uvcvideo
soundcore               7860  1 snd
lp                      9112  0 
x_tables               21645  1 ip_tables
jmb38x_ms               8484  0 
led_class               3556  2 iwlcore,sdhci
psmouse                52687  0 
v4l1_compat            15537  2 uvcvideo,videodev
snd_page_alloc          8388  2 snd_hda_intel,snd_pcm
cfg80211              140103  3 iwlagn,iwlcore,mac80211
parport                36303  2 ppdev,lp
v4l2_compat_ioctl32    11252  1 videodev
memstick                9367  1 jmb38x_ms
serio_raw               4672  0 
nvidia              10309788  38 
usbhid                 39208  0 
video                  19498  0 
output                  2391  1 video
ohci1394               29447  0 
r8169                  38401  0 
mii                     5125  1 r8169
ieee1394               89948  1 ohci1394

---

### Post by MrSatchmoo on 2010-02-01
Hi pacsy,

I'm wondering whether you had any success in activating your cart? I think I have the same problem and couldn't find any help here so far. Tried to get some help from mysn, but they just told me to install windows (great help!!!). :-(

---

### Post by MrSatchmoo on 2010-02-12
Solved it!! was pretty easy in the end, but I had to search way too long. I just installed the package linux-backports-modules-karmic and everything works fine now :P

---

