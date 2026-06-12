---
title: "No surround: All sounds from center speaker"
date: 2013-02-11
forum: Multimedia Software
---

### Post by just1ce on 2013-02-11
Hi!

I have my PC connected to my reciever through an HDMI cable. The reciever and speakers are set up just fine (other systems can play sounds correctly). When I try to play through this computer though, all sounds end up playing (with a crackly sound) in the center speaker.

lspci:
>  00:1b.0 Audio device: Intel Corporation Panther Point High Definition Audio Controller (rev 04 

lsmod | grep snd:
> snd_hda_codec_hdmi 32474 1
snd_hda_codec_realtek 224173 1
snd_hda_intel 33773 3
snd_hda_codec 127706 3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_i ntel
snd_hwdep 17764 1 snd_hda_codec
snd_pcm 97275 3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi 13324 0
snd_rawmidi 30748 1 snd_seq_midi
snd_seq_midi_event 14899 1 snd_seq_midi
snd_seq 61929 2 snd_seq_midi,snd_seq_midi_event
snd_timer 29990 2 snd_pcm,snd_seq
snd_seq_device 14540 3 snd_seq_midi,snd_rawmidi,snd_seq
snd 79041 16 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_i ntel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,s nd_seq,snd_timer,snd_seq_device
soundcore 15091 1 snd
snd_page_alloc 18529 2 snd_hda_intel,snd_pcm
dennis@ubuntu:~$ lsmod | grep snd
snd_hda_codec_hdmi 32474 1
snd_hda_codec_realtek 224173 1
snd_hda_intel 33773 3
snd_hda_codec 127706 3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_i ntel
snd_hwdep 17764 1 snd_hda_codec
snd_pcm 97275 3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi 13324 0
snd_rawmidi 30748 1 snd_seq_midi
snd_seq_midi_event 14899 1 snd_seq_midi
snd_seq 61929 2 snd_seq_midi,snd_seq_midi_event
snd_timer 29990 2 snd_pcm,snd_seq
snd_seq_device 14540 3 snd_seq_midi,snd_rawmidi,snd_seq
snd 79041 16 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_i ntel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,s nd_seq,snd_timer,snd_seq_device
soundcore 15091 1 snd
snd_page_alloc 18529 2 snd_hda_intel,snd_pcm 

Even though the card is supposed to manage a 7.1 system, the only option I have in pavucontrol is "Digital Stereo (HDMI) Output". There's no "Digital Surround", as I had expected.

I also noticed something stranged when playing a sound and using alsamixer. The sound is only affected by muting/unmuting the "S/PDIF 1" thingy. Not even master affects it!

What do I have to do to enable surround sound?

---

