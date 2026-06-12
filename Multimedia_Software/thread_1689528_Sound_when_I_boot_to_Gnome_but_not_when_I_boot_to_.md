---
title: "Sound when I boot to Gnome but not when I boot to text mode"
date: 2011-02-16
forum: Multimedia Software
---

### Post by VoiDeR on 2011-02-16
I have Ubuntu 10.10 installed with xbmc. If I boot up to Gnome my sound works fine. If I boot to text mode and start xbmc via startx I don't have any sound. Im not sure where to start with this. Does gnome start some extra service that enable sound?

Sound card
```
00:08.0 Audio device: nVidia Corporation MCP79 High Definition Audio (rev b1)
```

Modules
```
parport_pc             26058  0 
ppdev                   5556  0 
nvidia               9329739  38 
snd_hda_codec_nvhdmi    12879  1 
snd_hda_codec_via      51755  1 
binfmt_misc             6599  1 
snd_hda_intel          22107  0 
snd_hda_codec          87552  3 snd_hda_codec_nvhdmi,snd_hda_codec_via,snd_hda_intel
snd_hwdep               5040  1 snd_hda_codec
snd_pcm                71475  2 snd_hda_intel,snd_hda_codec
snd_seq_midi            4588  0 
snd_rawmidi            17783  1 snd_seq_midi
ir_lirc_codec           3092  3 
lirc_dev                9393  1 ir_lirc_codec
snd_seq_midi_event      6047  1 snd_seq_midi
ir_sony_decoder         1889  0 
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
ir_jvc_decoder          1950  0 
ir_rc6_decoder          2334  0 
ir_rc5_decoder          1950  0 
snd_timer              19067  2 snd_pcm,snd_seq
rc_rc6_mce              1146  0 
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
ir_nec_decoder          2014  0 
shpchp                 29886  0 
mceusb                 11494  0 
psmouse                59033  0 
ir_core                14654  9 ir_lirc_codec,ir_sony_decoder,ir_jvc_decoder,ir_rc6_decoder,ir_rc5_decoder,rc_rc6_mce,ir_nec_decoder,mceusb
serio_raw               4022  0 
snd                    49006  9 snd_hda_codec_via,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore                880  1 snd
agpgart                32011  1 nvidia
snd_page_alloc          7120  2 snd_hda_intel,snd_pcm
i2c_nforce2             5179  0 
lp                      7342  0 
parport                31492  3 parport_pc,ppdev,lp
ahci                   19013  0 
forcedeth              49433  0 
libahci                21667  3 ahci

```

Let me know if you need more info.

---

