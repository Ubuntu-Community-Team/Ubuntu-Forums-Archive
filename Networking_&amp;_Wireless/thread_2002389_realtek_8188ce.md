---
title: "realtek 8188ce"
date: 2012-06-12
forum: Networking &amp; Wireless
---

### Post by mintfan2389 on 2012-06-12
My realtek 8188ce seems to get really slow at times and some times when I boot ubuntu my wifi will be disabled , I have tried using ndiswrapper with no success , anybody else have this card ? and how did you get it to work correctly , also it works fine on windows 7 and 8 but mint and ubuntu seem to not want to work correctly with this card any help please ?

---

### Post by praseodym on 2012-06-12
Hi,

please show from terminal (CTRL+ALT+T):

```
uname -a
lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
rfkill list
```
What kind of computer is that?

---

### Post by mamaragan on 2012-07-21
I am also having wifi issues. Dropping out after login & not being able to reconnect. No problem at all with Win7. Terminal output below

stephen@stephen-Satellite-L840:~$ uname -a
Linux stephen-Satellite-L840 3.2.0-26-generic #41-Ubuntu SMP Thu Jun 14 17:49:24 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

stephen@stephen-Satellite-L840:~$ lspci -nnk | grep -iA2 net
08:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter [10ec:8176] (rev 01)
	Kernel driver in use: rtl8192ce
	Kernel modules: rtl8192ce
09:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR8151 v2.0 Gigabit Ethernet [1969:1083] (rev c0)
	Subsystem: Toshiba America Info Systems Device [1179:fb50]
	Kernel driver in use: atl1c

stephen@stephen-Satellite-L840:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 001 Device 004: ID 064e:e21c Suyin Corp. 

stephen@stephen-Satellite-L840:~$ lsmod
Module                  Size  Used by
rfcomm                 47604  0 
bnep                   18281  2 
bluetooth             180104  10 rfcomm,bnep
parport_pc             32866  0 
ppdev                  17113  0 
binfmt_misc            17540  1 
snd_hda_codec_hdmi     32474  1 
snd_hda_codec_conexant    62311  1 
snd_hda_intel          33773  1 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel
snd_seq_midi           13324  0 
snd_hwdep              13668  1 snd_hda_codec
joydev                 17693  0 
snd_rawmidi            30748  1 snd_seq_midi
snd_pcm                97188  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
hid_logitech_dj        18594  0 
arc4                   12529  2 
radeon                804372  2 
ttm                    76949  1 radeon
uvcvideo               72627  0 
drm_kms_helper         46978  1 radeon
drm                   242038  4 radeon,ttm,drm_kms_helper
rtl8192ce              84826  0 
rtl8192c_common        75767  1 rtl8192ce
rtlwifi               111202  1 rtl8192ce
snd                    78855  12 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_rawmidi,snd_pcm,snd_seq,snd_timer,snd_seq_device
videodev               98259  1 uvcvideo
mac80211              506816  3 rtl8192ce,rtl8192c_common,rtlwifi
psmouse                87692  0 
serio_raw              13211  0 
v4l2_compat_ioctl32    17128  1 videodev
toshiba_acpi           18582  0 
sparse_keymap          13890  1 toshiba_acpi
i2c_algo_bit           13423  1 radeon
cfg80211              205544  2 rtlwifi,mac80211
mac_hid                13253  0 
mei                    41616  0 
video                  19596  0 
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
wmi                    19256  1 toshiba_acpi
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
reiserfs              244805  2 
atl1c                  41717  0 
usbhid                 47199  1 hid_logitech_dj
hid                    99559  2 hid_logitech_dj,usbhid

stephen@stephen-Satellite-L840:~$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"NETGEAR20"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 2C:B0:5D:72:11:C7   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=58/70  Signal level=-52 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

stephen@stephen-Satellite-L840:~$ rfkill list
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

Thanks in advance - Steve

---

### Post by praseodym on 2012-07-22
Check the encryption mode of your network. Mixed mode WPA/WPA2 is pretty unstable with the NM, better is WPA2-AES.

---

