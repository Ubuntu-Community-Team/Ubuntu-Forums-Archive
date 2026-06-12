---
title: "Alsa playback device -&gt; Pulse Audio profile"
date: 2017-12-14
forum: Multimedia Software
---

### Post by scokar2 on 2017-12-14
Hello!

Question:  How can I make an alsa playback device name available to Pulse Audio as a card profile?

I have a Yamaha Steinberg UR44 USB audio interface.


aplay -l identifies the device as:


```
card 1: UR44 [Steinberg UR44], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #



```

aplay -L includes a "front" playback device:


```
front:CARD=UR44,DEV=0
    Steinberg UR44, USB Audio
    Front speakers



```

However, pactl list cards does not show "front" as an **output profile**:


```
pactl list cards
Card #0
    Name: alsa_card.usb-Yamaha_Corporation_Steinberg_UR44-00
    Driver: module-alsa-card.c
    Owner Module: 6
    Properties:
        alsa.card = "1"
        alsa.card_name = "Steinberg UR44"
        alsa.long_card_name = "Yamaha Corporation Steinberg UR44 at usb-0000:00:14.0-14, high speed"
        alsa.driver_name = "snd_usb_audio"
        device.bus_path = "pci-0000:00:14.0-usb-0:14:1.0"
        sysfs.path = "/devices/pci0000:00/0000:00:14.0/usb3/3-14/3-14:1.0/sound/card1"
        udev.id = "usb-Yamaha_Corporation_Steinberg_UR44-00"
        device.bus = "usb"
        device.vendor.id = "0499"
        device.vendor.name = "Yamaha Corp."
        device.product.id = "1704"
        device.product.name = "Steinberg UR44"
        device.serial = "Yamaha_Corporation_Steinberg_UR44"
        device.string = "1"
        device.description = "Steinberg UR44"
        module-udev-detect.discovered = "1"
        device.icon_name = "audio-card-usb"
    **Profiles:**
        **input:multichannel-input:** Multichannel Input (sinks: 0, sources: 1, priority: 1, available: yes)
        **output:analog-surround-40**: Analog Surround 4.0 Output (sinks: 1, sources: 0, priority: 700, available: yes)
        **output:analog-surround-40+input:multichannel-input**: Analog Surround 4.0 Output + Multichannel Input (sinks: 1, sources: 1, priority: 701, available: yes)
        off: Off (sinks: 0, sources: 0, priority: 0, available: yes)
    Active Profile: output:analog-surround-40+input:multichannel-input
    Ports:
        multichannel-input: Multichannel Input (priority: 0, latency offset: 0 usec)
            Part of profile(s): input:multichannel-input, output:analog-surround-40+input:multichannel-input
        analog-output: Analog Output (priority: 9900, latency offset: 0 usec)
            Part of profile(s): output:analog-surround-40, output:analog-surround-40+input:multichannel-input





```

How do I get the "front" stereo profile to be available and selectable in Pulse Audio?


Thanks

---

