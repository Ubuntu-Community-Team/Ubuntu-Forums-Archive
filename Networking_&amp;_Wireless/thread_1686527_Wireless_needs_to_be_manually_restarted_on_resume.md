---
title: "Wireless needs to be manually restarted on resume"
date: 2011-02-12
forum: Networking &amp; Wireless
---

### Post by JoeBrooks on 2011-02-12
I'm using an Eee PC 1001P, which (some googling tells me) has an AR2427 wireless chip.  I'm not sure what driver I'm using, probably ath9k from skimming my lsmod output:

```
Module                  Size  Used by
binfmt_misc             6599  1 
vboxnetadp              6454  0 
vboxnetflt             15152  0 
vboxdrv               190199  2 vboxnetadp,vboxnetflt
parport_pc             26058  0 
ppdev                   5556  0 
snd_hda_codec_realtek   218227  1 
joydev                  8767  0 
snd_hda_intel          22107  4 
rfcomm                 33811  8 
arc4                    1165  2 
snd_hda_codec          87552  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5040  1 snd_hda_codec
ath9k                  88756  0 
i915                  294989  5 
snd_pcm                71475  3 snd_hda_intel,snd_hda_codec
ath9k_common            5982  1 ath9k
snd_seq_midi            4588  0 
ath9k_hw              292297  2 ath9k,ath9k_common
sco                     7998  2 
snd_rawmidi            17783  1 snd_seq_midi
ath                     8153  2 ath9k,ath9k_hw
drm_kms_helper         30200  1 i915
bnep                    9542  2 
mac80211              231541  2 ath9k,ath9k_common
snd_seq_midi_event      6047  1 snd_seq_midi
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
l2cap                  37008  16 rfcomm,bnep
snd_timer              19067  2 snd_pcm,snd_seq
drm                   168092  5 i915,drm_kms_helper
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
uvcvideo               55847  0 
eeepc_wmi               2899  0 
btusb                  10969  2 
cfg80211              144470  4 ath9k,ath9k_common,ath,mac80211
psmouse                61837  0 
snd                    49038  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
intel_agp              26694  2 i915
bluetooth              50500  9 rfcomm,sco,bnep,l2cap,btusb
videodev               43098  1 uvcvideo
eeepc_laptop           14193  0 
v4l1_compat            13359  2 uvcvideo,videodev
serio_raw               4022  0 
i2c_algo_bit            5168  1 i915
video                  18712  1 i915
soundcore                880  1 snd
sparse_keymap           3145  2 eeepc_wmi,eeepc_laptop
led_class               2633  2 ath9k,eeepc_laptop
agpgart                32011  2 drm,intel_agp
snd_page_alloc          7120  2 snd_hda_intel,snd_pcm
output                  1883  1 video
lp                      7342  0 
parport                31492  3 parport_pc,ppdev,lp
ahci                   19198  1 
libahci                21664  1 ahci
atl1c                  29949  0 

```

Anyway, my wireless works right away when I boot up, but when the laptop wakes from resume and grabs a connection, pages won't load.  I have to manually disconnect and reconnect every time to get internet access.  Anyone know of a fix or have ideas for a script to run on resume to automate this?

---

