---
title: "Wireless network not visible"
date: 2013-03-18
forum: Networking &amp; Wireless
---

### Post by Adi Krishnan on 2013-03-18
Hi,

I am fairly new to linux and installed Kubuntu yesterday. Since my installation, I've been unable to see my private wireless network but I can see others. I tried going to many forums but wasn't able to find something that matched my needs. I would like some help to fix this.

I ran some commands I found.

```

$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=19 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
eth0      no wireless extensions.

```

Digi123 is the ESSID of my network, I checked it at the modem configuration on the browser.

```

$ iwconfig essid $Digi123
essid     No such device

```

lsmod

```

$ lsmod
Module                  Size  Used by
iwlwifi               366509  0 
joydev                 17393  0 
parport_pc             32114  0 
ppdev                  12849  0 
rfcomm                 38139  16 
bnep                   17830  2 
btusb                  17948  2 
bluetooth             158479  23 rfcomm,bnep,btusb
bcma                   25651  0 
arc4                   12473  2 
dell_wmi               12601  0 
sparse_keymap          13658  1 dell_wmi
dell_laptop            17767  0 
dcdbas                 14098  1 dell_laptop
snd_hda_codec_idt      60251  1 
intel_ips              17822  0 
psmouse                86520  0 
serio_raw              13027  0 
snd_hda_intel          32765  3 
snd_hda_codec         109562  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80916  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51592  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
brcmsmac              540923  0 
mac_hid                13077  0 
mac80211              436493  2 iwlwifi,brcmsmac
snd                    62218  15 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
uvcvideo               67203  0 
brcmutil               14675  1 brcmsmac
videodev               86588  1 uvcvideo
cfg80211              178877  3 iwlwifi,brcmsmac,mac80211
soundcore              14635  1 snd
crc8                   12781  1 brcmsmac
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
cordic                 12518  1 brcmsmac
mei                    36570  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
usbhid                 41937  0 
hid                    77428  1 usbhid
i915                  423451  8 
wmi                    18744  1 dell_wmi
drm_kms_helper         45466  1 i915
drm                   197641  4 i915,drm_kms_helper
atl1c                  36718  0 
i2c_algo_bit           13199  1 i915
video                  19115  1 i915

```

---

### Post by Hadaka on 2013-03-18
Hi, please do..
```
lspci -nnk | grep -iA3 net
```

post the results.
thanks

---

### Post by Adi Krishnan on 2013-03-20
I do not know how but this started working again. Murphy's law I guess! :)

---

