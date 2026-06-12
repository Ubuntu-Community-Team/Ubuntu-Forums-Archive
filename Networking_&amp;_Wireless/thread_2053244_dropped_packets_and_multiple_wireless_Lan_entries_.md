---
title: "dropped packets and multiple wireless Lan entries in rfkill"
date: 2012-09-04
forum: Networking &amp; Wireless
---

### Post by sportsdude81 on 2012-09-04
I am getting really long latency (like 400-500 ms) and packets are dropping left and right.  I have a Broadcom wireless card so I had to install there proprietary drivers which were working fine until the most recent update I got in 12.04. Now I have to wireless entries in rfkill:

```
[~]
$ rfkill list
0: brcmwl-0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
2: hp-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
3: hp-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no

```

the first brcmwl-0 is the broadcom one from the driver. I don't know where this hp-wifi one came from.

Does anybody have any insight on this?

Thanks in advance

Edit: More info
```

$ lspci -nn | grep 14e4
02:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)

```

```

$ lsmod
Module                  Size  Used by
joydev                 17693  0 
snd_hda_codec_hdmi     32474  1 
snd_hda_codec_idt      70795  1 
btusb                  18288  2 
uvcvideo               72627  0 
snd_hda_intel          33773  3 
videodev               98259  1 uvcvideo
v4l2_compat_ioctl32    17128  1 videodev
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
rfcomm                 47604  12 
snd_hwdep              13668  1 snd_hda_codec
bnep                   18281  2 
bluetooth             180104  23 btusb,rfcomm,bnep
snd_pcm                97188  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
parport_pc             32866  0 
ppdev                  17113  0 
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
hp_wmi                 18092  0 
sparse_keymap          13890  1 hp_wmi
binfmt_misc            17540  1 
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
lib80211_crypt_tkip    17390  0 
wl                   2568210  0 
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
i915                  472941  3 
snd                    78855  16 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                85790  0 
drm_kms_helper         46978  1 i915
serio_raw              13211  0 
drm                   242038  4 i915,drm_kms_helper
mei                    41616  0 
rts_pstor             445196  0 
i2c_algo_bit           13423  1 i915
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
lib80211               14381  2 lib80211_crypt_tkip,wl
wmi                    19256  1 hp_wmi
mac_hid                13253  0 
video                  19596  1 i915
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
sdhci_pci              18826  0 
sdhci                  33205  1 sdhci_pci
r8169                  62099  0 

```

---

### Post by sportsdude81 on 2012-09-05
Seem to fix this by adding this to my /etc/modeprobe.d/blacklist.conf:

```

blacklist bcma
blacklist brcm80211
blacklist brcmsmac
blacklist ssb
blacklist b43

```

got that gem from this arch linux wiki [https://wiki.archlinux.org/index.php/HP_Folio_13]("https://wiki.archlinux.org/index.php/HP_Folio_13")

---

