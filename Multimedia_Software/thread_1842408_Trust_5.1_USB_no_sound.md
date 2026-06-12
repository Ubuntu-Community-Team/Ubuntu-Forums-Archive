---
title: "Trust 5.1 USB no sound"
date: 2011-09-11
forum: Multimedia Software
---

### Post by Sirserega on 2011-09-11
Hello, i have installed ubuntu 11.04 yesterday, but my soundcard is not working on this version. I really dont know why becouse on 10.10 was work correctly. Please help me. 

**[B]lsmod | grep snd**[/B]

```
snd_hda_codec_hdmi     28103  4 
snd_hda_intel          33211  0 
snd_hda_codec         103804  2 snd_hda_codec_hdmi,snd_hda_intel
snd_usb_audio         112426  2 
snd_pcm                96625  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_usb_audio
snd_hwdep              13604  2 snd_hda_codec,snd_usb_audio
snd_usbmidi_lib        25139  1 snd_usb_audio
snd_seq_midi           13324  0 
snd_rawmidi            30486  2 snd_usbmidi_lib,snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61621  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29602  2 snd_pcm,snd_seq
snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    67382  15 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_usb_audio,snd_pcm,snd_hwdep,snd_usbmidi_lib,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm

```

**[B]cat /proc/asound/cards **
[/B]
```
  0 [NVidia         ]: HDA-Intel - HDA NVidia
                      HDA NVidia at 0xfa080000 irq 17
 1 [Audio          ]: USB-Audio - USB Audio
                      USB Audio at usb-0000:05:00.0-3, full speed
```

P.S. I'm so sorry about my english.

---

