---
title: "Soundcard installation issue.  ALC861VD"
date: 2008-10-01
forum: Multimedia Software
---

### Post by Maxwelldon on 2008-10-01
So, I've got this motherboard; [Biostar P4M900-M4](http://www.biostar.com.tw/app/en-us/mb/content.php?S_ID=283)
And Ati HD3850 256MB as Graphics card.

Soundcard is integrated Realtek ALC861VD 6-Channel HD Audio and I just cant seem get it work properly even though I've tried a few ways to do it..
Now I've got fresh install with just updates installed and no modifications to settings more than maxing volume up.

Mic seems to go around to the speakers but none of the flash apps give any sound from FireFox to my speakers..

I've tried no music / movie players yet since I can't decide which to install...

Main purpose for the current installation would be to get games to work; Main target is Steam and CS:S with sounds and mic.

**sudo lshw -class sound**
```
  *-multimedia            
       description: Audio device
       product: Radeon HD 3870 Audio device
       vendor: ATI Technologies Inc
       physical id: 0.1
       bus info: pci@0000:02:00.1
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi bus_master cap_list
       configuration: driver=HDA Intel latency=0 module=snd_hda_intel
  *-multimedia
       description: Audio device
       product: VIA High Definition Audio Controller
       vendor: VIA Technologies, Inc.
       physical id: 1
       bus info: pci@0000:80:01.0
       version: 10
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=HDA Intel latency=0 module=snd_hda_intel
```

**cat /proc/asound/card0/codec\#***
```
Codec: Generic 1002 ATI R6xx HDMI
Address: 0
Vendor Id: 0x1002aa01
Subsystem Id: 0xaa0100
Revision Id: 0x100000
No Modem Function Group found
Default PCM:
    rates [0x40]: 48000
    bits [0x2]: 16
    formats [0x1]: PCM
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
GPIO: io=0, o=0, i=0, unsolicited=0, wake=0
Node 0x02 [Audio Output] wcaps 0x201: Stereo Digital
  Converter: stream=0, channel=0
  Digital:
  Digital category: 0x0
Node 0x03 [Pin Complex] wcaps 0x400381: Stereo Digital
  Pincap 0x0894: OUT Detect R/L
  Pin Default 0x18560010: [Jack] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0x1, Sequence = 0x0
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Connection: 1
     0x02
```

**lsmod | grep snd**
```
snd_hda_intel         344728  3 
snd_pcm_oss            42144  0 
snd_mixer_oss          17920  1 snd_pcm_oss
snd_pcm                78596  2 snd_hda_intel,snd_pcm_oss
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
snd_hwdep              10500  1 snd_hda_intel
snd_seq_dummy           4868  0 
snd_seq_oss            35584  0 
snd_seq_midi            9376  0 
snd_rawmidi            25760  1 snd_seq_midi
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24836  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    56996  17 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
```

**ls /proc/asound/**
```
 /proc/asound/
card0  card1  cards  devices  HDMI  hwdep  modules  oss  pcm  seq  timers  version  VT82xx
```

**less /proc/asound/cards**
```
 0 [HDMI           ]: HDA-Intel - HDA ATI HDMI
                      HDA ATI HDMI at 0xfdefc000 irq 22
 1 [VT82xx         ]: HDA-Intel - HDA VIA VT82xx
                      HDA VIA VT82xx at 0xbfffc000 irq 23
```

**less /proc/asound/devices**
```
  0: [ 0]   : control
  1:        : sequencer
  4: [ 0- 0]: hardware dependent
 19: [ 0- 3]: digital audio playback
 32: [ 1]   : control
 33:        : timer
 36: [ 1- 0]: hardware dependent
 48: [ 1- 0]: digital audio playback
 49: [ 1- 1]: digital audio playback
 56: [ 1- 0]: digital audio capture
```

---

### Post by Yellow Pasque on 2008-10-01
```
sudo apt-get install libflashsupport
asoundconf list

```
Use *asoundconf set-default-card cardname* to set the default card to your onboard audio and not the HDMI (it looks like it might have the HDMI as default[/code]

Also, make sure your alsa-base is configured correctly: [http://ubuntuforums.org/showpost.php?p=5131958&postcount=2](http://ubuntuforums.org/showpost.php?p=5131958&postcount=2)

---

### Post by Maxwelldon on 2008-10-02
Thanks, so far it's been working now with MP3 files via Rhythmbox and installed codecs as well as flash app sounds.
Going to download and install Warsow to see if game sounds are working :)

---

