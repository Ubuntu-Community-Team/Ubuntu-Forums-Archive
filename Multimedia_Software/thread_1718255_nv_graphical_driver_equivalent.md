---
title: "nv graphical driver equivalent ?"
date: 2011-03-31
forum: Multimedia Software
---

### Post by synhedionn on 2011-03-31
Hi,
I don't understand: on my eeePC Ubuntu 10.10 ,even if nv is in my xorg.conf , in lsmod I have no nv driver, but I have a graphical session. 

> :~$ lsmod
Module                  Size  Used by
aes_i586                7280  1 
aes_generic            26875  1 aes_i586
rfcomm                 33811  2 
l2cap                  37008  3 rfcomm
bluetooth              50500  2 rfcomm,l2cap
binfmt_misc             6599  1 
vboxnetadp              6454  0 
vboxnetflt             15152  0 
vboxdrv               190199  2 vboxnetadp,vboxnetflt
parport_pc             26058  0 
ppdev                   5556  0 
snd_hda_codec_realtek   218492  1 
snd_hda_intel          22235  2 
snd_hda_codec          87552  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5040  1 snd_hda_codec
snd_pcm                71475  2 snd_hda_intel,snd_hda_codec
arc4                    1165  2 
snd_seq_midi            4588  0 
snd_rawmidi            17783  1 snd_seq_midi
snd_seq_midi_event      6047  1 snd_seq_midi
ath9k                  88884  0 
i915                  295435  3 
ath9k_common            5982  1 ath9k
ath9k_hw              292329  2 ath9k,ath9k_common
drm_kms_helper         30200  1 i915
ath                     8153  2 ath9k,ath9k_hw
drm                   168060  3 i915,drm_kms_helper
joydev                  8767  0 
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
snd_timer              19067  2 snd_pcm,snd_seq
mac80211              231959  2 ath9k,ath9k_common
intel_agp              26566  2 i915
agpgart                32011  2 drm,intel_agp
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
cfg80211              144694  4 ath9k,ath9k_common,ath,mac80211
i2c_algo_bit            5168  1 i915
uvcvideo               55847  0 
lp                      7342  0 
psmouse                59033  0 
snd                    49038  13  snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore                880  1 snd
videodev               43098  1 uvcvideo
video                  18712  1 i915
snd_page_alloc          7120  2 snd_hda_intel,snd_pcm
eeepc_laptop           14193  0 
serio_raw               4022  0 
sparse_keymap           3145  1 eeepc_laptop
led_class               2633  2 ath9k,eeepc_laptop
v4l1_compat            13359  2 uvcvideo,videodev
output                  1883  1 video
parport                31492  3 parport_pc,ppdev,lp
ahci                   19198  2 
libahci                21728  1 ahci
atl1c                  29949  0 
So how can I have a graphical session without  nv nor nvidia driver?

---

### Post by Mia1990 on 2011-03-31
I think ubuntu installs the nouveaux driver when you install ubuntu the nouveaux driver doesn't do so well for compiz but i think they are working on a driver to do compiz.

---

### Post by synhedionn on 2011-03-31
I thought too about Nouveau driver but it's not in lsmod, nor in xorg.conf:
...Oh it's not there anymore, but xorg.conf.dist-upgrade-201010150737 !!?...strange.

---

### Post by coffeecat on 2011-03-31
> **synhedionn said:**
> I thought too about Nouveau driver but it's not in lsmod, nor in xorg.conf:

Unless you installed the proprietary nvidia driver, you are using the nouveau driver if you have a nvidia graphics card. It doesn't appear in the output of lsmod because it is not a kernel module. You do not have an xorg.conf file because you don't need one with the version of the xserver that comes with 10.10 if you are using an open source driver. Or rather, you only need one for rare occasions. The newer versions of xserver autodetect hardware and autoconfigure themselves.

---

### Post by Yellow Pasque on 2011-03-31
Are you sure you have an nvidia card? I see intel modules (i915) loaded. Check /var/log/Xorg.0.log to know what driver is being used.

---

### Post by synhedionn on 2011-03-31
good clues   coffeecat and Temüjin.
Thank you all.

I'll see it.

---

