---
title: "No sound with ubuntu server 10.10 on packard bell easy note"
date: 2010-10-20
forum: Multimedia Software
---

### Post by jidey on 2010-10-20
Hi guys

First, I'm french, sorry for my poor english...

I'm working on my problem for hours now, and I think I need some help... ^^
I have a packard bell easy note netbook. I use it as a server and I installed Ubuntu server 10.10 on it (no graphical interface).
I would like to play some music, with MPD, but I can't get any sound. :(
 I think drivers and modules are OK, but I'm not understanding this point completely.

I installed pulse-audio and alsa paquets, even if I don't uderstand exactly the role of each one.
I think I configured correctly alsamixer (nothing to mute).

I'm testing this way (it's in french, sorry...) :

```
julien@dradouch:~$ speaker-test -c2 -twav

speaker-test 1.0.23

Le périphérique de lecture est default
Les paramètres du flux sont 48000Hz, S16_LE, 2 canaux
Fichier(s) WAV
Taux fixé à 48000Hz (demandé 48000Hz)
Taille du tampon entre 96 et 1048576
Taille de la periode entre 32 et 349526
Utilisation du tampon maximal 1048576
Périodes = 4
La durée de la période à été définie= 262144
La taille du tampon à été définie = 1048576
 0 - Avant Gauche
 1 - Avant Droit
Temps par période = 5,206963
 0 - Avant Gauche
 1 - Avant Droit
Temps par période = 5,194968
 0 - Avant Gauche
.....

```No error, but no sound. 


Some ideas? Thanks!

Some commands, if you need some others, just ask !
```
julien@dradouch:~$ aplay -L
pulse
    Playback/recording through the PulseAudio sound server
front:CARD=Intel,DEV=0
    HDA Intel, ALC260 Analog
    Front speakers
surround40:CARD=Intel,DEV=0
    HDA Intel, ALC260 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Intel,DEV=0
    HDA Intel, ALC260 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Intel,DEV=0
    HDA Intel, ALC260 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Intel,DEV=0
    HDA Intel, ALC260 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Intel,DEV=0
    HDA Intel, ALC260 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=Intel,DEV=0
    HDA Intel, ALC260 Digital
    IEC958 (S/PDIF) Digital Audio Output

``````
julien@dradouch:~$ lsmod | grep snd
snd_hda_codec_realtek   217980  1
snd_hda_intel          22203  2
snd_hda_codec          87552  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5040  1 snd_hda_codec
snd_pcm                71571  2 snd_hda_intel,snd_hda_codec
snd_seq_midi            4588  0
snd_rawmidi            17783  1 snd_seq_midi
snd_seq_midi_event      6047  1 snd_seq_midi
snd_seq                47174  2 snd_seq_midi,snd_seq_midi_event
snd_timer              19067  2 snd_pcm,snd_seq
snd_seq_device          5744  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    49006  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore                880  1 snd
snd_page_alloc          7216  2 snd_hda_intel,snd_pcm

``````
julien@dradouch:~$ cat /proc/asound/modules
 0 snd_hda_intel
```

---

