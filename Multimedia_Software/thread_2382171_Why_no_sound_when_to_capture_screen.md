---
title: "Why no sound when to capture screen ?"
date: 2018-01-10
forum: Multimedia Software
---

### Post by yufeiluo on 2018-01-10
```
sudo apt-get install libav-tools
avconv -f x11grab -r 25 -s 1920x1080 -i :0.0 -vcodec libx264 -threads 4 /tmp/test.avi
```

For the test.avi , all motion in screen were captured  without sound(Playing music with mplayer when capturing screen ,it sounds loud) .
Why no sound captured ?
More info on my alsa.

ls -a /proc/asound
```
card0  devices  modules  PCH  seq     version
..  cards  hwdep    oss      pcm  timers
```


pactl list sources
```
Source #0
    State: SUSPENDED
    Name: alsa_output.pci-0000_00_1b.0.analog-stereo.monitor
    Description: Monitor of Built-in Audio Analog Stereo
    Driver: module-alsa-card.c
    Sample Specification: s16le 2ch 44100Hz
    Channel Map: front-left,front-right
    Owner Module: 6
    Mute: no
    Volume: front-left: 65536 / 100% / 0.00 dB,   front-right: 65536 / 100% / 0.00 dB
            balance 0.00
    Base Volume: 65536 / 100% / 0.00 dB
    Monitor of Sink: alsa_output.pci-0000_00_1b.0.analog-stereo
    Latency: 0 usec, configured 0 usec
    Flags: DECIBEL_VOLUME LATENCY 
    Properties:
        device.description = "Monitor of Built-in Audio Analog Stereo"
        device.class = "monitor"
        alsa.card = "0"
        alsa.card_name = "HDA Intel PCH"
        alsa.long_card_name = "HDA Intel PCH at 0xf7d10000 irq 30"
        alsa.driver_name = "snd_hda_intel"
        device.bus_path = "pci-0000:00:1b.0"
        sysfs.path = "/devices/pci0000:00/0000:00:1b.0/sound/card0"
        device.bus = "pci"
        device.vendor.id = "8086"
        device.vendor.name = "Intel Corporation"
        device.product.id = "8c20"
        device.product.name = "8 Series/C220 Series Chipset High Definition Audio Controller"
        device.form_factor = "internal"
        device.string = "0"
        module-udev-detect.discovered = "1"
        device.icon_name = "audio-card-pci"
    Formats:
        pcm

Source #1
    State: SUSPENDED
    Name: alsa_input.pci-0000_00_1b.0.analog-stereo
    Description: Built-in Audio Analog Stereo
    Driver: module-alsa-card.c
    Sample Specification: s16le 2ch 44100Hz
    Channel Map: front-left,front-right
    Owner Module: 6
    Mute: no
    Volume: front-left: 4465 /   7% / -70.00 dB,   front-right: 4465 /   7% / -70.00 dB
            balance 0.00
    Base Volume: 6554 /  10% / -60.00 dB
    Monitor of Sink: n/a
    Latency: 0 usec, configured 0 usec
    Flags: HARDWARE HW_MUTE_CTRL HW_VOLUME_CTRL DECIBEL_VOLUME LATENCY 
    Properties:
        alsa.resolution_bits = "16"
        device.api = "alsa"
        device.class = "sound"
        alsa.class = "generic"
        alsa.subclass = "generic-mix"
        alsa.name = "ALC887-VD Analog"
        alsa.id = "ALC887-VD Analog"
        alsa.subdevice = "0"
        alsa.subdevice_name = "subdevice #0"
        alsa.device = "0"
        alsa.card = "0"
        alsa.card_name = "HDA Intel PCH"
        alsa.long_card_name = "HDA Intel PCH at 0xf7d10000 irq 30"
        alsa.driver_name = "snd_hda_intel"
        device.bus_path = "pci-0000:00:1b.0"
        sysfs.path = "/devices/pci0000:00/0000:00:1b.0/sound/card0"
        device.bus = "pci"
        device.vendor.id = "8086"
        device.vendor.name = "Intel Corporation"
        device.product.id = "8c20"
        device.product.name = "8 Series/C220 Series Chipset High Definition Audio Controller"
        device.form_factor = "internal"
        device.string = "front:0"
        device.buffering.buffer_size = "352800"
        device.buffering.fragment_size = "176400"
        device.access_mode = "mmap+timer"
        device.profile.name = "analog-stereo"
        device.profile.description = "Analog Stereo"
        device.description = "Built-in Audio Analog Stereo"
        alsa.mixer_name = "Realtek ALC887-VD"
        alsa.components = "HDA:10ec0887,10438576,00100302"
        module-udev-detect.discovered = "1"
        device.icon_name = "audio-card-pci"
    Ports:
        analog-input-front-mic: Front Microphone (priority: 8500, not available)
        analog-input-rear-mic: Rear Microphone (priority: 8200, not available)
        analog-input-linein: Line In (priority: 8100, not available)
    Active Port: analog-input-front-mic
    Formats:
        pcm
```

Does     State: SUSPENDED of alsa   matter ?    
How to fix it?

---

