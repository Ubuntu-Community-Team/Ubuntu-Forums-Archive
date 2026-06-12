---
title: "Upgraded to 10.10 and wired internet no longer functions properly (Atheros AR8152)"
date: 2011-01-12
forum: Networking &amp; Wireless
---

### Post by adari1 on 2011-01-12
related hardware:
Asus 1215n
Atheros AR8152

I upgraded to 10.10 to fix a mic problem, and as result my internet no longer functions properly.  I can use the internet fine for web browsing, I am even using it to post this right now.  The problem comes, the moment I try to use any chat client.  If pidgin tries to connect to anything, then the connection breaks entirely, and refuses to reestablish unless I restart the system entirely.  Not just pidgin, if the gmail gchat page tries to connect, it also does this, and so does facebook.  I can go to one 'chat-like' server, KGS Go Server, without this issue. I researched for over two hours on any solution, to no avail. I hope that someone here can try to help me, thank you.

Here is some info that I saw other people being asked:
******While internet is working
ifconfig
```

eth0      Link encap:Ethernet  HWaddr 20:cf:30:21:e0:f1  
          inet addr:10.31.21.50  Bcast:10.31.21.255  Mask:255.255.255.0
          inet6 addr: fe80::22cf:30ff:fe21:e0f1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1192 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1252 errors:0 dropped:0 overruns:0 carrier:1
          collisions:0 txqueuelen:1000 
          RX bytes:943981 (943.9 KB)  TX bytes:282209 (282.2 KB)
          Interrupt:45 


```
sudo /sbin/route -n
```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.31.21.0      0.0.0.0         255.255.255.0   U     1      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         10.31.21.1      0.0.0.0         UG    0      0        0 eth0

```
--lspci | grep ethernet
(nothing)
lsmod
```

Module                  Size  Used by
parport_pc             26058  0 
ppdev                   5556  0 
binfmt_misc             6599  1 
snd_hda_codec_realtek   218227  1 
joydev                  8767  0 
arc4                    1165  2 
snd_hda_intel          22107  2 
snd_hda_codec          87552  2 snd_hda_codec_realtek,snd_hda_intel
nouveau               517242  0 
snd_hwdep               5040  1 snd_hda_codec
snd_pcm                71475  2 snd_hda_intel,snd_hda_codec
ttm                    56633  1 nouveau
snd_seq_midi            4588  0 
ath9k                  88756  0 
i915                  294989  3 
snd_rawmidi            17783  1 snd_seq_midi
snd_seq_midi_event      6047  1 snd_seq_midi
ath9k_common            5982  1 ath9k
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
ath9k_hw              292297  2 ath9k,ath9k_common
drm_kms_helper         30200  2 nouveau,i915
ath                     8153  2 ath9k,ath9k_hw
mac80211              231541  2 ath9k,ath9k_common
snd_timer              19067  2 snd_pcm,snd_seq
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
uvcvideo               55847  0 
eeepc_wmi               2899  0 
sparse_keymap           3145  1 eeepc_wmi
drm                   168092  5 nouveau,ttm,i915,drm_kms_helper
cfg80211              144470  4 ath9k,ath9k_common,ath,mac80211
videodev               43098  1 uvcvideo
snd                    49038  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
v4l1_compat            13359  2 uvcvideo,videodev
intel_agp              26694  2 i915
psmouse                59033  0 
led_class               2633  1 ath9k
soundcore                880  1 snd
serio_raw               4022  0 
snd_page_alloc          7120  2 snd_hda_intel,snd_pcm
agpgart                32011  3 ttm,drm,intel_agp
i2c_algo_bit            5168  2 nouveau,i915
video                  18712  1 i915
output                  1883  1 video
lp                      7342  0 
parport                31492  3 parport_pc,ppdev,lp
ahci                   19198  2 
libahci                21664  1 ahci
atl1c                  29949  0 

```
--ping 8.8.8.8
```

--- 8.8.8.8 ping statistics ---
128 packets transmitted, 128 received, 0% packet loss, time 127187ms
rtt min/avg/max/mdev = 57.699/59.147/67.478/1.348 ms

```


*******After internet breaks
ifconfig
```

eth0      Link encap:Ethernet  HWaddr 20:cf:30:21:e0:f1   
          inet addr:10.31.21.50  Bcast:10.31.21.255  Mask:255.255.255.0 
          inet6 addr: fe80::22cf:30ff:fe21:e0f1/64 Scope:Link 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1 
          RX packets:1972 errors:0 dropped:0 overruns:0 frame:0 
          TX packets:1576 errors:0 dropped:0 overruns:0 carrier:1 
          collisions:0 txqueuelen:1000  
          RX bytes:1964356 (1.9 MB)  TX bytes:181148 (181.1 KB) 
          Interrupt:45

```
sudo /sbin/route -n
```

Kernel IP routing table 
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface 
10.31.21.0      0.0.0.0         255.255.255.0   U     1      0        0 eth0 
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0 
0.0.0.0         10.31.21.1      0.0.0.0         UG    0      0        0 eth0

```
lspci | grep ethernet
```

nothing

```
lsmod
```

Module                  Size  Used by 
binfmt_misc             6599  1  
parport_pc             26058  0  
ppdev                   5556  0  
snd_hda_codec_realtek   218227  1  
joydev                  8767  0  
snd_hda_intel          22107  2  
snd_hda_codec          87552  2 snd_hda_codec_realtek,snd_hda_intel 
snd_hwdep               5040  1 snd_hda_codec 
nouveau               517242  0  
arc4                    1165  2  
snd_pcm                71475  2 snd_hda_intel,snd_hda_codec 
ath9k                  88756  0  
i915                  294989  3  
snd_seq_midi            4588  0  
ath9k_common            5982  1 ath9k 
ath9k_hw              292297  2 ath9k,ath9k_common 
ath                     8153  2 ath9k,ath9k_hw 
mac80211              231541  2 ath9k,ath9k_common 
snd_rawmidi            17783  1 snd_seq_midi 
snd_seq_midi_event      6047  1 snd_seq_midi 
ttm                    56633  1 nouveau 
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event 
snd_timer              19067  2 snd_pcm,snd_seq 
drm_kms_helper         30200  2 nouveau,i915 
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq 
eeepc_wmi               2899  0  
uvcvideo               55847  0  
sparse_keymap           3145  1 eeepc_wmi 
cfg80211              144470  4 ath9k,ath9k_common,ath,mac80211 
drm                   168092  5 nouveau,i915,ttm,drm_kms_helper 
intel_agp              26694  2 i915 
videodev               43098  1 uvcvideo 
snd                    49038  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device 
psmouse                59033  0  
v4l1_compat            13359  2 uvcvideo,videodev 
led_class               2633  1 ath9k 
serio_raw               4022  0  
agpgart                32011  3 ttm,intel_agp,drm 
soundcore                880  1 snd 
snd_page_alloc          7120  2 snd_hda_intel,snd_pcm 
i2c_algo_bit            5168  2 nouveau,i915 
video                  18712  1 i915 
output                  1883  1 video 
lp                      7342  0  
parport                31492  3 parport_pc,ppdev,lp 
ahci                   19198  2  
libahci                21664  1 ahci 
atl1c                  29949  0 

```
ping 8.8.8.8
```

forgot to save the exact words but the ping no longer works at all.

```

---

### Post by adari1 on 2011-01-13
solution found here:
[http://ubuntuforums.org/showthread.php?t=1617044](http://ubuntuforums.org/showthread.php?t=1617044)

---

