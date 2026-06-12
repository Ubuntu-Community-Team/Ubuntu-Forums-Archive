---
title: "WebCam microphone not working"
date: 2022-05-21
forum: Multimedia Software
---

### Post by Armence on 2022-05-21
I'm trying to get my webcam microphone to work. The webcam itself works fine. The microphone appears to be detected, but it does not actually pickup any sound. (I use this same webcam with Windows in dual-boot and the mic itself works fine)

```

$ pacmd list-sources

3 source(s) available.
    index: 2
    name: <alsa_output.pci-0000_00_1f.3.iec958-stereo.monitor>
    driver: <module-alsa-card.c>
    flags: DECIBEL_VOLUME LATENCY DYNAMIC_LATENCY
    state: SUSPENDED
    suspend cause: IDLE
    priority: 1030
    volume: front-left: 65536 / 100% / 0.00 dB,   front-right: 65536 / 100% / 0.00 dB
            balance 0.00
    base volume: 65536 / 100% / 0.00 dB
    volume steps: 65537
    muted: no
    current latency: 0.00 ms
    max rewind: 0 KiB
    sample spec: s16le 2ch 44100Hz
    channel map: front-left,front-right
                 Stereo
    used by: 0
    linked by: 0
    configured latency: 0.00 ms; range is 0.50 .. 2000.00 ms
    monitor_of: 1
    card: 2 <alsa_card.pci-0000_00_1f.3>
    module: 9
    properties:
        device.description = "Monitor of Built-in Audio Digital Stereo (IEC958)"
        device.class = "monitor"
        alsa.card = "0"
        alsa.card_name = "HDA Intel PCH"
        alsa.long_card_name = "HDA Intel PCH at 0x4012110000 irq 174"
        alsa.driver_name = "snd_hda_intel"
        device.bus_path = "pci-0000:00:1f.3"
        sysfs.path = "/devices/pci0000:00/0000:00:1f.3/sound/card0"
        device.bus = "pci"
        device.vendor.id = "8086"
        device.vendor.name = "Intel Corporation"
        device.product.id = "43c8"
        device.product.name = "Tiger Lake-H HD Audio Controller"
        device.form_factor = "internal"
        device.string = "0"
        module-udev-detect.discovered = "1"
        device.icon_name = "audio-card-pci"
    index: 4
    name: <alsa_output.pci-0000_01_00.1.hdmi-stereo.monitor>
    driver: <module-alsa-card.c>
    flags: DECIBEL_VOLUME LATENCY DYNAMIC_LATENCY
    state: IDLE
    suspend cause: (none)
    priority: 1030
    volume: front-left: 65536 / 100% / 0.00 dB,   front-right: 65536 / 100% / 0.00 dB
            balance 0.00
    base volume: 65536 / 100% / 0.00 dB
    volume steps: 65537
    muted: no
    current latency: 0.00 ms
    max rewind: 2 KiB
    sample spec: s16le 2ch 44100Hz
    channel map: front-left,front-right
                 Stereo
    used by: 0
    linked by: 0
    configured latency: 1999.82 ms; range is 0.50 .. 1999.82 ms
    monitor_of: 2
    card: 0 <alsa_card.pci-0000_01_00.1>
    module: 7
    properties:
        device.description = "Monitor of HDA NVidia Digital Stereo (HDMI)"
        device.class = "monitor"
        alsa.card = "2"
        alsa.card_name = "HDA NVidia"
        alsa.long_card_name = "HDA NVidia at 0xa1080000 irq 17"
        alsa.driver_name = "snd_hda_intel"
        device.bus_path = "pci-0000:01:00.1"
        sysfs.path = "/devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card2"
        device.bus = "pci"
        device.vendor.id = "10de"
        device.vendor.name = "NVIDIA Corporation"
        device.product.id = "228e"
        device.string = "2"
        module-udev-detect.discovered = "1"
        device.icon_name = "audio-card-pci"
  * index: 7
    name: <alsa_input.usb-USB_Camera_USB_Camera_SN0001-02.mono-fallback>
    driver: <module-alsa-card.c>
    flags: HARDWARE HW_MUTE_CTRL HW_VOLUME_CTRL DECIBEL_VOLUME LATENCY DYNAMIC_LATENCY
    state: RUNNING
    suspend cause: (none)
    priority: 9040
    volume: mono: 65536 / 100% / 0.00 dB
            balance 0.00
    base volume: 65536 / 100% / 0.00 dB
    volume steps: 65537
    muted: no
    current latency: 0.00 ms
    max rewind: 0 KiB
    sample spec: s16le 1ch 44100Hz
    channel map: mono
                 Mono
    used by: 1
    linked by: 1
    configured latency: 10.00 ms; range is 0.50 .. 2000.00 ms
    card: 6 <alsa_card.usb-USB_Camera_USB_Camera_SN0001-02>
    module: 27
    properties:
        alsa.resolution_bits = "16"
        device.api = "alsa"
        device.class = "sound"
        alsa.class = "generic"
        alsa.subclass = "generic-mix"
        alsa.name = "USB Audio"
        alsa.id = "USB Audio"
        alsa.subdevice = "0"
        alsa.subdevice_name = "subdevice #0"
        alsa.device = "0"
        alsa.card = "1"
        alsa.card_name = "USB Camera"
        alsa.long_card_name = "USB Camera USB Camera at usb-0000:00:14.0-11.4, high speed"
        alsa.driver_name = "snd_usb_audio"
        device.bus_path = "pci-0000:00:14.0-usb-0:11.4:1.2"
        sysfs.path = "/devices/pci0000:00/0000:00:14.0/usb1/1-11/1-11.4/1-11.4:1.2/sound/card1"
        udev.id = "usb-USB_Camera_USB_Camera_SN0001-02"
        device.bus = "usb"
        device.vendor.id = "0c45"
        device.vendor.name = "Microdia"
        device.product.id = "6366"
        device.product.name = "Webcam Vitade AF"
        device.serial = "USB_Camera_USB_Camera_SN0001"
        device.form_factor = "webcam"
        device.string = "hw:1"
        device.buffering.buffer_size = "176400"
        device.buffering.fragment_size = "88200"
        device.access_mode = "mmap+timer"
        device.profile.name = "mono-fallback"
        device.profile.description = "Mono"
        device.description = "Webcam Vitade AF Mono"
        module-udev-detect.discovered = "1"
        device.icon_name = "camera-web-usb"
    ports:
        analog-input-mic: Microphone (priority 8700, latency offset 0 usec, available: unknown)
            properties:
                device.icon_name = "audio-input-microphone"
    active port: <analog-input-mic>

```

---

