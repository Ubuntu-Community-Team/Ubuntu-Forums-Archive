---
title: "Int and Ext Mic won't work"
date: 2009-12-11
forum: Multimedia Software
---

### Post by David Yoakley on 2009-12-11
Switched to ubuntu from windoze and have not been able to get mic to work relicably.
Initially installed 9.04. Using skype, mic would work in 1 call then not again until I rebooted.

Upgraded to 9.10 and can't get it to work at all.  Speakers work fine, just not internal or external mic (spdif headset).

Card: HDA NVidia                                                             &#9474;
Chip: Conexant CX20549 (Venice)
lspci | grep Audio
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)

Its not muted or turned down.  arecord tries to record but playing it back I get nothing.  I've dumped what I know to dump below.  Using alsamixer I notice that it shows "Ext Mic", "ExtMic", "Int Mic" and "IntMic".  Only "Ext Mic" and "Int Mic" allow me to set the capture level.  I've tried turning one off and testing other but no luk.  Also verified that neither is muted.

Using gnome Sound Preferences, I see these hardware options:
  Analog Stereo Input
  Analog Stereo Duplex (IEC958)
  Digital Stereo (IEC958) Output + Analog Stereo Input
  Analog Stereo Output
  Analog Stereo Duplex

Output tab shows varius things depending on Hardware tab.  I think I've tried about all the combinations between the two.  I've also installed the Pulse Audo Applet and fiddled with it. 

>lsmod | grep snd
snd_seq_dummy           3460  0 
snd_seq_oss            33440  0 
snd_seq_midi            8192  0 
snd_rawmidi            27360  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                60608  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_seq_device          8308  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd_pcm_oss            44704  0 
snd_mixer_oss          18976  1 snd_pcm_oss
snd_hda_codec_conexant    25376  1 
snd_hda_intel          31880  6 
snd_hda_codec          87584  2 snd_hda_codec_conexant,snd_hda_intel
snd_hwdep               9352  1 snd_hda_codec
snd_pcm                93160  5 snd_pcm_oss,snd_hda_intel,snd_hda_codec
snd_timer              26992  2 snd_seq,snd_pcm
snd                    77096  22 snd_seq_oss,snd_rawmidi,snd_seq,snd_seq_device,snd_pcm_oss,snd_mixer_oss,snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_timer
soundcore               9088  1 snd
snd_page_alloc         10928  2 snd_hda_intel,snd_pcm

>amixer
Simple mixer control 'Master',0
  Capabilities: pvolume pswitch pswitch-joined
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 43
  Mono:
  Front Left: Playback 27 [63%] [-24.00dB] [on]
  Front Right: Playback 25 [58%] [-27.00dB] [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 20
  Mono:
  Front Left: Playback 20 [100%] [0.00dB] [on]
  Front Right: Playback 20 [100%] [0.00dB] [on]
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'IEC958 Default PCM',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'Ext Mic',0
  Capabilities: pvolume cvolume pswitch cswitch
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 20 Capture 0 - 23
  Front Left: Playback 14 [70%] [-9.00dB] [on] Capture 16 [70%] [24.00dB] [on]
  Front Right: Playback 14 [70%] [-9.00dB] [on] Capture 14 [61%] [21.00dB] [on]
Simple mixer control 'ExtMic',0
  Capabilities: cswitch cswitch-joined cswitch-exclusive
  Capture exclusive group: 0
  Capture channels: Mono
  Mono: Capture [on]
Simple mixer control 'Int Mic',0
  Capabilities: pvolume cvolume pswitch cswitch
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: Playback 0 - 20 Capture 0 - 23
  Front Left: Playback 14 [70%] [-9.00dB] [off] Capture 15 [65%] [22.50dB] [off]
  Front Right: Playback 14 [70%] [-9.00dB] [off] Capture 15 [65%] [22.50dB] [off]
Simple mixer control 'IntMic',0
  Capabilities: cswitch cswitch-joined cswitch-exclusive
  Capture exclusive group: 0
  Capture channels: Mono
  Mono: Capture [off]


:(
David

---

### Post by moninalexander on 2009-12-11
Have similar problem with internal mic (haven't checked if external works)

---

### Post by David Yoakley on 2009-12-11
Something else that may or may not be related.  I've noticed that the speakers crack/pop every few minutes almost as if the audio card is going in and out of power savings mode.  Can someone tell me how to turn on/off powersavings mode for the card to I can look into this part?

---

### Post by etherealknight on 2010-02-22
you need to enter this command into the terminal: sudo gedit '/etc/modprobe.d/alsa-base.conf' 

and change this line: options snd-hda-intel power_save=10
to this: options snd-hda-intel power_save=0

the '/ect/modprobe.d/alsa-base.conf' being the file within that directory. drag it to the terminal after typing sudo gedit.

---

