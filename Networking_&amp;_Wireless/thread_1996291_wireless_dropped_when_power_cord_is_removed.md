---
title: "wireless dropped when power cord is removed"
date: 2012-06-04
forum: Networking &amp; Wireless
---

### Post by shinkansen on 2012-06-04
Forgive me for cross posting (with apple users forum - many views but no replies).

I have a mac book air 4.2, single boot kubuntu 12.04.

When the power cable is removed by wireless network connection stops dead, if I plug it back in the wireless starts up again (and the connection come back to life some 20 seconds later).  Obviously this is a big problem and very likely something to do with power management but beyond that I'm stumped.

I have  this module installed bcm5974 the syslogs give no clue as to what is happening.

Any ideas where to start?

---

### Post by shinkansen on 2012-06-04
I found the offending script and bodged it:
/usr/lib/pm-utils/power.d/wireless

by changing this line:
 iwconfig_batt="power on";;

to

iwconfig_batt="power off";;

It would appear the either 

(1) this script is suggesting that turning the wireless off is the right thing to do on battery (unlikely) or 

(2) the power management is borked because I get no wireless whatsoever with "power on" 

I suspect the latter - this could (of course) be some quirk of the mac but is probably something wrong with drivers?

I'm not sure what the power consequences of this bodge but "no network" is not an acceptable outcome!

---

### Post by sasasasasasa on 2012-06-06
bump - I'd really like to know if I've done something dumb or should be proceeding to file a bug against something (wireless driver or power management?)...

Ta

---

### Post by praseodym on 2012-06-06
Check with
> iwconfig
if the power management is "on". If yes:

> sudo iwconfig wlan0 power off
Replace wlan0 with your wireless interface name, if necessary.

---

### Post by sasasasasasa on 2012-06-07
This is exactly what I have done in the power management script above.

My problem is should turning power management on cause the wireless to drop out? if not then there appears to be a bug downstream of this (presumably in the driver) which needs to be reported.

My other laptop (11.10) managed  just fine with power management turned on so it looks more likely this is bug in 12.04 or a bug associate with my hardware MPA. It looks likely that I need to file a bug against bcm5974 but I'd be interested to here if anyone else has this problem with 12.04.

---

### Post by sasasasasasa on 2012-06-07
Ok this appears to be a known issue with the wl driver:

[http://wiki.debian.org/wl#Known_Issues](http://wiki.debian.org/wl#Known_Issues)

Does anyone have any experience trying the b43 or brcmsmac/brcmfmac drivers under 12.04 (on a mba)?

Ta

---

### Post by praseodym on 2012-06-08
Please show:
> 
lspci -nnk | grep -iA2 net
lsmod
iwconfig

---

### Post by sasasasasasa on 2012-06-12
lspci -nnk |grep -iA2 net

02:00.0 Network controller [0280]: Broadcom BCM43224 802.11/a/b/g/n/[14e4:4353] (rev01)
Subsystem Apple Inc. Device [106b:00e9]
Kernel driver in use: wl

---

### Post by sasasasasasa on 2012-06-13
lsmod
Module                  Size  Used by
michael_mic            12612  0 
arc4                   12529  0 
usbhid                 47199  0 
dm_crypt               23125  0 
bnep                   18281  2 
rfcomm                 47604  0 
parport_pc             32866  0 
ppdev                  17113  0 
nls_iso8859_1          12713  1 
nls_cp437              16991  1 
vfat                   17585  1 
fat                    61512  1 vfat
snd_hda_codec_hdmi     32474  1 
snd_hda_codec_cirrus    23965  1 
joydev                 17693  0 
snd_hda_intel          33773  3 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_cirrus,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                97188  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
applesmc               19554  0 
input_polldev          13896  1 applesmc
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
lib80211_crypt_tkip    17390  0 
btusb                  18288  1 
bluetooth             180104  13 bnep,rfcomm,btusb
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    78855  16 snd_hda_codec_hdmi,snd_hda_codec_cirrus,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
uvcvideo               72627  0 
videodev               98259  1 uvcvideo
v4l2_compat_ioctl32    17128  1 videodev
wl                   2568210  0 
bcm5974                17399  0 
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
lib80211               14381  2 lib80211_crypt_tkip,wl
apple_bl               13673  0 
mac_hid                13253  0 
mei                    41616  0 
coretemp               13525  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
uas                    18180  0 
usb_storage            49198  0 
hid_apple              13375  0 
hid                    99559  2 usbhid,hid_apple
i915                  468764  3 
drm_kms_helper         46978  1 i915
drm                   242038  4 i915,drm_kms_helper
i2c_algo_bit           13423  1 i915
video                  19596  1 i915

---

### Post by sasasasasasa on 2012-06-13
iwconfig
lo        no wireless extensions.

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:222  Noise level:167
          Rx invalid nwid:0  invalid crypt:273  invalid misc:0

---

