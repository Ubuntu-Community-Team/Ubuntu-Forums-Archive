---
title: "Alsaconf won't detect soundcard"
date: 2010-01-02
forum: Multimedia Software
---

### Post by Arkitekt on 2010-01-02
I manually compiled the 1.0.22 Alsa drivers a couple of weeks ago as my netbook didn't seem to agree with the 1.0.18 drivers that come with Jaunty. 

For some reason after every restart I have to run alsaconf and configure my soundcard for sound to properly output using alsa. The other day while running alsaconf my son managed to restart my netbook, now when running alsaconf I get a message saying that it cannot detect any PnP or PCI cards and asks if I would like to search for legacy cards.

How can I get my soundcard to work again? do I need to update to 9.10 or just re-compile the 1.0.22 drivers? I haven't upgraded to 9.10 yet as I like the launcher on 9.04.

output for lspci | grep Audio is

```
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)

```

output for lsmod | grep snd is

```
snd_hda_codec_idt      63496  1 
snd_hda_intel          36480  3 
snd_hda_codec          92928  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              15364  1 snd_hda_codec
snd_pcm_oss            45984  0 
snd_mixer_oss          22912  1 snd_pcm_oss
snd_pcm                83972  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy          10884  0 
snd_seq_oss            36224  0 
snd_seq_midi           14496  0 
snd_rawmidi            29984  1 snd_seq_midi
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
snd_seq                57584  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29192  2 snd_pcm,snd_seq
snd_seq_device         15372  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    68260  20 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15200  1 snd
snd_page_alloc         17032  2 snd_hda_intel,snd_pcm

```

---

### Post by Arkitekt on 2010-01-03
can someone help me please?

---

