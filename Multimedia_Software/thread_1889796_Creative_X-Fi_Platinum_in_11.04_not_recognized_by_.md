---
title: "Creative X-Fi Platinum in 11.04 not recognized by ALSA"
date: 2011-12-02
forum: Multimedia Software
---

### Post by wsexson on 2011-12-02
I am trying to get an X-Fi Platinum sound card to work in Ubuntu 11.04 (64 bit) and ALSA doesn't recognize it as a sound device.

lspci tells me


```
01:08.0 VGA compatible unclassified device: Creative Labs SB X-Fi
	Subsystem: Creative Labs X-Fi Platinum
	Flags: medium devsel, IRQ 16
	I/O ports at cc00 [size=32]
	Memory at 80200000 (64-bit, non-prefetchable) [size=2M]
	Memory at 88000000 (64-bit, non-prefetchable) [size=128M]
	Capabilities: [40] Power Management version 2
	Capabilities: [50] MSI: Enable- Count=1/1 Maskable- 64bit+
	Kernel modules: snd-ctxfi
```

lsmod shows

```
Module                  Size  Used by
snd_seq_midi           13324  0 
snd_rawmidi            30434  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                65527  2 snd_seq_midi,snd_seq_midi_event
snd_seq_device         14498  3 snd_seq_midi,snd_rawmidi,snd_seq
snd_ctxfi             104755  0 
binfmt_misc            17565  1 
vboxnetadp             13340  0 
vboxnetflt             28297  0 
vboxdrv               252684  2 vboxnetadp,vboxnetflt
vesafb                 13761  1 
snd_hda_codec_realtek   359097  1 
arc4                   12529  2 
snd_hda_intel          32922  2 
nvidia              10709116  28 
snd_hda_codec         112255  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13604  1 snd_hda_codec
snd_pcm               100349  3 snd_ctxfi,snd_hda_intel,snd_hda_codec
ath5k                 155466  0 
ath                    23773  1 ath5k
ppdev                  17113  0 
mac80211              294370  1 ath5k
snd_timer              29395  2 snd_seq,snd_pcm
snd                    78151  16 snd_seq_midi,snd_rawmidi,snd_seq_midi_event,snd_seq,snd_seq_device,snd_ctxfi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_timer
joydev                 17606  0 
soundcore              12680  1 snd
cfg80211              178528  3 ath5k,ath,mac80211
psmouse                73535  0 
edac_core              53845  0 
serio_raw              13166  0 
k8temp                 13016  0 
lp                     17825  0 
edac_mce_amd           23464  0 
parport_pc             36959  1 
snd_page_alloc         18484  3 snd_ctxfi,snd_hda_intel,snd_pcm
parport                46458  3 ppdev,lp,parport_pc
i2c_nforce2            13058  0 
hid_logitech           17693  0 
ff_memless             13097  1 hid_logitech
usbhid                 46956  1 hid_logitech
hid                    91020  2 hid_logitech,usbhid
floppy                 74120  0 
raid10                 30673  0 
raid456                62777  0 
async_pq               12995  1 raid456
async_xor              12879  2 raid456,async_pq
xor                    12890  1 async_xor
async_memcpy           12529  1 raid456
async_raid6_recov      12776  1 raid456
sata_nv                32054  16 
forcedeth              63555  0 
pata_amd               14130  0 
raid6_pq               88307  2 async_pq,async_raid6_recov
async_tx               13349  5 raid456,async_pq,async_xor,async_memcpy,async_raid6_recov
raid1                  30596  7 
raid0                  17271  0 
multipath              13187  0 
linear                 12966  0
``` 

Is "VGA compatible unclassified device" part of my problem, and if it is can anyone suggest a workaround?

---

### Post by terran4000 on 2011-12-13
In 11.04 I have the solution: [http://www.piotrkrzyzek.com/creative-x-fi-titanium-5-1-digital-surround-on-ubuntu/](http://www.piotrkrzyzek.com/creative-x-fi-titanium-5-1-digital-surround-on-ubuntu/)

Problem is, when I wrote that it was ONLY for 11.04 and under. 11.10 is still borked. :(

Good luck.

---

