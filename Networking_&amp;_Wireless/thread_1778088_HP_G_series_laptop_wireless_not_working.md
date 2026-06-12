---
title: "HP G series laptop wireless not working"
date: 2011-06-08
forum: Networking &amp; Wireless
---

### Post by AustinSanchez on 2011-06-08
Here's all the information I think you will need

BTW: I am using BackTrace, which I'm pretty sure is based on Ubuntu, if it isn't, my bad :(

I've been working on this for a few days now, and have looked at so many threads, I just can't find the answer. The wireless button on my keyboard is showing orange, and it won't let me turn it on (In windows I can press it and it turns blue), any advice please?

Edit: It is Ubuntu, Ubuntu 10.04.2 LTS

Thanks for any help
```

02:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8191SEvA Wireless LAN Controller (rev 10)

# ifconfig
eth0      Link encap:Ethernet  HWaddr 60:eb:69:25:09:b5  
          inet addr:192.168.1.108  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::62eb:69ff:fe25:9b5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5306 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4122 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6400665 (6.4 MB)  TX bytes:504583 (504.5 KB)
          Interrupt:42 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:179 errors:0 dropped:0 overruns:0 frame:0
          TX packets:179 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:28121 (28.1 KB)  TX bytes:28121 (28.1 KB)

root@bt:~# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

Module                  Size  Used by
dm_crypt               16476  0 
joydev                 10865  0 
snd_hda_codec_hdmi     24641  1 
snd_hda_codec_realtek   325232  1 
snd_hda_intel          25353  0 
snd_hda_codec          88363  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               6666  1 snd_hda_codec
snd_pcm_oss            39737  0 
snd_mixer_oss          15545  1 snd_pcm_oss
snd_pcm                83404  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1782  0 
snd_seq_oss            29952  0 
snd_seq_midi            5676  0 
snd_rawmidi            21765  1 snd_seq_midi
snd_seq_midi_event      6708  2 snd_seq_oss,snd_seq_midi
snd_seq                54693  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              21990  2 snd_pcm,snd_seq
snd_seq_device          6265  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
hp_wmi                  6315  0 
snd                    65330  13 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
sparse_keymap           3782  1 hp_wmi
soundcore               7208  1 snd
rfkill                 18476  1 hp_wmi
psmouse                60384  0 
snd_page_alloc          8117  2 snd_hda_intel,snd_pcm
wmi                     9912  1 hp_wmi
serio_raw               4784  0 
lp                      9893  0 
parport                34080  1 lp
mac_hid                 3869  0 
i915                  505415  1 
drm_kms_helper         32506  1 i915
r8169                  41388  0 
ahci                   21302  2 
mii                     4798  1 r8169
drm                   204443  3 i915,drm_kms_helper
libahci                21959  1 ahci
intel_agp              11830  1 i915
i2c_algo_bit            5564  1 i915
intel_gtt              16156  3 i915,intel_agp
video                  12530  1 i915

```

---

