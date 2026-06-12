---
title: "upgrade from 9.04 to 9.10 = no sound"
date: 2010-01-30
forum: Mythbuntu
---

### Post by diskmaster23 on 2010-01-30
Okay, I have been searching for solution all morning through the forums, but I have not been able to find a solution to get my sound working.

Here are my outputs
aplay -l output
```

aplay: device_list:223: no soundcards found..
```

lspci output
```

00:00.0 Host bridge: nVidia Corporation nForce3 250Gb Host Bridge (rev a1)
00:01.0 ISA bridge: nVidia Corporation nForce3 250Gb LPC Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation nForce 250Gb PCI System Management (rev a1)
00:02.0 USB Controller: nVidia Corporation CK8S USB Controller (rev a1)
00:02.1 USB Controller: nVidia Corporation CK8S USB Controller (rev a1)
00:02.2 USB Controller: nVidia Corporation nForce3 EHCI USB 2.0 Controller (rev a2)
00:05.0 Bridge: nVidia Corporation CK8S Ethernet Controller (rev a2)
00:08.0 IDE interface: nVidia Corporation CK8S Parallel ATA Controller (v2.5) (rev a2)
00:0a.0 IDE interface: nVidia Corporation nForce3 Serial ATA Controller (rev a2)
00:0b.0 PCI bridge: nVidia Corporation nForce3 250Gb AGP Host to PCI Bridge (rev a2)
00:0e.0 PCI bridge: nVidia Corporation nForce3 250Gb PCI-to-PCI Bridge (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: nVidia Corporation NV44A [GeForce 6200] (rev a1)
02:06.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 07)
02:06.1 Input device controller: Creative Labs SB Live! Game Port (rev 07)
02:07.0 Multimedia video controller: Internext Compression Inc iTVC16 (CX23416) MPEG-2 Encoder (rev 01)
02:09.0 RAID bus controller: Silicon Image, Inc. SiI 3114 [SATALink/SATARaid] Serial ATA Controller (rev 02)
02:0b.0 Ethernet controller: Marvell Technology Group Ltd. 88E8001 Gigabit Ethernet Controller (rev 13)
02:0d.0 RAID bus controller: Silicon Image, Inc. SiI 3512 [SATALink/SATARaid] Serial ATA Controller (rev 01)

```

lsmod output
```
Module                  Size  Used by
vboxnetadp             14272  0 
vboxnetflt             22416  0 
vboxdrv              1792940  2 vboxnetadp,vboxnetflt
cx8800                 45036  0 
cx88xx                 88104  1 cx8800
videobuf_dvb           16516  1 cx88xx
dvb_core              106924  1 videobuf_dvb
bttv                  214100  0 
ir_common              56068  2 cx88xx,bttv
videobuf_dma_sg        22660  3 cx8800,cx88xx,bttv
videobuf_core          29828  5 cx8800,cx88xx,videobuf_dvb,bttv,videobuf_dma_sg
btcx_risc              13960  3 cx8800,cx88xx,bttv
lirc_i2c               18948  0 
lirc_dev               22088  1 lirc_i2c
nfsd                  285728  13 
auth_rpcgss            52512  1 nfsd
exportfs               13440  1 nfsd
snd_emu10k1_synth      15488  0 
nfs                   304848  0 
snd_emux_synth         46208  1 snd_emu10k1_synth
snd_seq_virmidi        14464  1 snd_emux_synth
lockd                  83924  2 nfsd,nfs
nfs_acl                11776  2 nfsd,nfs
snd_seq_midi_emul      16000  1 snd_emux_synth
snd_emu10k1           162720  1 snd_emu10k1_synth
snd_ac97_codec        133848  1 snd_emu10k1
ac97_bus               10368  1 snd_ac97_codec
snd_pcm_oss            52352  0 
snd_mixer_oss          24960  1 snd_pcm_oss
tuner_simple           24084  1 
tuner_types            26240  1 tuner_simple
snd_pcm                99464  3 snd_emu10k1,snd_ac97_codec,snd_pcm_oss
wm8775                 15020  0 
snd_page_alloc         18704  2 snd_emu10k1,snd_pcm
snd_util_mem           13184  2 snd_emux_synth,snd_emu10k1
snd_hwdep              16776  2 snd_emux_synth,snd_emu10k1
cx25840                38320  0 
snd_seq_dummy          11524  0 
snd_seq_oss            41984  0 
tuner                  36036  0 
snd_seq_midi           15744  0 
emu10k1_gp             11520  0 
snd_rawmidi            33920  3 snd_seq_virmidi,snd_emu10k1,snd_seq_midi
ivtv                  168644  4 
compat_ioctl32         18304  3 cx8800,bttv,ivtv
i2c_algo_bit           15364  3 cx88xx,bttv,ivtv
cx2341x                22148  1 ivtv
v4l2_common            23296  7 cx8800,bttv,wm8775,cx25840,tuner,ivtv,cx2341x
videodev               45184  6 cx8800,cx88xx,bttv,tuner,ivtv,compat_ioctl32
v4l1_compat            23940  1 videodev
snd_seq_midi_event     16512  3 snd_seq_virmidi,snd_seq_oss,snd_seq_midi
snd_seq                66272  9 snd_emux_synth,snd_seq_virmidi,snd_seq_midi_emul,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              34064  3 snd_emu10k1,snd_pcm,snd_seq
snd_seq_device         16276  8 snd_emu10k1_synth,snd_emux_synth,snd_emu10k1,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    78920  13 snd_emux_synth,snd_seq_virmidi,snd_emu10k1,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
iptable_filter         11392  0 
sunrpc                227304  16 nfsd,auth_rpcgss,nfs,lockd,nfs_acl
gameport               21648  2 emu10k1_gp
soundcore              16800  1 snd
ip_tables              28304  1 iptable_filter
tveeprom               23428  3 cx88xx,bttv,ivtv
nvidia              10324264  34 
ppdev                  16904  0 
lp                     19588  0 
i2c_nforce2            16136  0 
shpchp                 44572  0 
x_tables               31624  1 ip_tables
k8temp                 13440  0 
parport_pc             45096  1 
xfs                   568592  1 
parport                49584  3 ppdev,lp,parport_pc
raid10                 32000  0 
raid1                  32640  0 
raid0                  15616  0 
multipath              16512  0 
linear                 13440  0 
raid456               140064  1 
async_xor              12160  1 raid456
async_memcpy           10752  1 raid456
async_tx               16636  3 raid456,async_xor,async_memcpy
xor                    13968  2 raid456,async_xor
usbhid                 47040  0 
skge                   54032  0 
forcedeth              68368  0 

```

alsamixer, tried running it, but I get this
```
alsamixer: function snd_ctl_open failed for default: No such file or directory

```

Any suggestions?

---

