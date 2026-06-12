---
title: "No wireless on lenovo S10-2 / Karmic Koala 9.10 Netbook Remix"
date: 2009-11-08
forum: Networking &amp; Wireless
---

### Post by Claudius1974 on 2009-11-08
All,

I've just installed Karmic Koala 9.10 Netbook remix on my Lenovo S10-2 and the wireless doesn't work. It doesn't appear on Gnome and ifconfig just shows the wired and loopback interface only.

I'm a bit of a newbie with linux so not totally sure where to start. I've run sudo lshw -C network and I get the following output:

```
  *-network               
       description: Network controller
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:17 memory:56100000-56103fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:26:22:07:d7:2d
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.7 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:29 ioport:2000(size=256) memory:52010000-52010fff(prefetchable) memory:52000000-5200ffff(prefetchable) memory:52020000-5203ffff(prefetchable)

```

and looking through dmesg I see the following:

```

[    9.467349] b43-phy0: Broadcom 4312 WLAN found (core revision 15)
[    9.512092] b43-phy0 ERROR: FOUND UNSUPPORTED PHY (Analog 6, Type 5, Revision 1)
[    9.512162] b43: probe of ssb0:0 failed with error -95
[    9.512237] Broadcom 43xx driver loaded [ Features: PL, Firmware-ID: FW13 ]
[    9.652234] type=1505 audit(1257677964.371:11): operation="profile_replace" pid=734 name=/sbin/dhclient3
<snip>
[   10.319736] cfg80211: World regulatory domain updated:
[   10.319744] 	(start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   10.319752] 	(2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.319758] 	(2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   10.319764] 	(2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   10.319770] 	(5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   10.319777] 	(5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)

```

I hope this is enough information to start with. 

Thanks!

---

### Post by Claudius1974 on 2009-11-08
I've spent this afternoon following all the posts on the forums and google without success. Looking at the HOWTO post I've run lsmod and have the following output

```

Module                  Size  Used by
binfmt_misc             8356  1 
snd_hda_codec_realtek   203328  1 
snd_hda_intel          26920  2 
snd_hda_codec          75708  2 snd_hda_codec_realtek,snd_hda_intel
ppdev                   6688  0 
snd_hwdep               7200  1 snd_hda_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           2656  0 
snd_seq_oss            28576  0 
snd_seq_midi            6432  0 
snd_rawmidi            22208  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
joydev                 10272  0 
uvcvideo               59080  0 
b43                   122136  0 
iptable_filter          3100  0 
ip_tables              11692  1 iptable_filter
snd                    59204  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               7264  1 snd
x_tables               16544  1 ip_tables
mac80211              181236  1 b43
snd_page_alloc          9156  2 snd_hda_intel,snd_pcm
lp                      8964  0 
videodev               36736  1 uvcvideo
psmouse                56180  0 
parport                35340  2 ppdev,lp
v4l1_compat            14496  2 uvcvideo,videodev
cfg80211               93052  2 b43,mac80211
serio_raw               5280  0 
led_class               4096  1 b43
fbcon                  36640  72 
tileblit                2460  1 fbcon
font                    8124  1 fbcon
bitblit                 5372  1 fbcon
softcursor              1756  1 bitblit
r8169                  32064  0 
mii                     5212  1 r8169
i915                  221064  3 
drm                   159584  3 i915
i2c_algo_bit            5760  1 i915
intel_agp              27484  2 i915
agpgart                34988  2 drm,intel_agp
video                  19380  1 i915
output                  2780  1 video
ssb                    35300  1 b43

```

---

### Post by CoolDreamZ on 2009-11-11
Hi, I had exactly the same problem, this is a serious bug in 9.10. See this [thread ]("http://ubuntuforums.org/showthread.php?t=1312603")for a solution

---

### Post by Claudius1974 on 2009-11-15
Thanks! I'll work through the thread and report back.

---

### Post by djmaxmalta on 2010-03-29
mine is fixed, and it was easy, so here's the trick


so click administration -> synaptic package manager -> then click origin - restricted (i found it to be the first one in the list if it is not then search broadcom wireless the only one in the list - i reapeat this should work as i found it twice on google, and yahoo hopefully it would work for you guys i am going to try it out with my lenovo s10-2 with a wubi install of ubuntu 9.10 and 9.10 remix

also if you have other findings please do share

---

