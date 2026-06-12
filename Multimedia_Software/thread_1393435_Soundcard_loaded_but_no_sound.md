---
title: "Soundcard loaded but no sound"
date: 2010-01-29
forum: Multimedia Software
---

### Post by Bjartur on 2010-01-29
Hi, I don't hear any sound from my computer.
Trying to play raw files with aplay or mpg123 doesn't work, nor did playing a real sound file.

The sound card is loaded:
$aplay * & sleep 1 && cat /proc/asound/modules
0 snd_ens1371
$ lsmod | grep snd
snd_seq_dummy           2656  0 
snd_seq_oss            28576  0 
snd_seq_midi            6432  0 
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_pcm_oss            37920  1 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_ens1371            22016  1 
gameport               11368  1 snd_ens1371
snd_ac97_codec        101216  1 snd_ens1371
ac97_bus                1532  1 snd_ac97_codec
snd_pcm                75296  3 snd_pcm_oss,snd_ens1371,snd_ac97_codec
snd_rawmidi            22208  2 snd_seq_midi,snd_ens1371
snd_timer              22276  2 snd_seq,snd_pcm
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq,snd_rawmidi
snd                    59204  10 snd_seq_oss,snd_seq,snd_pcm_oss,snd_mixer_oss,snd_ens1371,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_timer,snd_seq_device
soundcore               7264  2 snd
snd_page_alloc          9156  1 snd_pcm

I could hear beeps in an old version of Ubuntu (8.10 IIRC) but after upgrading to 9.10 I don't even hear that.

$alsa reload
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/sm/.gvfs
      Output information may be incomplete.
/sbin/alsa: Warning: Processes using sound devices: 1584(pulseaudio). 
Unloading ALSA sound driver modules: snd-ens1371 snd-pcm-oss snd-mixer-oss snd-ac97-codec snd-seq-dummy snd-pcm snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device snd-page-alloc (failed: modules still loaded: snd-ens1371 snd-ac97-codec snd-pcm snd-rawmidi snd-timer snd-seq-device snd-page-alloc).
Loading ALSA sound driver modules: snd-ens1371 snd-pcm-oss snd-mixer-oss snd-ac97-codec snd-seq-dummy snd-pcm snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device snd-page-alloc.

So Pulseaudio is up and running. But wait, I need GVFS?!! WTF?! :confused: Hope it's just for debugging... 

$cat /proc/asound/oss/sndstat 
Sound Driver:3.8.1a-980706 (ALSA v1.0.20 emulation code)
Kernel: Linux bikkjan 2.6.31-17-generic #54-Ubuntu SMP Thu Dec 10 16:20:31 UTC 2009 i686
Config options: 0

Installed drivers: 
Type 10: ALSA emulation

Card config: 
Ensoniq AudioPCI ENS1371 at 0x1000, irq 17

Audio devices:
0: ES1371 DAC2/ADC (DUPLEX)

Synth devices: NOT ENABLED IN CONFIG

Midi devices:
0: ES1371

Timers:
31: system timer

Mixers:
0: SigmaTel STAC9721,23

BTW I'm using ALSA 1.0.20
$cat /proc/asound/version 
Advanced Linux Sound Architecture Driver Version 1.0.20.

My volume is up, but I might have configured it all wrong. I guess it's analog duplex, but um unsure. I'm a Linux n00b. :(

---

### Post by barti.net on 2010-03-20
Did you solve this?
I have similar issue after upgrade, but with different hardware. Generally, after system is up there is no sound and no sound device available in preferences. After typing below, everything works fine.
```
sudo alsa force-reload
```I have also doubts about GVFS
```
lsof: WARNING: can't stat() fuse.gvfs-fuse-daemon file system /home/«user»/.gvfs
      Output information may be incomplete.

```Found this solution, but it works only till next reboot, so if it really causes my sound issue, this is not the fix I am looking for.
```
 fusermount -u /home/«user»/.gvfs
```

---

### Post by Bjartur on 2010-10-18
I found a more detailed post by you and my symptoms are exactly the same: card identified, module loaded, pulseaudio started -- but complains about GVFS (why?), the mounting $HOME/.gvfs doesn't help, nor does reloading ALSA.

I'm trying to disable pulse and use alsa directly. Failing that, I will have to stream sound to my Gentoo laptop, which doesn't (currently) use pulse. Sadly, I seem to have to install PulseAudio to receive the stream. :( I was hoping to be able to ‘socket -l 60516 > /dev/audio‘ or ‘nc -s 45610 > /dev/audio‘.

P.S. The numbers 60516 and 45610 are left as an exercise for the reader :P

---

