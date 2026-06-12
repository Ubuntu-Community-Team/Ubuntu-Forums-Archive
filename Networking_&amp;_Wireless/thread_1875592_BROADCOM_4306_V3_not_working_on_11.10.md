---
title: "BROADCOM 4306 V3 not working on 11.10"
date: 2011-11-05
forum: Networking &amp; Wireless
---

### Post by TheFonz on 2011-11-05
```

02:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5705M Gigabit Ethernet [14e4:165d] (rev 01)
02:03.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11a/b/g [14e4:4324] (rev 03)

```

```

rolando@Virgo:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

```
```

rolando@Virgo:~$ lsmod
Module                  Size  Used by
bnep                   17923  2 
rfcomm                 38408  0 
bluetooth             148839  10 bnep,rfcomm
arc4                   12473  0 
joydev                 17393  0 
snd_intel8x0           33318  2 
snd_ac97_codec        106082  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80468  2 snd_intel8x0,snd_ac97_codec
ppdev                  12849  0 
snd_seq_midi           13132  0 
snd_rawmidi            25241  1 snd_seq_midi
radeon                925020  2 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
dcdbas                 14098  0 
mac80211              272785  0 
pcmcia                 39822  0 
snd_timer              28932  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    55902  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ttm                    65224  1 radeon
cfg80211              172392  1 mac80211
drm_kms_helper         32889  1 radeon
drm                   192226  4 radeon,ttm,drm_kms_helper
psmouse                73673  0 
soundcore              12600  1 snd
yenta_socket           27428  0 
pcmcia_rsrc            18367  1 yenta_socket
snd_page_alloc         14115  2 snd_intel8x0,snd_pcm
serio_raw              12990  0 
pcmcia_core            21511  3 pcmcia,yenta_socket,pcmcia_rsrc
binfmt_misc            17292  1 
i2c_algo_bit           13199  1 radeon
video                  18908  0 
parport_pc             32114  1 
shpchp                 32356  0 
lp                     17455  0 
parport                40930  3 ppdev,parport_pc,lp
ssb                    50682  0 
tg3                   132972  0 

```

I tried to install the firmware-b43-installer and this yields an error saying found an incompatible card to use the b43legacy-installer, but that one says the same.  Any help is appreciated....

---

