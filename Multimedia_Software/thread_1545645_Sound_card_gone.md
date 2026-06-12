---
title: "Sound card gone"
date: 2010-08-04
forum: Multimedia Software
---

### Post by Orlando84 on 2010-08-04
Hi all Ubuntians!
I've got a trouble with my sound card. I'd like to tell the actions I did that made my sound card seems to be "broken". I've plugged earphones, than noticed that sound is still going through laptop dynamics. I went to System->Sound, and on one of the tabs changed sound output from "speakers " to "earphones". Everything looked fine until my laptop hanged. I rebooted it with pressing and holding "power" button. When it loaded the Ubuntu system I've noticed that there were no system sounds, then I went to System->sound to check the trouble and saw that there was no device at all (on the devices tab). lspci says that card is OK
```
lspci
``````
00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)
```So help me please to make my sound card working again.

P.S. I don't even know which I'm running: Pulse Audio or ALSA

---

### Post by Orlando84 on 2010-08-04
This is output of ```
lsmod
``````
Module                  Size  Used by
binfmt_misc             8356  1 
ppdev                   6688  0 
arc4                    1660  2 
ecb                     2524  2 
ath5k                 124260  0 
mac80211              181236  1 ath5k
ath                     8060  1 ath5k
lp                      8964  0 
snd_hda_codec_realtek   203328  1 
snd_hda_codec_si3054     4636  1 
snd_hda_intel          26920  0 
snd_hda_codec          75708  3 snd_hda_codec_realtek,snd_hda_codec_si3054,snd_hda_intel
snd_hwdep               7200  1 snd_hda_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  4 snd_hda_codec_si3054,snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           2656  0 
snd_seq_oss            28576  0 
snd_seq_midi            6432  0 
snd_rawmidi            22208  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    59204  13 snd_hda_codec_realtek,snd_hda_codec_si3054,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
cfg80211               93052  3 ath5k,mac80211,ath
soundcore               7264  1 snd
parport                35340  2 ppdev,lp
snd_page_alloc          9156  2 snd_hda_intel,snd_pcm
iptable_filter          3100  0 
ip_tables              11692  1 iptable_filter
x_tables               16544  1 ip_tables
joydev                 10272  0 
mmc_block              10592  0 
pcmcia                 36808  0 
yenta_socket           24200  1 
sdhci_pci               7100  0 
rsrc_nonstatic         11644  1 yenta_socket
sdhci                  17472  1 sdhci_pci
led_class               4096  2 ath5k,sdhci
pcmcia_core            35792  3 pcmcia,yenta_socket,rsrc_nonstatic
psmouse                56180  0 
i2c_piix4               9932  0 
serio_raw               5280  0 
shpchp                 32272  0 
ricoh_mmc               3676  0 
hid_a4tech              2652  0 
usbhid                 38208  0 
8139too                22620  0 
8139cp                 19260  0 
mii                     5212  2 8139too,8139cp
video                  19380  0 
output                  2780  1 video
radeon                636000  2 
ttm                    36212  1 radeon
drm                   159584  4 radeon,ttm
i2c_algo_bit            5760  1 radeon
ati_agp                 6760  0 
agpgart                34988  3 ttm,drm,ati_agp
```

---

