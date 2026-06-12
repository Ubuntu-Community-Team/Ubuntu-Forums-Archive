---
title: "How to test microphone is working"
date: 2011-06-17
forum: Multimedia Software
---

### Post by oygle on 2011-06-17
I have a Logitech ClearChat Stereo headset, and can hear music playing with the headset connected to the PC speakers (external Logitech).

Have setup Empathy to be able to talk to someone using Google Talk. It seems to have been setup correctly, as I can see 2 contacts in the offline list.

I don't have PulseAudio installed (I think ??), and can see only System | Preferences | Sound , which doesn't show me much.

Here are the settings at present (inboard audio card) ..

```

:~$ sudo aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC1200 Analog [ALC1200 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC1200 Digital [ALC1200 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
:~$
:~$ lsb_release -a && uname -r
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 10.04.2 LTS
Release:	10.04
Codename:	lucid
2.6.32-32-generic
:~$ 
:~$ dmesg | egrep -i "sound|audio|snd"
:~$ 
:~$ cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xf9ff8000 irq 22
:~$ 
:~$ lspci | grep -i audio
00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
:~$ 
:~$ lsmod | grep snd
snd_hda_codec_realtek   279008  1 
snd_hda_intel          25805  4 
snd_hda_codec          85759  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               6924  1 snd_hda_codec
snd_pcm_oss            41394  0 
snd_mixer_oss          16299  1 snd_pcm_oss
snd_pcm                87946  4 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1782  0 
snd_seq_oss            31191  0 
snd_seq_midi            5829  0 
snd_rawmidi            23420  1 snd_seq_midi
snd_seq_midi_event      7267  2 snd_seq_oss,snd_seq_midi
snd_seq                57481  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23649  2 snd_pcm,snd_seq
snd_seq_device          6888  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    71283  19 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8052  1 snd
snd_page_alloc          8500  2 snd_hda_intel,snd_pcm
:~$ 

```

How can I test that the microphone is working correctly please ?

Oygle

---

### Post by sanderj on 2011-06-17
> **oygle said:**
> 


How can I test that the microphone is working correctly please ?



Applications -> Sound & Video -> Sound Recorder.

---

### Post by oygle on 2011-06-17
I had to change the settings to get the input correct, but then it worked fine and recorded. Thanks.  :)

---

