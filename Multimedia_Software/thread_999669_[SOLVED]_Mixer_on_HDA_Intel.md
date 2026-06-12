---
title: "[SOLVED] Mixer on HDA Intel"
date: 2008-12-02
forum: Multimedia Software
---

### Post by schoonbee on 2008-12-02
Hi,

I need some help to configure my Medion laptop's mixer. Running gamix gives some 'scrambled mappings'. Same with OSS Mixer.

I also had some problems with suspend resume, but the workaround of "sudo alsa force-reload" helps me out for now. Only problem is my mixers are mixed ;)

Some info:
```

$lspci | grep Audio
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)

$cat /proc/asound/cards 
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xfc200000 irq 22


$cat /proc/asound/devices 
  0: [ 0]   : control
  1:        : sequencer
  4: [ 0- 0]: hardware dependent
  6: [ 0- 2]: hardware dependent
 16: [ 0- 0]: digital audio playback
 17: [ 0- 1]: digital audio playback
 20: [ 0- 4]: digital audio playback
 24: [ 0- 0]: digital audio capture
 25: [ 0- 1]: digital audio capture
 26: [ 0- 2]: digital audio capture
 28: [ 0- 4]: digital audio capture
 33:        : timer

$ lsmod | grep snd_
snd_hda_intel         344856  4 
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  2 snd_pcm_oss
snd_pcm                78596  3 snd_hda_intel,snd_pcm_oss
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
snd_hwdep              10500  1 snd_hda_intel
snd_seq_dummy           4868  0 
snd_seq_oss            35584  0 
snd_seq_midi            9376  0 
snd_rawmidi            25760  1 snd_seq_midi
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24836  3 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    56996  15 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device


$aplay -L
default:CARD=Intel
    HDA Intel, ALC883 Analog
    Default Audio Device
front:CARD=Intel,DEV=0
    HDA Intel, ALC883 Analog
    Front speakers
surround40:CARD=Intel,DEV=0
    HDA Intel, ALC883 Analog
    4.0 Surround output to Front and Rear speakers
surround41:CARD=Intel,DEV=0
    HDA Intel, ALC883 Analog
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=Intel,DEV=0
    HDA Intel, ALC883 Analog
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=Intel,DEV=0
    HDA Intel, ALC883 Analog
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=Intel,DEV=0
    HDA Intel, ALC883 Analog
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=Intel,DEV=0
    HDA Intel, ALC883 Digital
    IEC958 (S/PDIF) Digital Audio Output
null
    Discard all samples (playback) or generate zero samples (capture)


```

For the moment I do not have /etc/asound.conf and did not edit /etc/modprobe.d/alsa-base

Then I have:
```

$ amixer 
ALSA lib simple_none.c:1741:(simple_add1) helem (MIXER,'Headphone Playback Switch',0,2,0) appears twice or more
amixer: Mixer default load error: Invalid argument


```

---

### Post by schoonbee on 2008-12-02
Hi,

Solved my problem, even suspend and resume. Thanks to [http://wiki.ubuntuusers.de/Baustelle/Medion_MD_96630](http://wiki.ubuntuusers.de/Baustelle/Medion_MD_96630)

Edit: /etc/modprobe.d/alsa-base
```

options snd-hda-intel model=laptop-medion probe_mask=1 

```

Then reload it:
```

sudo rmmod snd-hda-intel
sudo modprobe snd-hda-intel model=medion probe_mask=1 

```

---

