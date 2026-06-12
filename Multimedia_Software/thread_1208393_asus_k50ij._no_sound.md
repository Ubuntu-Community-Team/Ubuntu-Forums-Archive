---
title: "asus k50ij. no sound"
date: 2009-07-09
forum: Multimedia Software
---

### Post by Squier13 on 2009-07-09
hello. asus k50ij + ubuntu 9.04 = no sound...
I install alsa 1.0.20 for hda-intel ([faq (rus)]("https://wiki.ubuntu.com/RussianDocumentation/AlsaHda-intel"))

```
$ lsmod | grep snd
snd_hda_codec_via      36352  1 
snd_hda_intel          35808  1 
snd_hda_codec          86016  2 snd_hda_codec_via,snd_hda_intel
snd_hwdep              15364  1 snd_hda_codec
snd_pcm_oss            46208  0 
snd_mixer_oss          22912  1 snd_pcm_oss
snd_pcm                83588  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy          10884  0 
snd_seq_oss            36096  0 
snd_seq_midi           14336  0 
snd_rawmidi            30080  1 snd_seq_midi
snd_seq_midi_event     15232  2 snd_seq_oss,snd_seq_midi
snd_seq                57520  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              29192  2 snd_pcm,snd_seq
snd_seq_device         15244  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    67108  14 snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              15200  1 snd
snd_page_alloc         17032  2 snd_hda_intel,snd_pcm

```

```
$ lspci | grep Audio
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)

```

At installation alsa has left alsa-base.conf(delete), but has appeared 50-sound.conf.

help me... sorry, badly I speak English

---

### Post by Squier13 on 2009-07-10
f.a.q's?

---

### Post by Squier13 on 2009-07-12
```
sudo -s
wget ftp://ftp.kernel.org/pub/linux/kernel/people/tiwai/misc/hda-verb/hda-verb-0.3.tar.gz
tar xf hda-verb-0.3.tar.gz
cd hda-verb-0.3
make
cp hda-verb /usr/bin
hda-verb /dev/snd/hwC0D0 0x1c SET_EAPD_BTLENABLE PCM
```
and
```
sudo -s
wget ftp://ftp.kernel.org/pub/linux/kernel/people/tiwai/snapshot/alsa-driver-unstable-snapshot.tar.gz
tar xf alsa-driver-unstable-snapshot.tar.gz
cd alsa-driver-unstable
./configure --with-cards=hda-intel
make
make install
reboot
```

Thanks. Can to whom will help:p

---

