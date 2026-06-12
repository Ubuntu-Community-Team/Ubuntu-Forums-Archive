---
title: "Microphone/sound input not working (Samsung NC10)"
date: 2011-01-21
forum: Multimedia Software
---

### Post by scaara on 2011-01-21
Hi!

I've tried to look for a solution for a few days now, and haven't had any results so far. I really hope you can help me so I can get to talk with my girlfriend =D Any and all help is much appreciated!

I'm running Lubuntu with 10.04 LTS, and alsa version 1.0.23 on Samsung NC10.

**_Short description:_** 

Hardware works, soundcard is recognized by the OS, modules are loaded, alsamixer volume up and unmuted, sound output is ok, arecord or sound recorder don't get input.

_**Long description:**_

- The microphone hardware works. Having the volumes up I hear the noise from the speakers when tapping the microphone.

- Soundcard is recognized by OS (and like I said, music and all other sound output is perfectly fine)

```
        *-multimedia
             description: Audio device
             product: N10/ICH 7 Family High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=HDA Intel latency=0
             resources: irq:27 memory:f0340000-f0343fff

```

- Here are all the "snd"-modules given by lsmod:

```
snd_hda_codec_realtek   216061  1 
snd_hda_intel          20767  7 
snd_hda_codec          86936  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5604  1 snd_hda_codec
snd_pcm_oss            34539  0 
snd_mixer_oss          13897  1 snd_pcm_oss
snd_pcm                71582  5 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1434  0 
snd_seq_oss            27274  0 
snd_seq_midi            4589  0 
snd_rawmidi            19077  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47594  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              18678  4 snd_pcm,snd_seq
snd_seq_device          6020  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    56335  24 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm

```

- I've added line **options snd-hda-intel model=samsung-nc10** to **/etc/modprobe.d/alsa-base.conf** according to [[COLOR="Red"]this guide[/COLOR]]("https://help.ubuntu.com/community/HdaIntelSoundHowto").

- Here is part from the output of the script from the step 3 of [[COLOR="red"]this guide[/COLOR]]("https://help.ubuntu.com/community/SoundTroubleshootingProcedure"):

```
!!Aplay/Arecord output
!!------------

APLAY

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC272 Analog [ALC272 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

ARECORD

**** List of CAPTURE Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC272 Analog [ALC272 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

!!Amixer output
!!-------------

!!-------Mixer controls for card 0 [Intel]

Card hw:0 'Intel'/'HDA Intel at 0xf0340000 irq 27'
  Mixer name	: 'Realtek ALC272'
  Components	: 'HDA:10ec0272,144dca00,00100001'
  Controls      : 18
  Simple ctrls  : 11
Simple mixer control 'Master',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 64
  Mono: Playback 47 [73%] [-17.00dB] [on]
Simple mixer control 'Headphone',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 64
  Mono:
  Front Left: Playback 64 [100%] [0.00dB] [on]
  Front Right: Playback 64 [100%] [0.00dB] [on]
Simple mixer control 'Speaker',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 64
  Mono:
  Front Left: Playback 64 [100%] [0.00dB] [on]
  Front Right: Playback 64 [100%] [0.00dB] [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 255 [100%] [0.00dB]
  Front Right: Playback 255 [100%] [0.00dB]
Simple mixer control 'Beep',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 0 [0%] [-34.50dB] [off]
  Front Right: Playback 0 [0%] [-34.50dB] [off]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 31
  Front Left: Capture 31 [100%] [30.00dB] [off]
  Front Right: Capture 31 [100%] [30.00dB] [off]
Simple mixer control 'Digital',0
  Capabilities: cvolume penum
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 120
  Front Left: Capture 120 [100%] [30.00dB]
  Front Right: Capture 120 [100%] [30.00dB]
Simple mixer control 'Ext Mic',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 31 [100%] [12.00dB] [on]
  Front Right: Playback 31 [100%] [12.00dB] [on]
Simple mixer control 'Ext Mic Boost',0
  Capabilities: volume penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 3
  Front Left: 0 [0%]
  Front Right: 0 [0%]
Simple mixer control 'Int Mic',0
  Capabilities: pvolume pswitch penum
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 31
  Mono:
  Front Left: Playback 31 [100%] [12.00dB] [on]
  Front Right: Playback 31 [100%] [12.00dB] [on]
Simple mixer control 'Int Mic Boost',0
  Capabilities: volume penum
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 3
  Front Left: 0 [0%]
  Front Right: 0 [0%]

```

Hopefully someone could give a few pointers here. Even if this remains unsolved, I thank you as this forum has helped me in the past so many times! Thank you! =)

-Samu

---

### Post by scaara on 2011-01-21
Wow, it seems those three other threads I tried to make last night got started after all. I'm terribly sorry about flooding the forums. Please ignore those and only use this one.

-Samu

---

### Post by lidex on 2011-01-21
First, for mic problem, check this.
**Gnome-alsamixer**
Using Alt+F2 run dialog
```
 gnome-alsamixer 
```
**Use 'Edit -> Sound Card Properties' menu to enable elements.**
Soundcard tab to select / adjust levels.
To install:
```
sudo apt-get install gnome-alsamixer
```

Then go to 'Sound Preferences' to select the correct device and mic ('Connector' option) and unmute your mic in 'Input' tab.
Make sure you have selected a profile with 'duplex' or 'analog input' for the correct sound device on the 'Hardware' tab.
Use Pulse Audio Volume Control (pavucontrol) to unlock stereo sliders for the mic in 'Input Devices' tab. Drag the right slider down to zero. The mic is a mono device.

From alsa documentation:
> Capture Problems
~~~~~~~~~~~~~~~~
The capture problems are often because of missing setups of mixers.
Thus, before submitting a bug report, make sure that you set up the
mixer correctly.  For example, both "Capture Volume" and "Capture
Switch" have to be set properly in addition to the right "Capture
Source" or "Input Source" selection.  Some devices have "Mic Boost"
volume or switch.

When the PCM device is opened via "default" PCM (without pulse-audio
plugin), you'll likely have "Digital Capture Volume" control as well.
This is provided for the extra gain/attenuation of the signal in
software, especially for the inputs without the hardware volume
control such as digital microphones.  Unless really needed, this
should be set to exactly 50%, corresponding to 0dB -- neither extra
gain nor attenuation.  When you use "hw" PCM, i.e., a raw access PCM,
this control will have no influence, though.

---

### Post by scaara on 2011-01-24
Thank you for the reply! In the end it turns out gnome-alsamixer was enough =) After installing it and checking the box "Rec" under Capture slider everything works fine.

Thank you so much!

-Samu

---

