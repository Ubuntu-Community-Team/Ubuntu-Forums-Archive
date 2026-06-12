---
title: "acer aspire 7250 wlan problem"
date: 2012-06-05
forum: Networking &amp; Wireless
---

### Post by rsacomp on 2012-06-05
i loaded xubuntu 12.04 32 bit on my acer aspire 7250 notebook. and i think its the wireless driver thats causing the pc to freeze. as soon as i unplug the lan and try connecting to wlan, it freezes. not accepting any keyboard/mouse input. also my audio driver . the microphone is very distorted, can i update this driver

---

### Post by praseodym on 2012-06-05
Hi,

please show the terminal (CTRL+ALT+T) outputs of:

```
lspci -nnk | grep -iA2 net
iwconfig
lsmod
rfkill list
```

---

### Post by rsacomp on 2012-06-06
riaz@riaz-Aspire-7250:~/Desktop$ lspci -nnk | grep -iA2 net
06:00.0 Network controller [0280]: Atheros Communications Inc. AR9485 Wireless Network Adapter [168c:0032] (rev 01)
	Subsystem: Lite-On Communications Inc Device [11ad:6617]
	Kernel driver in use: ath9k
--
07:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR8152 v2.0 Fast Ethernet [1969:2062] (rev c1)
	Subsystem: Acer Incorporated [ALI] Device [1025:0614]
	Kernel driver in use: atl1c
riaz@riaz-Aspire-7250:~/Desktop$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
eth0      no wireless extensions.

riaz@riaz-Aspire-7250:~/Desktop$ lsmod
Module                  Size  Used by
snd_hda_codec_realtek   174055  1 
snd_hda_codec_hdmi     31775  1 
sp5100_tco             13495  0 
joydev                 17393  0 
acer_wmi               23612  0 
sparse_keymap          13658  1 acer_wmi
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_hda_intel          32765  7 
snd_hda_codec         109562  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80845  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
arc4                   12473  2 
snd_seq_midi_event     14475  1 snd_seq_midi
ath9k                 117425  0 
mac80211              436455  1 ath9k
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
ath9k_common           13781  1 ath9k
snd_timer              28931  2 snd_pcm,snd_seq
psmouse                87213  0 
ath9k_hw              391523  2 ath9k,ath9k_common
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
serio_raw              13027  0 
k10temp                12990  0 
ath                    19387  3 ath9k,ath9k_common,ath9k_hw
cfg80211              178679  3 ath9k,mac80211,ath
uvcvideo               67203  0 
snd                    62064  24 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_rawmidi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_seq,snd_timer,snd_seq_device
videodev               86588  1 uvcvideo
rfcomm                 38139  4 
i2c_piix4              13093  0 
parport_pc             32114  0 
soundcore              14635  1 snd
bnep                   17830  2 
ppdev                  12849  0 
bluetooth             158438  10 rfcomm,bnep
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
radeon                729591  2 
ttm                    65344  1 radeon
drm_kms_helper         45466  1 radeon
drm                   197692  4 radeon,ttm,drm_kms_helper
i2c_algo_bit           13199  1 radeon
binfmt_misc            17292  1 
video                  19068  0 
mac_hid                13077  0 
wmi                    18744  1 acer_wmi
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
usbhid                 41906  0 
hid                    77367  1 usbhid
ums_realtek            17920  0 
uas                    17828  0 
atl1c                  36718  0 
usb_storage            39646  1 ums_realtek
riaz@riaz-Aspire-7250:~/Desktop$ rfkill list


many thanks

---

### Post by praseodym on 2012-06-06
No output with "rfkill list"? The card is turned off. No button/key/switch/key combination (e.g. Fn+F2)?

Checked the BIOS settings?

---

### Post by rsacomp on 2012-06-06
really sorry about this but my bad. i forgot to mention i physically turned off the wireless button because it was freezing as soon as it tried to connect. but theres no physical switch its a key combo that activates/deactivates the wireless feature

---

