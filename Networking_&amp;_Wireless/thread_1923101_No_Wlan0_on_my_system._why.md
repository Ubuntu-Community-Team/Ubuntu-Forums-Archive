---
title: "No Wlan0 on my system. why?"
date: 2012-02-09
forum: Networking &amp; Wireless
---

### Post by alecodd on 2012-02-09
hi! 
I reinstalled ubuntu, but iwconfig doesn't know aobut wlan0. why?

lspic | grep Network -> shows only atheros ar8131. is it a wireless card?

one more thing. how can i verify that it is a software problem, and not an hardware one?

thanks

---

### Post by wildmanne39 on 2012-02-10
Hi, welcome to the forum! Please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:

```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
iwconfig
rfkill list all
lsmod
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by alecodd on 2012-02-10
iwconfig :
lo        no wireless extensions.

eth0      no wireless extensions.

ppp0      no wireless extensions.
-------------------------------------------------

cat /etc/lsb-release:

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.04
DISTRIB_CODENAME=natty
DISTRIB_DESCRIPTION="Ubuntu 11.04"


-------------------------------------
lsmod:

Module                  Size  Used by
ppp_deflate            12838  0 
zlib_deflate           26594  1 ppp_deflate
bsd_comp               12777  0 
ppp_async              17308  1 
crc_ccitt              12595  1 ppp_async
option                 21045  2 
usb_wwan               19711  1 option
usbserial              37116  7 option,usb_wwan
usb_storage            43946  0 
uas                    17676  0 
binfmt_misc            13213  1 
parport_pc             32111  0 
ppdev                  12849  0 
snd_hda_codec_hdmi     27479  1 
snd_hda_codec_realtek   255820  1 
joydev                 17322  0 
snd_hda_intel          24140  2 
snd_hda_codec          90901  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80244  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
nouveau               621970  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
i915                  450944  8 
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
ttm                    65184  1 nouveau
uvcvideo               66851  0 
drm_kms_helper         40745  2 nouveau,i915
snd                    55295  14 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
videodev               75143  1 uvcvideo
psmouse                73312  0 
intel_ips              17769  0 
drm                   180037  6 nouveau,i915,ttm,drm_kms_helper
serio_raw              12990  0 
asus_laptop            19298  0 
soundcore              12600  1 snd
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
i2c_algo_bit           13184  2 nouveau,i915
sparse_keymap          13666  1 asus_laptop
video                  18951  2 nouveau,i915
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
ahci                   21591  2 
libahci                25548  1 ahci
atl1c                  36237  0 

-----------------------------------

thnaks

---

### Post by wildmanne39 on 2012-02-10
Hi, I did not see any output for:
```
lspci -nnk | grep -iA2 net
rfkill list all
```
and if this is an usb adapter please post output of:
```
lsusb
```
Thanks

---

