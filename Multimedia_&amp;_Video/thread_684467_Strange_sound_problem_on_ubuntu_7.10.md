---
title: "Strange sound problem on ubuntu 7.10"
date: 2008-02-01
forum: Multimedia &amp; Video
---

### Post by czah on 2008-02-01
Hello,

the situations is the the sound I have is a bad quality sound, I can hardly hear the lower tones, bass is gone, I can say. I tried with equalizer, on amarok or xmms. Other strange things I noticed is that when I run alsamixer or alsamixergui the PCM settings has no influence on volume level. The one that works is "Front". I tried alsaconf , no changes...  This is all happening on ubuntu 7.10, earlier, on .06 I had no problems, sound was really good. I'm using only headphones (KOSS with no bass, terrible) , another things is that I lost singal on front jack, I had to plug the cable on rear green jack...

what's wrong?

cat /proc/asound/card0/codec#* | grep Codec
Codec: Realtek ALC260

 lsmod|grep snd
snd_hda_intel         291488  0 
snd_pcm_oss            43008  0 
snd_mixer_oss          17664  1 snd_pcm_oss
snd_pcm                80004  2 snd_hda_intel,snd_pcm_oss
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
snd_hwdep              10244  1 snd_hda_intel
snd_seq_dummy           4740  0 
snd_seq_oss            33152  0 
snd_seq_midi            9600  0 
snd_rawmidi            25728  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                53360  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24324  2 snd_pcm,snd_seq
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    54788  10 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd

---

### Post by linuxwizard on 2008-02-03
Look over this 

[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

---

