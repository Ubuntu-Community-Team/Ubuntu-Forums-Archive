---
title: "Working SSH and X2Go but no network"
date: 2012-12-06
forum: Networking &amp; Wireless
---

### Post by clownius on 2012-12-06
Ok this is an odd one and im not even sure where to start.

Im running a headless Kubuntu Box at home as a NAS/Torrent Box and whatever i feel like at the time.  I generally control it via SSH but also have X2Go setup so i can remote desktop when i feel like it.

I made the mistake of upgrading from 12.04 to 12.10.

I can SSH into it and even open a Remote desktop with x2go no problems so i know the actual Network card is working and it is connected.  

But Network Manager doesnt start with the box and when i enable networking i get "No network Interfaces".

Also Deluged cant connect to anything but Firefox and Filezilla can....

This is your average every day bog standard Gigabit Ethernet port.

I have seen the following suggested to provide more info

```
lspci -nnk | grep -iA2 net
04:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR8151 v2.0 Gigabit Ethernet [1969:1083] (rev c0)
        Subsystem: Giga-byte Technology Device [1458:e000]
        Kernel driver in use: atl1c

lsmod
Module                  Size  Used by
tcp_diag               12591  0 
inet_diag              18477  1 tcp_diag
bnep                   18140  2 
rfcomm                 46619  0 
bluetooth             209199  10 bnep,rfcomm
parport_pc             32688  0 
ppdev                  17073  0 
nls_iso8859_1          12713  1 
snd_hda_codec_hdmi     32007  1 
snd_hda_codec_via      46599  1 
coretemp               13400  0 
snd_hda_intel          33491  0 
kvm                   414070  0 
ghash_clmulni_intel    13180  0 
aesni_intel            51037  0 
cryptd                 20403  2 ghash_clmulni_intel,aesni_intel
snd_hda_codec         134212  3 snd_hda_codec_hdmi,snd_hda_codec_via,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm                96580  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30512  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61521  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29425  2 snd_pcm,snd_seq
lpc_ich                17061  0 
aes_x86_64             17208  1 aesni_intel
snd_seq_device         14497  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    78734  10 snd_hda_codec_hdmi,snd_hda_codec_via,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
mac_hid                13205  0 
mei                    40690  0 
psmouse                95552  0 
soundcore              15047  1 snd
microcode              22803  0 
snd_page_alloc         18484  2 snd_hda_intel,snd_pcm
serio_raw              13215  0 
lp                     17759  0 
parport                46345  3 parport_pc,ppdev,lp
i915                  520629  1 
drm_kms_helper         46784  1 i915
drm                   275528  2 i915,drm_kms_helper
atl1c                  41101  0 
i2c_algo_bit           13413  1 i915
video                  19335  1 i915

nm-tool

** (process:11366): WARNING **: Could not initialize NMClient /org/freedesktop/NetworkManager: Rejected send message, 2 matched rules; type="method_call", sender=":1.45" (uid=1000 pid=11366 comm="nm-tool ") interface="org.freedesktop.DBus.Properties" member="GetAll" error name="(unset)" requested_reply="0" destination="org.freedesktop.NetworkManager" (uid=0 pid=1157 comm="NetworkManager ")

NetworkManager Tool

State: unknown


** (process:11366): WARNING **: error: could not connect to NetworkManager
```

I would like in the future to setup a VPN from this box too so it would be nice to have a working network manager.

---

