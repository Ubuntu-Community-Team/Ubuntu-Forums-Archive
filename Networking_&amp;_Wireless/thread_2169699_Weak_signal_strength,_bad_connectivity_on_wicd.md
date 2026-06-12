---
title: "Weak signal strength, bad connectivity on wicd"
date: 2013-08-23
forum: Networking &amp; Wireless
---

### Post by lisa_m2 on 2013-08-23
Hi all,

I've been a Linux-user from birth, but am now posting for the first time in the forum - and I hope that somebody can help me with my issue :)
I'm running wicd on a Dell XPS 14z with 12.10 installed. All of a sudden, without me changing any configuration, the signal strength drops immensely, as does the speed and overall connectivity. Now I can get max. 40%, usually more around 28% on wicd. 
The router hasn't been moved, and although it's placed in the next room (my flatmate's - so I can't move it or plug in the cable), I know that I can get up to 70-80%. 
This issue has already appeared a few times just out of the blue, unfortunately I haven't documented how I fixed it :( Now I'm at my wit's end, have searched forums and the internet, and am in desperate need of your help.

Here's some output of the console, please tell me what else you need:

iwconfig:
```
eth0      no wireless extensions.

lo        no wireless extensions.


wlan0     IEEE 802.11abgn  ESSID:"dlinkmfd"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:24:01:F7:53:24   
          Bit Rate=12 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=24/70  Signal level=-86 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:14  Invalid misc:1701   Missed beacon:0
```

ifconfig:
```
eth0      Link encap:Ethernet  Hardware Adresse d4:be:d9:05:ff:4e            UP BROADCAST MULTICAST  MTU:1500  Metrik:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:1000 
          RX-Bytes:0 (0.0 B)  TX-Bytes:0 (0.0 B)


lo        Link encap:Lokale Schleife  
          inet Adresse:127.0.0.1  Maske:255.0.0.0
          inet6-Adresse: ::1/128 Gültigkeitsbereich:Maschine
          UP LOOPBACK RUNNING  MTU:16436  Metrik:1
          RX packets:5098 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5098 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:0 
          RX-Bytes:419012 (419.0 KB)  TX-Bytes:419012 (419.0 KB)


wlan0     Link encap:Ethernet  Hardware Adresse 88:53:2e:74:a6:30  
          inet Adresse:192.168.0.10  Bcast:192.168.0.255  Maske:255.255.255.0
          inet6-Adresse: fe80::8a53:2eff:fe74:a630/64 Gültigkeitsbereich:Verbindung
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metrik:1
          RX packets:12537 errors:0 dropped:0 overruns:0 frame:0
          TX packets:11547 errors:0 dropped:0 overruns:0 carrier:0
          Kollisionen:0 Sendewarteschlangenlänge:1000 
          RX-Bytes:12605508 (12.6 MB)  TX-Bytes:2030501 (2.0 MB)

```

lsmod:
```
Module                  Size  Used byparport_pc             32689  0 
ppdev                  17074  0 
rfcomm                 46620  12 
bnep                   18141  2 
joydev                 17458  0 
snd_hda_codec_hdmi     32049  1 
snd_hda_codec_realtek    78147  1 
uvcvideo               76750  0 
nouveau               896008  1 
videobuf2_core         32852  1 uvcvideo
videodev              120310  2 uvcvideo,videobuf2_core
arc4                   12530  2 
videobuf2_vmalloc      12861  1 uvcvideo
videobuf2_memops       13405  1 videobuf2_vmalloc
iwlwifi               386837  0 
i915                  520799  2 
ttm                    83596  1 nouveau
coretemp               13401  0 
snd_hda_intel          33492  3 
drm_kms_helper         49113  2 nouveau,i915
drm                   288436  6 nouveau,i915,ttm,drm_kms_helper
kvm_intel             132760  0 
psmouse               100389  0 
kvm                   414111  1 kvm_intel
snd_hda_codec         134213  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
ghash_clmulni_intel    13221  0 
snd_hwdep              17699  1 snd_hda_codec
snd_pcm                96668  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13325  0 
snd_rawmidi            30513  1 snd_seq_midi
aesni_intel            51038  2 
cryptd                 20404  2 ghash_clmulni_intel,aesni_intel
serio_raw              13216  0 
aes_x86_64             17256  1 aesni_intel
mac80211              535936  1 iwlwifi
snd_seq_midi_event     14900  1 snd_seq_midi
snd_seq                61555  2 snd_seq_midi,snd_seq_midi_event
cfg80211              206797  2 iwlwifi,mac80211
dell_laptop            17370  0 
dcdbas                 14439  1 dell_laptop
btusb                  22475  0 
mac_hid                13206  0 
dell_wmi               12682  0 
sparse_keymap          13891  1 dell_wmi
snd_timer              29426  2 snd_pcm,snd_seq
snd_seq_device         14498  3 snd_seq_midi,snd_rawmidi,snd_seq
bluetooth             209249  22 rfcomm,bnep,btusb
snd                    78921  16 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
microcode              22804  0 
mei                    40691  0 
rtsx_pci_ms            13012  0 
soundcore              15048  1 snd
i2c_algo_bit           13414  2 nouveau,i915
snd_page_alloc         18485  2 snd_hda_intel,snd_pcm
video                  19391  2 nouveau,i915
mxm_wmi                13022  1 nouveau
wmi                    19071  3 nouveau,dell_wmi,mxm_wmi
memstick               16555  1 rtsx_pci_ms
lpc_ich                17062  0 
lp                     17760  0 
parport                46346  3 parport_pc,ppdev,lp
ses                    17364  0 
enclosure              15209  1 ses
usb_storage            48839  1 
rtsx_pci_sdmmc         17476  0 
ahci                   25721  3 
libahci                31192  1 ahci
rtsx_pci               33452  2 rtsx_pci_ms,rtsx_pci_sdmmc
atl1c                  41102  0 
```

(I'm sure you need some more, so please ask)

I've tried a bunch of things (i.e. turning off wlan0), but I'm really bad with all things related to network so I don't know where to begin. I appreciate all help greatly! Thank you :)

---

### Post by lisa_m2 on 2013-08-26
I'm still experiencing the same problem and haven't found a solution. Can anybody help, please? I'm obviously still looking, however it's very hard to do that with a weak/no connection :(

---

