---
title: "Microsoft Lifechat LX-3000 USB Headset, Wine, Ventrilo Problem."
date: 2008-09-06
forum: Multimedia Software
---

### Post by piph on 2008-09-06
Hello all,

I've been using ubuntu off and on for about a year, not really hardcore linux guru or anything but I'm getting irritated with this problem I'm having. Now before I tell you about my problem and people go "Dude use the search engine there is thousands of guides on this, blah blah you want to support linux go download teamspeak or mumble". Now I've tried all these guides on here and some other places and still have no fix for my problem. Yes I know my headset is microsoft but its one of the best headsets I've had that is comfortable and produces decent sound. I have sound and my microphone works fine in any other program but stuff that is used in wine. Now in wine if i select ALSA, I can hear people but can't talk. If I switch to OSS, I can talk and I can't hear people. Everything in System > Preferences > Sound is on ALSA, and device is set to Microsoft Lifechat LX-3000 (Alsa mixer). Alsamixer recognizes my usb headset (playback/capture/all).

Running Ubuntu Hardy Heron 8.04, Wine 1.1.3(Tried downgrading too), Ventrilo 3.01

$ cat /proc/asound/cards
1 [default        ]: USB-Audio - Microsoft LifeChat LX-3000 
                      Microsoft LifeChat LX-3000  at usb-0000:00:02.0-1, full speed

$ cat /proc/asound/devices
  1:        : sequencer
 32: [ 1]   : control
 33:        : timer
 48: [ 1- 0]: digital audio playback
 56: [ 1- 0]: digital audio capture

$ ls /dev/*dsp*
/dev/dsp1

$ cat /proc/asound/pcm
01-00: USB Audio : USB Audio : playback 1 : capture 1

$ lsmod | grep snd
snd_usb_audio          88416  1 
snd_usb_lib            19456  1 snd_usb_audio
snd_hwdep              10884  1 snd_usb_audio
snd_pcm_oss            51232  0 
snd_mixer_oss          18432  1 snd_pcm_oss
snd_pcm                86660  2 snd_usb_audio,snd_pcm_oss
snd_seq_dummy           4996  0 
snd_seq_oss            35968  0 
snd_seq_midi           10784  0 
snd_rawmidi            27168  2 snd_usb_lib,snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                58320  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              25988  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    64708  16 snd_usb_audio,snd_usb_lib,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq_midi_event,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
snd_page_alloc         12168  1 snd_pcm
usbcore               146028  6 snd_usb_audio,snd_usb_lib,usbhid,ehci_hcd,ohci_hcd

Now in Wine, I did eventually have both sound and voice working with Esound (however after a couple re-installations and what not of wine and messing aroudn with it, it is no longer there, and when it was there I sounded like optimus prime from transformers)

Now I'm pretty sure it has to do with my ~/asoundrc file, because when I play around with that wine seems to recognize dmix and dsnooper (wavein/out) under alsa. But still having the same problem as i'm allowed to hear people on vent with alsa, and only talk on OSS. Will post any other information to help me with this problem. I appreciate you taking the time to read this and hopefully solve my problem!

Edit: Forgot to mention that when I run in alsa (under wine) ventrilo, i get this error when trying to test my microphone:
Unable to activate DirectSound for selected device.
DirectSoundCaptureCreate failed, hr = 88780078 (followed by: Open input device failed)

---

### Post by piph on 2008-09-08
Bump

---

