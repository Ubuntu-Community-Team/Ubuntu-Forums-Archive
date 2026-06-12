---
title: "Usb sound device problems with Karmic"
date: 2009-11-27
forum: Multimedia Software
---

### Post by itlarson on 2009-11-27
I Have a usb sound device which worked under jaunty, but doesn't under Karmic.  It is the Art usb phono preamp.  I believe it used to supported by the module snd-usb-audio, but this doesn't seem to be installed or in the repositories.  Here's a few things I have tried to diagnose this:

itl@itldesk:~$ lsmod | grep snd
snd_intel8x0           30168  4 
snd_ac97_codec        101216  1 snd_intel8x0
ac97_bus                1532  1 snd_ac97_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           2656  0 
snd_seq_oss            28576  0 
snd_seq_midi            6432  0 
snd_rawmidi            22208  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    59204  18 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               7264  1 snd
snd_page_alloc          9156  2 snd_intel8x0,snd_pcm


itl@itldesk:~$ lsusb
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 03f0:1204 Hewlett-Packard DeskJet 930c
Bus 002 Device 002: ID 046d:c404 Logitech, Inc. TrackMan Wheel
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

itl@itldesk:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: ICH5 [Intel ICH5], device 0: Intel ICH [Intel ICH5]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH5 [Intel ICH5], device 4: Intel ICH - IEC958 [Intel ICH5 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


There is no mention of anything like my usb sound device, and nothing usb shows up in audacity recording device setup.

---

### Post by itlarson on 2009-11-27
Oh I thought to try sudo modprobe snd_usb_audio.  Now snd_usb_audio shows up when I lsmod, but the other two outputs are the same.  I restarted audacity, but still no usb devices in preferences.

---

### Post by itlarson on 2009-11-28
bump

---

### Post by itlarson on 2009-12-05
Nevermind- I hadn't thought to check the cable, since the device was getting power. When I finally did I found it was slightly loose.  I pushed it in the rest of the way, and sure enough, usb audio codec showed up in audacity's sound devices.  Who knew a usb cable could be plugged in enough to provide power, but not enough to send data.

---

