---
title: "avermedia dvb-s card problem"
date: 2011-05-22
forum: Multimedia Software
---

### Post by emreugur on 2011-05-22
hello;

i have been tried all day long with avermedia dvb-s card and couldn't make dvb active.

as sure , dear pals you will ask me , lspci , modprobe etc.



lspci -vvnn

```

03:06.0 Multimedia controller [0480]: Philips Semiconductors SAA7131/SAA7133/SAA7135 Video Broadcast Decoder [1131:7133] (rev d1)
    Subsystem: Avermedia Technologies Inc Device [1461:2155]
    Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR+ FastB2B- DisINTx-
    Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR- INTx-
    Latency: 64
    Interrupt: pin A routed to IRQ 20
    Region 0: Memory at febff800 (32-bit, non-prefetchable) [size=2K]
    Capabilities: [40] Power Management version 2
        Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0-,D1-,D2-,D3hot-,D3cold-)
        Status: D0 NoSoftRst- PME-Enable- DSel=0 DScale=0 PME-
    Kernel driver in use: saa7134
    Kernel modules: saa7134

```lsmod

```
Module                  Size  Used by
snd_hda_codec_via      56765  1 
saa7134_alsa           18130  0 
snd_hda_intel          24140  0 
snd_hda_codec          90901  2 snd_hda_codec_via,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80244  3 saa7134_alsa,snd_hda_intel,snd_hda_codec
radeon                896428  2 
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
ttm                    65184  1 radeon
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
drm_kms_helper         40745  1 radeon
saa7134               149236  1 saa7134_alsa
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
ppdev                  12849  0 
drm                   180037  4 radeon,ttm,drm_kms_helper
v4l2_common            16757  1 saa7134
videodev               75143  2 saa7134,v4l2_common
i2c_algo_bit           13184  1 radeon
videobuf_dma_sg        18747  2 saa7134_alsa,saa7134
psmouse                73312  0 
parport_pc             32111  1 
asus_atk0110           17664  0 
videobuf_core          25193  2 saa7134,videobuf_dma_sg
snd                    55295  10 snd_hda_codec_via,saa7134_alsa,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
tveeprom               17009  1 saa7134
serio_raw              12990  0 
ir_lirc_codec          12770  0 
lirc_dev               18720  1 ir_lirc_codec
soundcore              12600  1 snd
sp5100_tco             13456  0 
k10temp                12951  0 
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
ir_sony_decoder        12493  0 
shpchp                 32345  0 
dm1105                 17844  0 
i2c_piix4              13095  0 
ir_jvc_decoder         12490  0 
ir_rc6_decoder         12490  0 
dvb_core               90587  1 dm1105
ir_rc5_decoder         12490  0 
ir_nec_decoder         12490  0 
rc_core                25760  8 saa7134,ir_lirc_codec,ir_sony_decoder,dm1105,ir_jvc_decoder,ir_rc6_decoder,ir_rc5_decoder,ir_nec_decoder
joydev                 17322  0 
lp                     13349  0 
parport                36746  3 ppdev,parport_pc,lp
usbhid                 41704  0 
hid                    77084  1 usbhid
ahci                   21591  0 
libahci                25548  1 ahci
atl1c                  36237  0 
pata_atiixp            12968  2 

```for any help appriciated.

thanks.

---

