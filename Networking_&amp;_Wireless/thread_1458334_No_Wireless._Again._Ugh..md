---
title: "No Wireless. Again. Ugh."
date: 2010-04-19
forum: Networking &amp; Wireless
---

### Post by SurferGTO on 2010-04-19
Ok this is just getting annoying. Initially my problem was that my laptop would not connect to MY wireless network, for whatever reason. XBOX Live had no problem.  I was using my appartment complex's wireless but that was way too slow so I attempted to have a comcast rep set it up while he was here for the phone the other day.  We now have the xbox live setup no problem on my wireless, secured initially.  I remembered having a problem with my laptop not signing on to secured networks so i made the a/p unsecured. still cant connect to MY network. and now, after having changed NO settings, I cant even sign on to the Appartment wireless network with my laptop, but the xbox still can.  I have no problem finding the network in the WICD network manager, and I can connect to the net via a wired connection on the same laptop, but now i cant go wireless at ALL.

to start: Karmic:
> scott@ubuntu:~$ lshw -C network 
WARNING: you should run this program as super-user.
PCI (sysfs)  
  *-network               
       description: Ethernet interface
       product: MCP67 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:1d:72:48:08:20
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=forcedeth driverversion=0.64 ip=192.168.1.101 latency=0 maxlatency=20 mingnt=1 multicast=yes
       resources: irq:27 memory:fc488000-fc488fff ioport:30f8(size=8) memory:fc489c00-fc489cff memory:fc489800-fc48980f
  *-network
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth1
       version: 01
       serial: 00:1a:73:e3:c2:b8
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.10.91.9 latency=0 multicast=yes wireless=IEEE 802.11
       resources: irq:21 memory:fc000000-fc003fff
scott@ubuntu:~$ lsmod
Module                  Size  Used by
binfmt_misc             8356  1 
ppdev                   6688  0 
snd_hda_codec_conexant    20060  1 
snd_hda_intel          26920  2 
snd_hda_codec          75708  2 snd_hda_codec_conexant,snd_hda_intel
snd_hwdep               7200  1 snd_hda_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           2656  0 
snd_seq_oss            28576  0 
uvcvideo               59080  0 
snd_seq_midi            6464  0 
snd_rawmidi            22176  1 snd_seq_midi
videodev               36736  1 uvcvideo
v4l1_compat            14336  2 uvcvideo,videodev
joydev                 10240  0 
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
k8temp                  4188  0 
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
lib80211_crypt_tkip     8636  0 
psmouse                56500  0 
serio_raw               5280  0 
wl                   1272936  0 
lib80211                6432  2 lib80211_crypt_tkip,wl
sdhci_pci               7100  0 
sdhci                  17504  1 sdhci_pci
led_class               4096  1 sdhci
sbp2                   22888  0 
iptable_filter          3100  0 
ip_tables              11692  1 iptable_filter
x_tables               16544  1 ip_tables
nvidia               9586440  42 
agpgart                34988  1 nvidia
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    59204  16 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               7264  1 snd
snd_page_alloc          9156  2 snd_hda_intel,snd_pcm
i2c_nforce2             6784  0 
lp                      8964  0 
parport                35340  2 ppdev,lp
usbhid                 38208  0 
ohci1394               29900  0 
video                  19380  0 
output                  2780  1 video
ieee1394               86596  2 sbp2,ohci1394
forcedeth              54152  0 
scott@ubuntu:~$ 


---

### Post by SurferGTO on 2010-04-21
Bump - come on gurus I havent been able to fix this yet and I've searched all related topics with zero results

---

### Post by SurferGTO on 2010-04-23
Anyone?

---

