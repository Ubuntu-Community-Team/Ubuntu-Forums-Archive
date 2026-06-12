---
title: "Problems with b43-lpphy drivers"
date: 2011-02-08
forum: Networking &amp; Wireless
---

### Post by eZtaR on 2011-02-08
After struggling to get wifi on my Packard Bell Dot S, I finally found that the solution seemed to be uninstalling the firmware-b43-installer package and replacing it with the firmware-b43-lpphy-installer. But after it working for a short while, I rebooted and it hasn't worked since :(

How do i get it working again?

```
eztar@ezonthenet:~$ lspci -nn | grep Network
01:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
```

```
eztar@ezonthenet:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:26:22:72:cb:c7  
          inet addr:192.168.1.115  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::226:22ff:fe72:cbc7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4133 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1503 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:5423296 (5.4 MB)  TX bytes:209555 (209.5 KB)
          Interrupt:45 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:180 errors:0 dropped:0 overruns:0 frame:0
          TX packets:180 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:13832 (13.8 KB)  TX bytes:13832 (13.8 KB)
```

```
eztar@ezonthenet:~$ lsmod
Module                  Size  Used by
parport_pc             26058  0 
ppdev                   5556  0 
snd_hda_codec_realtek   218492  1 
binfmt_misc             6599  1 
joydev                  8767  0 
snd_hda_intel          22203  2 
snd_hda_codec          87552  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5040  1 snd_hda_codec
snd_pcm                71475  2 snd_hda_intel,snd_hda_codec
i915                  295243  4 
snd_seq_midi            4588  0 
snd_rawmidi            17783  1 snd_seq_midi
drm_kms_helper         30200  1 i915
snd_seq_midi_event      6047  1 snd_seq_midi
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
snd_timer              19067  2 snd_pcm,snd_seq
drm                   168092  4 i915,drm_kms_helper
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
uvcvideo               55847  0 
intel_agp              26566  2 i915
videodev               43098  1 uvcvideo
snd                    49038  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                59033  0 
v4l1_compat            13359  2 uvcvideo,videodev
serio_raw               4022  0 
led_class               2633  0 
soundcore                880  1 snd
snd_page_alloc          7120  2 snd_hda_intel,snd_pcm
i2c_algo_bit            5168  1 i915
agpgart                32011  2 drm,intel_agp
video                  18712  1 i915
output                  1883  1 video
lp                      7342  0 
parport                31492  3 parport_pc,ppdev,lp
ahci                   19198  2 
libahci                21728  1 ahci
atl1c                  29949  0 
```

---

