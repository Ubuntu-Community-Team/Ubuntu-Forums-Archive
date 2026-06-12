---
title: "[regression] USB audio not working anymore?"
date: 2012-09-28
forum: Multimedia Software
---

### Post by CHaoSlayeR on 2012-09-28
Hi there,

I just recently upgraded my system from 11.04 to 11.10 and then directly to 12.04.

I don't exactly remember when it was but either directly after that upgrade or some other upgrade later on my SoundBlaster Live! 24-bit External USB stopped working.

All the controls say that things should be fine, when using pavucontrol I see that the system things the audio is being delivered to the box but whatever I do I cannot get a single noise out of it.

Also, in pavucontrol I see all the outputs, but it doesn't matter which one I try, there is simple not a single crack to hear (and yes, I checked speakers and cables first).

Let's go through some standard things first:

```

$ aplay -l
...
card 1: External [SB Live! 24-bit External], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
...

```

```

$ aplay -L
...
sysdefault:CARD=External
    SB Live! 24-bit External, USB Audio
    Default Audio Device
front:CARD=External,DEV=0
    SB Live! 24-bit External, USB Audio
    Front speakers
surround40:CARD=External,DEV=0
    SB Live! 24-bit External, USB Audio
    4.0 Surround output to Front and Rear speakers
surround41:CARD=External,DEV=0
    SB Live! 24-bit External, USB Audio
    4.1 Surround output to Front, Rear and Subwoofer speakers
surround50:CARD=External,DEV=0
    SB Live! 24-bit External, USB Audio
    5.0 Surround output to Front, Center and Rear speakers
surround51:CARD=External,DEV=0
    SB Live! 24-bit External, USB Audio
    5.1 Surround output to Front, Center, Rear and Subwoofer speakers
surround71:CARD=External,DEV=0
    SB Live! 24-bit External, USB Audio
    7.1 Surround output to Front, Center, Side, Rear and Woofer speakers
iec958:CARD=External,DEV=0
    SB Live! 24-bit External, USB Audio
    IEC958 (S/PDIF) Digital Audio Output
dmix:CARD=External,DEV=0
    SB Live! 24-bit External, USB Audio
    Direct sample mixing device
dsnoop:CARD=External,DEV=0
    SB Live! 24-bit External, USB Audio
    Direct sample snooping device
hw:CARD=External,DEV=0
    SB Live! 24-bit External, USB Audio
    Direct hardware device without any conversions
plughw:CARD=External,DEV=0
    SB Live! 24-bit External, USB Audio
    Hardware device with all software conversions
...

```

```

$ amixer -c 1
Simple mixer control 'PCM',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 100
  Mono: Playback 100 [100%] [0.00dB] [on]
Simple mixer control 'Mic',0
  Capabilities: cvolume cvolume-joined penum
  Capture channels: Mono
  Limits: Capture 0 - 15
  Mono: Capture 0 [0%] [0.00dB]
Simple mixer control 'CMSS LED',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'Power LED',0
  Capabilities: pswitch pswitch-joined penum
  Playback channels: Mono
  Mono: Playback [on]

```

So it looks like it detects the LEDs but nothing else, whereas the "aplay -L" output correctly shows the real capabilities of that device.

On the other hand, the built-in outputs on the mainboard are all working correctly.

So I suspect a problem with the snd_usb_audio kernel module instead of my ALSA/Pulse stack (which is basically all at defaults in terms of configuration).

Here are my loaded modules:
```

snd_hrtimer            12744  1 
snd_hda_codec_hdmi     32377  1 
snd_hda_codec_realtek    79533  1 
snd_hda_intel          34116  6 
snd_hda_codec         135140  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_usb_audio         132137  2 
snd_usbmidi_lib        25396  1 snd_usb_audio
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_hwdep              13668  2 snd_hda_codec,snd_usb_audio
snd_seq                61897  3 snd_seq_midi,snd_seq_midi_event
snd_rawmidi            30749  2 snd_usbmidi_lib,snd_seq_midi
snd_pcm                97435  5 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_usb_audio
snd_seq_device         14497  3 snd_seq_midi,snd_seq,snd_rawmidi
snd_timer              29989  3 snd_hrtimer,snd_seq,snd_pcm
snd                    83487  28 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_usb_audio,snd_usbmidi_lib,snd_hwdep,snd_seq,snd_rawmidi,snd_pcm,snd_seq_device,snd_timer
snd_page_alloc         18572  2 snd_hda_intel,snd_pcm

```

---

### Post by CHaoSlayeR on 2012-10-08
Bumping this one as I really need that device to function again.

Anyone has any idea?

---

### Post by CHaoSlayeR on 2012-10-28
This is embarrassing. I just connected this neat little USB box to my old Synology NAS (a DS409+) and now guess what: worked out of the box.

So there has been some mess-ups somewhere as it definitively worked back in 11.04.

---

