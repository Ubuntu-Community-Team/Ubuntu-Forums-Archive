---
title: "AliveNF7G-GLAN"
date: 2010-05-01
forum: Multimedia Software
---

### Post by bernd_b on 2010-05-01
Hello,

I have just installed ubuntu 10.4 using the mainboard AliveNF7G-GLAN by Asrock.

So far no sound at all.

The manual says it has al ALC662 Audio Chip.

Has anyone this board running with sound? 

Or is there any suggestions how I can track down the problem?

lsmod looks right to me:

```
Module                  Size  Used by
snd_hda_codec_realtek   278890  1 
nfs                   310131  0 
lockd                  75015  1 nfs
nfs_acl                 2709  1 nfs
auth_rpcgss            44452  1 nfs
sunrpc                227939  5 nfs,lockd,nfs_acl,auth_rpcgss
fbcon                  39270  71 
tileblit                2487  1 fbcon
font                    8053  1 fbcon
bitblit                 5811  1 fbcon
softcursor              1565  1 bitblit
vga16fb                12757  0 
vgastate                9857  1 vga16fb
snd_hda_intel          25645  2 
snd_hda_codec          85727  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               6924  1 snd_hda_codec
snd_pcm_oss            41394  0 
snd_mixer_oss          16299  1 snd_pcm_oss
snd_pcm                87850  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1782  0 
snd_seq_oss            31219  0 
snd_seq_midi            5829  0 
snd_rawmidi            23388  1 snd_seq_midi
snd_seq_midi_event      7267  2 snd_seq_oss,snd_seq_midi
snd_seq                57417  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
w83627ehf              23314  0 
snd_timer              23553  2 snd_pcm,snd_seq
snd_seq_device          6824  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
nouveau               515131  2 
ppdev                   6375  0 
ttm                    60815  1 nouveau
drm_kms_helper         30742  1 nouveau
hwmon_vid               3130  1 w83627ehf
edac_core              45423  0 
edac_mce_amd            9214  0 
snd                    70978  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
k8temp                  3912  0 
drm                   198770  4 nouveau,ttm,drm_kms_helper                                                                                                                          
i2c_algo_bit            6024  1 nouveau                                                                                                                                             
parport_pc             29958  1                                                                                                                                                     
soundcore               8052  1 snd                                                                                                                                                 
snd_page_alloc          8500  2 snd_hda_intel,snd_pcm                                                                                                                               
lp                      9336  0                                                                                                                                                     
i2c_nforce2             6099  0                                                                                                                                                     
parport                37160  3 ppdev,parport_pc,lp                                                                                                                                 
usbhid                 40988  0                                                                                                                                                     
hid                    83376  1 usbhid                                                                                                                                              
ahci                   37646  0                                                                                                                                                     
forcedeth              55592  0                                                                                                                                                     
pata_amd               11962  4 
```

---

### Post by bernd_b on 2010-05-02
Sorry for making noise.

After some sleep (it got late ...) I discovered today, that there is(!) sound - but only out of the front panel .....:popcorn::-#:-k:-?

---

