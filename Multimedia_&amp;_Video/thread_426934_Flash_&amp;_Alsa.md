---
title: "Flash &amp; Alsa"
date: 2007-04-28
forum: Multimedia &amp; Video
---

### Post by salinon on 2007-04-28
I earlier had no sound so I compiled the alsa drivers again. That has given me sound back in applications. That is, amarok, xmms etc. are good. But I dont  get any sound in flash in firefox or opera. When i try running alsamixer on the terminal i get a 

alsamixer: function snd_ctl_open failed for default: No such device

~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC861 Analog [ALC861 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 6: Si3054 Modem [Si3054 Modem]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

~$ lsmod | grep snd
snd_hda_intel          22296  1 
snd_hda_codec         200320  1 snd_hda_intel
snd_pcm_oss            44672  0 
snd_mixer_oss          17792  1 snd_pcm_oss
snd_pcm                80900  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_oss            35200  0 
snd_seq_midi_event      8576  1 snd_seq_oss
snd_seq                54000  4 snd_seq_oss,snd_seq_midi_event
snd_timer              24196  2 snd_pcm,snd_seq
snd_seq_device          9612  2 snd_seq_oss,snd_seq
snd                    56452  11 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_seq,snd_timer,snd_seq_device
soundcore               8672  1 snd
snd_page_alloc         11272  2 snd_hda_intel,snd_pcm

$lspci -nnv
00:1b.0 Audio device [0403]: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller [8086:27d8] (rev 02)
        Subsystem: Toshiba America Info Systems Unknown device [1179:ff10]
        Flags: bus master, fast devsel, latency 0, IRQ 22
        Memory at dc240000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

I dont know if these two problem are related. I try linking the files as explained in another post but that do anything. Help !

---

### Post by ckoester on 2007-05-09
I recently had a problem where I had no audio in Flash videos.  When I tried to open Alsamixer I received the following error:

ALSA lib conf.c:1587: (snd_config_load1)  _toplevel_:5:38:No such file or directory
ALSA lib conf.c:2848: (snd_config_hook_load)  /home/ckoester/.asoundrc may be old or corrupted: consider to remove or fix it
ALSA lib conf.c:2712: (snd_config_hooks_call)  function snd_config_hook_load returned error: No such file or directory
ALSA lib conf.c:3075: (snd_config_update_r)  hooks failed, removing configuration

It turned out that the file /home/ckoester/.asoundrc was indeed the problem.  The last line of the file was referring to a file with a username that no longer existed.  I commented out the last line and was immediately able to open Alsamixer. 

After adjusting a couple of things in Alsamixer my Flash audio now works fine.

---

