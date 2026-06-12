---
title: "HP Pavalion DV6 sound issue"
date: 2009-09-15
forum: Multimedia Software
---

### Post by Achayaan on 2009-09-15
Hi all

Please help me to getting sound in my HP Pavilion DV6 1260 . I followed [https://help.ubuntu.com/community/Sound](https://help.ubuntu.com/community/Sound) and i done everything told here [http://monespaceperso.org/blog-en/2009/08/31/upgrade-alsa-1-0-21-on-ubuntu-jaunty-9-04/](http://monespaceperso.org/blog-en/2009/08/31/upgrade-alsa-1-0-21-on-ubuntu-jaunty-9-04/)
and still i done have any sound from my laptop :( except sound everything is working :(
please help me to solve this issue

and here is tthe alsa output 

[http://pastebin.ca/1567358](http://pastebin.ca/1567358)

and 

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

and 

/usr/sbin/alsactl
snd_hda_codec_atihdmi    11520  1 
snd_hda_codec_idt      65160  1 
snd_hda_intel          35712  3 
snd_hda_codec          87168  3 snd_hda_codec_atihdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              15364  1 snd_hda_codec
snd_pcm_oss            45984  0 
snd_mixer_oss          22912  1 snd_pcm_oss
snd_pcm                83716  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_oss            36224  0 
snd_seq_midi_event     15232  1 snd_seq_oss
snd_seq                57584  4 snd_seq_oss,snd_seq_midi_event
snd_timer              29192  2 snd_pcm,snd_seq
snd_seq_device         15372  2 snd_seq_oss,snd_seq
snd                    67236  17 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_seq,snd_timer,snd_seq_device
soundcore              15200  1 snd
snd_page_alloc         17032  2 snd_hda_intel,snd_pcm

and if you want any more info i can send it

please help me

thanks:popcorn:

---

### Post by Achayaan on 2009-09-15
plzzz help me :(

---

### Post by Achayaan on 2009-09-16
still i am waiting :(

---

### Post by web032009 on 2009-09-16
try this one

gksudo gedit /etc/modprobe.d/alsa-base.conf

add this option

options snd slots=snd-hda-intel,snd-hda-inte
alias sounds-slot-0 snd-hda-intel
options snd-hda-intel model=dell-m4-1
options snd-hda-intel enable_msi=1

---

### Post by Achayaan on 2009-09-16
thanks web , I tried that but there is no hope :(

---

