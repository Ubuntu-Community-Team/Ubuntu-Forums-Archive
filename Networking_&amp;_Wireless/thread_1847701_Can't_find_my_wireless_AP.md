---
title: "Can't find my wireless AP"
date: 2011-09-21
forum: Networking &amp; Wireless
---

### Post by V@L! on 2011-09-21
Hi to all . Can anyone tell me how to change the regulatory domain from US to an EU country , because my ISP has the channel 13 , so it isn't supported by default from Ubuntu. Thanks .

---

### Post by chili555 on 2011-09-21
It usually depends on the wireless driver and/or one of its dependencies. What is yours? Please open a terminal and run and post:```
lsmod
```

---

### Post by V@L! on 2011-09-21
Here are :

> 
Module                  Size  Used by
dm_crypt               22463  0 
lp                     13349  0 
binfmt_misc            13213  1 
snd_hda_codec_realtek   255820  1 
snd_hda_intel          24140  2 
snd_usb_audio          91410  1 
snd_hda_codec          90901  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13274  2 snd_usb_audio,snd_hda_codec
snd_usbmidi_lib        24388  1 snd_usb_audio
snd_pcm                80244  3 snd_hda_intel,snd_usb_audio,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25269  2 snd_usbmidi_lib,snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
arc4                   12473  2 
snd_timer              28659  2 snd_pcm,snd_seq
ath5k                 144412  0 
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
ath                    19141  1 ath5k
snd                    55295  17 snd_hda_codec_realtek,snd_hda_intel,snd_usb_audio,snd_hda_codec,snd_hwdep,snd_usbmidi_lib,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ppdev                  12849  0 
gspca_stv06xx          32353  0 
mac80211              257001  1 ath5k
psmouse                73312  0 
gspca_main             27894  1 gspca_stv06xx
parport_pc             32111  1 
cfg80211              156212  3 ath5k,ath,mac80211
soundcore              12600  1 snd
parport                36746  3 lp,ppdev,parport_pc
videodev               75143  1 gspca_main
serio_raw              12990  0 
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
squashfs               35973  1 
aufs                  159344  3681 
nls_utf8               12493  1 
isofs                  39571  1 
dm_raid45              88410  0 
xor                    21860  1 dm_raid45
btrfs                 527341  0 
zlib_deflate           26594  1 btrfs
libcrc32c              12543  1 btrfs
i915                  450944  3 
r8169                  42534  0 
drm_kms_helper         40745  1 i915
drm                   180037  4 i915,drm_kms_helper
i2c_algo_bit           13184  1 i915
video                  18951  1 i915




Is there any solution to change regulatory domain using TERMINAL.

---

### Post by chili555 on 2011-09-21
> Is there any solution to change regulatory domain using TERMINAL.Are you kidding me?? Dr. Chili does *everything* with the terminal:```
sudo please fix me a hot tea
```There are two suspects I can see. The module ath5k has a parameter:```
$ modinfo ath5k
filename:       /lib/modules/2.6.38-11-generic/updates/cw-2.6.39/ath5k.ko
<snip>
parm:           all_channels:Expose all channels the device can use. (bool)
```So you might try:```
sudo ifconfig wlan0 down
sudo rmmod -f ath5k
sudo modprobe ath5k all_channels=1
sudo ifconfig wlan0 up
```Now check:```
sudo iwlist wlan0 freq
```Another candidate is a parameter in cfg80211:```
$ modinfo cfg80211
filename:       /lib/modules/2.6.38-11-generic/updates/cw-2.6.39/cfg80211.ko
<snip>
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
```In this case, try:```
sudo ifconfig wlan0 down
sudo rmmod -f ath5k
sudo rmmod -f cfg80211
sudo modprobe cfg80211 ieee80211_regdom=UK  <--Use the country code you want, if not UK.
sudo modprobe ath5k
sudo ifconfig wlan0 up
```Then check:```
sudo iwlist wlan0 freq
```Whichever one works, we can write a conf file, for instance:```
sudo vim /etc/modprobe.d/cfg80211.conf
```Add one line:```
options cfg80211 ieee80211_regdom=UK
```Post back your findings, please.

---

### Post by V@L! on 2011-09-22
Still the same problem , it shows just channel from 1 to 11 , and I need channel 13. Is there any other solutions ?

---

### Post by chili555 on 2011-09-22
Please see: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/292772](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/292772)

Also see:  [http://osdir.com/ml/linux.drivers.ath5k.devel/2008-08/msg00038.html](http://osdir.com/ml/linux.drivers.ath5k.devel/2008-08/msg00038.html)> Right now cfg80211 only supports "US" and "EU" regulatory domains and
you can set this with a module parameter. As you can see this is very
limitedPlease try:```
options cfg80211 ieee80211_regdom=EU
```Reboot and let us know.

---

### Post by V@L! on 2011-09-22
It doesn't work.

Ubuntu 11.04

---

### Post by chili555 on 2011-09-22
I'm sorry, I'm out of ideas.

---

