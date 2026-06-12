---
title: "Which USB WiFi Adapter for 11.04"
date: 2011-10-03
forum: Networking &amp; Wireless
---

### Post by PutzFrau on 2011-10-03
Hi

I need a WiFi USB Stick for my Laptop. I have a D-Link DWL-G122 C1  (Ralink RT73) which causes an unstable connection in 11.04. I tried out a few workarounds without effect. So now I am looking for a good WiFi stick for 11.04, preferably as small as possible and obviously no Ralink RT73 Chip.

Any Suggestions?

Thanks

---

### Post by praseodym on 2011-10-03
I dont want to advise any hardware, but maybe we can solve the problem with your current stick. Please show the outputs of

```
lsusb
lsmod
iwconfig
```

---

### Post by PutzFrau on 2011-10-03
I won't be able to test any of your tips before tomorrow as I use cable internet where I am right now.

lsusb:

```
Bus 002 Device 004: ID 04f2:b1da Chicony Electronics Co., Ltd 
Bus 002 Device 003: ID 046d:c062 Logitech, Inc. 
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 07d1:3c03 D-Link System AirPlus G DWL-G122 Wireless Adapter(rev.C1) [Ralink RT73]
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```


lsmod:

```
Module                  Size  Used by
arc4                   12473  2 
rt73usb                26854  0 
crc_itu_t              12627  1 rt73usb
rt2x00usb              19693  1 rt73usb
rt2x00lib              39075  2 rt73usb,rt2x00usb
mac80211              257001  2 rt2x00usb,rt2x00lib
cfg80211              156212  2 rt2x00lib,mac80211
cisco_ipsec           602355  1 
binfmt_misc            13213  1 
vboxnetadp             13323  0 
vboxnetflt             27855  0 
vboxdrv               219250  2 vboxnetadp,vboxnetflt
parport_pc             32111  0 
ppdev                  12849  0 
snd_hda_codec_hdmi     27479  1 
joydev                 17322  0 
snd_hda_codec_realtek   255820  1 
snd_hda_intel          24140  2 
snd_hda_codec          90901  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80244  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
nvidia               9766978  0 
uvcvideo               66851  0 
videodev               75143  1 uvcvideo
i915                  450944  7 
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
psmouse                73312  0 
drm_kms_helper         40745  1 i915
intel_ips              17769  0 
serio_raw              12990  0 
snd                    55295  14 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm                   180037  3 i915,drm_kms_helper
i2c_algo_bit           13184  1 i915
soundcore              12600  1 snd
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
ideapad_laptop         13262  0 
sparse_keymap          13666  1 ideapad_laptop
video                  18951  1 i915
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
usbhid                 41704  0 
hid                    77084  1 usbhid
ahci                   21591  3 
atl1c                  36237  0 
libahci                25548  1 ahci
```

iwconfig

```
wlan1     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
```

---

### Post by praseodym on 2011-10-03
Shut off the power management:

```
sudo iwconfig wlan0 power off
sudo service network-manager restart
```
I recommend WPA2-AES (CCMP) encryption with the network-manager for stability and security reasons.

---

### Post by PutzFrau on 2011-10-03
Will test that tomorrow asap.
What I did not mention: It works fine under 10.10.

---

### Post by PutzFrau on 2011-10-04
I probably won't get my wireless router before next week. I will keep you up to date about my efforts.

---

### Post by dayrehabs on 2011-10-04
Wireless USB adapters are pretty popular for desktop and laptop usage in  home. It  is capable of sending 480 Mbit/s at distances up to 3 meters  and 110 Mbit/s at up to 10 meters. Newer N series can work at 270Mbit/s  at up to 300 meters. However, 50-100 meters are acceptable ranges.  Unfortunately, finding Linux compatible USB wireless adapter is a big  challenge due to driver issues. Over a past few years, I've used and  installed various USB wireless adapters and created my own small HCL for  it. In this quick blog post I will list all working USB wireless  adapter.
[[COLOR=#000000][FONT=Arial]_long term alcohol rehabs_[/FONT][/COLOR]]("http://www.drug-alcohol-rehabs.org/long-term-rehab.html")
[[COLOR=#000000][FONT=Arial]_long term drug rehabs_[/FONT][/COLOR]]("http://www.drug-alcohol-rehabs.org/rehab-centers.html")
[[COLOR=#000000][FONT=Arial]_long term rehabs_[/FONT][/COLOR]]("http://www.drug-alcohol-rehabs.org/affordable-drug-rehab.html")
[COLOR=#000000][FONT=Arial] [/FONT][/COLOR]

---

### Post by runesvend on 2011-11-24
I'm also looking for a well-functioning USB Wifi dongle to use with Natty.

I'm getting really tired of my TP-Link TL-WN821N v3. It often hangs my whole system, or just drops the connection. Often I have to do a cold restart because the system stops responding (presumably because of a buggy kernel driver).

Anyone know of a good, stable USB wifi dongle for Linux, preferably with an open source driver so any bugs that appear can be fixed?

---

