---
title: "Pulseaudio through ssh"
date: 2010-11-09
forum: Multimedia Software
---

### Post by mslootweg on 2010-11-09
I´m totally not getting how to get sound to work for me.
What I am attempting is this:
My server is running Ubuntu 10.04 Server edition, with gdm and gnome-core(minimal gnome desktop) installed. This is because this server is also hooked up to a display. Now everything works wonderfully out of the box, I immediately got sound when I logged in on the graphical interface and played some video. If I login through SSH on the same user and play audio it also works. If I login through ssh on another user however I´m having no such luck.

running aplay -l will allways return the same output in all situations:

```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC662 rev1 Analog [ALC662 rev1 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC662 rev1 Digital [ALC662 rev1 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```using the list-sinks command of the program pacmd on the user used for the video output with functional sound return this output:

```
1 sink(s) available.
  * index: 0
    name: <alsa_output.pci-0000_00_1b.0.analog-stereo>
    driver: <module-alsa-card.c>
    flags: HARDWARE HW_MUTE_CTRL HW_VOLUME_CTRL DECIBEL_VOLUME LATENCY DYNAMIC_LATENCY
    state: RUNNING
    suspend cause: 
    priority: 9959
    volume: 0:  45% 1:  45%
            0: -21.00 dB 1: -21.00 dB
            balance 0.00
    base volume: 100%
                 0.00 dB
    volume steps: 65537
    muted: no
    current latency: 49.77 ms
    max request: 13 KiB
    max rewind: 344 KiB
    monitor source: 0
    sample spec: s16le 2ch 44100Hz
    channel map: front-left,front-right
                 Stereo
    used by: 1
    linked by: 1
    configured latency: 80.00 ms; range is 0.50 .. 1999.82 ms
    card: 0 <alsa_card.pci-0000_00_1b.0>
    module: 4
    properties:
        alsa.resolution_bits = "16"
        device.api = "alsa"
        device.class = "sound"
        alsa.class = "generic"
        alsa.subclass = "generic-mix"
        alsa.name = "ALC662 rev1 Analog"
        alsa.id = "ALC662 rev1 Analog"
        alsa.subdevice = "0"
        alsa.subdevice_name = "subdevice #0"
        alsa.device = "0"
        alsa.card = "0"
        alsa.card_name = "HDA Intel"
        alsa.long_card_name = "HDA Intel at 0x902c0000 irq 22"
        alsa.driver_name = "snd_hda_intel"
        device.bus_path = "pci-0000:00:1b.0"
        sysfs.path = "/devices/pci0000:00/0000:00:1b.0/sound/card0"
        device.bus = "pci"
        device.vendor.id = "8086"
        device.vendor.name = "Intel Corporation"
        device.product.id = "27d8"
        device.product.name = "N10/ICH 7 Family High Definition Audio Controller"
        device.form_factor = "internal"
        device.string = "front:0"
        device.buffering.buffer_size = "352768"
        device.buffering.fragment_size = "176384"
        device.access_mode = "mmap+timer"
        device.profile.name = "analog-stereo"
        device.profile.description = "Analog Stereo"
        device.description = "Internal Audio Analog Stereo"
        alsa.mixer_name = "Realtek ALC662 rev1"
        alsa.components = "HDA:10ec0662,8086d604,00100101"
        module-udev-detect.discovered = "1"
        device.icon_name = "audio-card-pci"
    ports:
        analog-output: Analog Output (priority 9900)
        analog-output-headphones: Analog Headphones (priority 9000)
    active port: <analog-output>

```using this same command over ssh on another user without working sound returns:
```
1 sink(s) available.
  * index: 0
    name: <auto_null>
    driver: <module-null-sink.c>
    flags: DECIBEL_VOLUME LATENCY DYNAMIC_LATENCY
    state: SUSPENDED
    suspend cause: IDLE 
    priority: 1000
    volume: 0: 100% 1: 100%
            0: 0.00 dB 1: 0.00 dB
            balance 0.00
    base volume: 100%
                 0.00 dB
    volume steps: 65537
    muted: no
    current latency: 0.00 ms
    max request: 1722 KiB
    max rewind: 1722 KiB
    monitor source: 0
    sample spec: s16le 2ch 44100Hz
    channel map: front-left,front-right
                 Stereo
    used by: 0
    linked by: 0
    configured latency: 0.00 ms; range is 0.50 .. 10000.00 ms
    module: 9
    properties:
        device.description = "Dummy Output"
        device.class = "abstract"
        device.icon_name = "audio-card"

```Obviously this "Dummy Output" seems to be the issue, however I cannot find any way to get pulseaudio to play it´s output to my soundcard. I´ve tried running pulseaudio in system mode but that didn´t help me either. Does anyone have any idea how I could get my sound working?

Edit: I´ve added the users to the audio and pulse-access groups.

Edit2: I´ve just noticed that sound does work if the SSH user is the only one playing sound at the time. However this single user can output multiple streams of audio at the same time. I´d still like to know how I can overcome this single user limitation

---

