---
title: "Line-Out not working on S6410"
date: 2008-10-25
forum: Multimedia Software
---

### Post by gangsterchen on 2008-10-25
Hi,

I've got a Fujitsu Siemens S6410 Notebook with a 
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)

loaded kernel modules:
```
acid@natalie ~ $ lsmod | grep hd
snd_hda_intel         344728  4 
snd_pcm                78596  2 snd_hda_intel,snd_pcm_oss
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
snd_hwdep              10500  1 snd_hda_intel
snd                    56996  19 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
acid@natalie ~ $ 
```


The sound is working perfectly with the integrated speakers, but not over the Line-Out.

I've activated everything over the Mixer applet from gnome, playing around with alsa-mixer and "m" doesn't help.

Is there a known bug or do you know something that can help?

greetz

gangsterchen

---

### Post by gangsterchen on 2008-10-27
push

---

