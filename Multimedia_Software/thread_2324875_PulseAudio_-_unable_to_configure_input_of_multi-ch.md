---
title: "PulseAudio - unable to configure input of multi-channel card"
date: 2016-05-17
forum: Multimedia Software
---

### Post by emp9183 on 2016-05-17
Hi all,
I recently bought an Audient iD14 sound interface which is working great in JACK applications (Bitwig, Ardour). It's also working great as my primary OS-wide output interface through PulseAudio, but I'm having issues trying to get it to work for input in non-multichannel applications (e.g. use the mic in Google Hangouts).
The Gnome Sound control panel doesn't recognize the card as an input. In 'pacmd list-sources' I do see it as a multi-channel input:
```
        name: <alsa_input.usb-Audient_Audient_iD14-00.multichannel>
        driver: <module-alsa-card.c>
        flags: HARDWARE DECIBEL_VOLUME LATENCY
        state: SUSPENDED
        suspend cause: IDLE
        priority: 9040
        volume: front-left: 0 /   0% / -inf dB,   front-right: 65536 / 100% / 0.00 dB,   rear-left: 0 /   0% / -inf dB,   rear-right: 0 /   0% / -inf dB,   front-center: 0 /   0% / -inf dB,   lfe: 0 /   0% / -inf dB,   side-left: 0 /   0% / -inf dB,   side-right: 0 /   0% / -inf dB,   aux0: 0 /   0% / -inf dB,   aux1: 0 /   0% / -inf dB
                balance 1.00
        base volume: 65536 / 100% / 0.00 dB
        volume steps: 65537
        muted: no
        current latency: 0.00 ms
        max rewind: 0 KiB
        sample spec: s32le 10ch 44100Hz
        channel map: front-left,front-right,rear-left,rear-right,front-center,lfe,side-left,side-right,aux0,aux1

```

I was thinking Gnome won't show the card as an input source because it's confused by the multiple input channels, so I was trying to remap one channel to get a single-input virtual interface:
```
pactl load-module module-remap-source source_name=s3 master=alsa_input.usb-Audient_Audient_iD14-00.multichannel master_channel_map=front-left channel_map=front-left
```
This caused the Sound panel to show a 'Remapped Audient iD14 Multichannel' interface, but this interface shows no signal no matter which master channel I choose as the master instead of the first front-left above :(
In fact, when trying to map a few of these, the Sound panel in Gnome acts completely weird and seems to show for some of them an active signal coming from the built-in laptop microphone (?!)
Am I doing something wrong here? Is there a better way to accomplish what I'm trying to do?
I'm using PulseAudio 6.0 coming with Ubuntu Gnome 15.10.

---

