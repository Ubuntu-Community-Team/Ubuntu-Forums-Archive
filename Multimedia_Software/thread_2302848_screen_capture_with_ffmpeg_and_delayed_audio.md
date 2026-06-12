---
title: "screen capture with ffmpeg and delayed audio"
date: 2015-11-14
forum: Multimedia Software
---

### Post by dave_anderson2 on 2015-11-14
I have a live video source sent with audio to a 2nd monitor (TV). The video is captured with a Decklink SDI card and gstreamer ans has a latency of about 320Milliseconds. I use the "line-in" on the sound card to feed audio, (pulse) implement a loopback (ie. "pactl load-module module-loopback latency_msec=320"), and select HDMI as output device. I now want to screencast this, but I cannot find the syntax to tell ffmpeg to look at the output for the source, the standard >>> "ffmpeg -f alsa -i pulse ....."  command gives the live audio, not the delayed I desire. The output of pacmd follows:

```
sjl@videoeditor:~$ pacmd list-sinks
Welcome to PulseAudio! Use "help" for usage information.
>>> 2 sink(s) available.
    index: 0
    name: <alsa_output.pci-0000_06_00.1.hdmi-stereo>
    driver: <module-alsa-card.c>
    flags: HARDWARE DECIBEL_VOLUME LATENCY DYNAMIC_LATENCY
    state: RUNNING
    suspend cause: 
    priority: 9050
    volume: 0:  87% 1:  87%
            0: -3.48 dB 1: -3.48 dB
            balance 0.00
    base volume: 100%
                 0.00 dB
    volume steps: 65537
    muted: no
    current latency: 65.61 ms
    max request: 18 KiB
    max rewind: 64 KiB
    monitor source: 0
    sample spec: s16le 2ch 48000Hz
    channel map: front-left,front-right
                 Stereo
    used by: 1
    linked by: 1
    configured latency: 100.00 ms; range is 0.50 .. 341.33 ms
    card: 0 <alsa_card.pci-0000_06_00.1>
    module: 5
    properties:
        alsa.resolution_bits = "16"
        device.api = "alsa"
        device.class = "sound"
        alsa.class = "generic"
        alsa.subclass = "generic-mix"
        alsa.name = "HDMI 0"
        alsa.id = "HDMI 0"
        alsa.subdevice = "0"
        alsa.subdevice_name = "subdevice #0"
        alsa.device = "3"
        alsa.card = "1"
        alsa.card_name = "HDA ATI HDMI"
        alsa.long_card_name = "HDA ATI HDMI at 0xfbe60000 irq 60"
        alsa.driver_name = "snd_hda_intel"
        device.bus_path = "pci-0000:06:00.1"
        sysfs.path = "/devices/pci0000:00/0000:00:03.2/0000:06:00.1/sound/card1"
        device.bus = "pci"
        device.vendor.id = "1002"
        device.vendor.name = "Advanced Micro Devices, Inc. [AMD/ATI]"
        device.product.id = "aaa0"
        device.product.name = "Tahiti XT HDMI Audio [Radeon HD 7970 Series]"
        device.string = "hdmi:1"
        device.buffering.buffer_size = "65536"
        device.buffering.fragment_size = "32768"
        device.access_mode = "mmap+timer"
        device.profile.name = "hdmi-stereo"
        device.profile.description = "Digital Stereo (HDMI)"
        device.description = "Tahiti XT HDMI Audio [Radeon HD 7970 Series] Digital Stereo (HDMI)"
        alsa.mixer_name = "ATI R6xx HDMI"
        alsa.components = "HDA:1002aa01,00aa0100,00100300"
        module-udev-detect.discovered = "1"
        device.icon_name = "audio-card-pci"
    ports:
        hdmi-output-0: HDMI / DisplayPort (priority 5900, latency offset 0 usec, available: yes)
            properties:
                device.icon_name = "video-display"
                device.product.name = "VW42L HDTV10A"
    active port: <hdmi-output-0>
  * index: 1
    name: <alsa_output.pci-0000_00_1b.0.analog-stereo>
    driver: <module-alsa-card.c>
    flags: HARDWARE HW_MUTE_CTRL HW_VOLUME_CTRL DECIBEL_VOLUME LATENCY DYNAMIC_LATENCY
    state: SUSPENDED
    suspend cause: IDLE 
    priority: 9959
    volume: 0:  92% 1:  92%
            0: -2.07 dB 1: -2.07 dB
            balance 0.00
    base volume: 100%
                 0.00 dB
    volume steps: 65537
    muted: no
    current latency: 0.00 ms
    max request: 0 KiB
    max rewind: 0 KiB
    monitor source: 1
    sample spec: s16le 2ch 44100Hz
    channel map: front-left,front-right
                 Stereo
    used by: 0
    linked by: 0
    configured latency: 0.00 ms; range is 0.50 .. 371.52 ms
    card: 1 <alsa_card.pci-0000_00_1b.0>
    module: 6
    properties:
        alsa.resolution_bits = "16"
        device.api = "alsa"
        device.class = "sound"
        alsa.class = "generic"
        alsa.subclass = "generic-mix"
        alsa.name = "ALC1150 Analog"
        alsa.id = "ALC1150 Analog"
        alsa.subdevice = "0"
        alsa.subdevice_name = "subdevice #0"
        alsa.device = "0"
        alsa.card = "0"
        alsa.card_name = "HDA Intel PCH"
        alsa.long_card_name = "HDA Intel PCH at 0xfbf10000 irq 58"
        alsa.driver_name = "snd_hda_intel"
        device.bus_path = "pci-0000:00:1b.0"
        sysfs.path = "/devices/pci0000:00/0000:00:1b.0/sound/card0"
        device.bus = "pci"
        device.vendor.id = "8086"
        device.vendor.name = "Intel Corporation"
        device.product.id = "8d20"
        device.product.name = "Wellsburg HD Audio Controller"
        device.form_factor = "internal"
        device.string = "front:0"
        device.buffering.buffer_size = "65536"
        device.buffering.fragment_size = "32768"
        device.access_mode = "mmap+timer"
        device.profile.name = "analog-stereo"
        device.profile.description = "Analog Stereo"
        device.description = "Built-in Audio Analog Stereo"
        alsa.mixer_name = "Realtek ALC1150"
        alsa.components = "HDA:10ec0900,1462d885,00100001"
        module-udev-detect.discovered = "1"
        device.icon_name = "audio-card-pci"
    ports:
        analog-output: Analog Output (priority 9900, latency offset 0 usec, available: unknown)
            properties:
                
        analog-output-headphones: Headphones (priority 9000, latency offset 0 usec, available: no)
            properties:
                device.icon_name = "audio-headphones"
    active port: <analog-output>
sjl@videoeditor:~$ claer
No command 'claer' found, did you mean:
 Command 'clear' from package 'ncurses-bin' (main)
claer: command not found
sjl@videoeditor:~$ clear

sjl@videoeditor:~$ pacmd list-sinks
Welcome to PulseAudio! Use "help" for usage information.
>>> 2 sink(s) available.
    index: 0
    name: <alsa_output.pci-0000_06_00.1.hdmi-stereo>
    driver: <module-alsa-card.c>
    flags: HARDWARE DECIBEL_VOLUME LATENCY DYNAMIC_LATENCY
    state: RUNNING
    suspend cause: 
    priority: 9050
    volume: 0:  87% 1:  87%
            0: -3.48 dB 1: -3.48 dB
            balance 0.00
    base volume: 100%
                 0.00 dB
    volume steps: 65537
    muted: no
    current latency: 99.80 ms
    max request: 18 KiB
    max rewind: 64 KiB
    monitor source: 0
    sample spec: s16le 2ch 48000Hz
    channel map: front-left,front-right
                 Stereo
    used by: 1
    linked by: 1
    configured latency: 100.00 ms; range is 0.50 .. 341.33 ms
    card: 0 <alsa_card.pci-0000_06_00.1>
    module: 5
    properties:
        alsa.resolution_bits = "16"
        device.api = "alsa"
        device.class = "sound"
        alsa.class = "generic"
        alsa.subclass = "generic-mix"
        alsa.name = "HDMI 0"
        alsa.id = "HDMI 0"
        alsa.subdevice = "0"
        alsa.subdevice_name = "subdevice #0"
        alsa.device = "3"
        alsa.card = "1"
        alsa.card_name = "HDA ATI HDMI"
        alsa.long_card_name = "HDA ATI HDMI at 0xfbe60000 irq 60"
        alsa.driver_name = "snd_hda_intel"
        device.bus_path = "pci-0000:06:00.1"
        sysfs.path = "/devices/pci0000:00/0000:00:03.2/0000:06:00.1/sound/card1"
        device.bus = "pci"
        device.vendor.id = "1002"
        device.vendor.name = "Advanced Micro Devices, Inc. [AMD/ATI]"
        device.product.id = "aaa0"
        device.product.name = "Tahiti XT HDMI Audio [Radeon HD 7970 Series]"
        device.string = "hdmi:1"
        device.buffering.buffer_size = "65536"
        device.buffering.fragment_size = "32768"
        device.access_mode = "mmap+timer"
        device.profile.name = "hdmi-stereo"
        device.profile.description = "Digital Stereo (HDMI)"
        device.description = "Tahiti XT HDMI Audio [Radeon HD 7970 Series] Digital Stereo (HDMI)"
        alsa.mixer_name = "ATI R6xx HDMI"
        alsa.components = "HDA:1002aa01,00aa0100,00100300"
        module-udev-detect.discovered = "1"
        device.icon_name = "audio-card-pci"
    ports:
        hdmi-output-0: HDMI / DisplayPort (priority 5900, latency offset 0 usec, available: yes)
            properties:
                device.icon_name = "video-display"
                device.product.name = "VW42L HDTV10A"
    active port: <hdmi-output-0>
  * index: 1
    name: <alsa_output.pci-0000_00_1b.0.analog-stereo>
    driver: <module-alsa-card.c>
    flags: HARDWARE HW_MUTE_CTRL HW_VOLUME_CTRL DECIBEL_VOLUME LATENCY DYNAMIC_LATENCY
    state: SUSPENDED
    suspend cause: IDLE 
    priority: 9959
    volume: 0:  92% 1:  92%
            0: -2.07 dB 1: -2.07 dB
            balance 0.00
    base volume: 100%
                 0.00 dB
    volume steps: 65537
    muted: no
    current latency: 0.00 ms
    max request: 0 KiB
    max rewind: 0 KiB
    monitor source: 1
    sample spec: s16le 2ch 44100Hz
    channel map: front-left,front-right
                 Stereo
    used by: 0
    linked by: 0
    configured latency: 0.00 ms; range is 0.50 .. 371.52 ms
    card: 1 <alsa_card.pci-0000_00_1b.0>
    module: 6
    properties:
        alsa.resolution_bits = "16"
        device.api = "alsa"
        device.class = "sound"
        alsa.class = "generic"
        alsa.subclass = "generic-mix"
        alsa.name = "ALC1150 Analog"
        alsa.id = "ALC1150 Analog"
        alsa.subdevice = "0"
        alsa.subdevice_name = "subdevice #0"
        alsa.device = "0"
        alsa.card = "0"
        alsa.card_name = "HDA Intel PCH"
        alsa.long_card_name = "HDA Intel PCH at 0xfbf10000 irq 58"
        alsa.driver_name = "snd_hda_intel"
        device.bus_path = "pci-0000:00:1b.0"
        sysfs.path = "/devices/pci0000:00/0000:00:1b.0/sound/card0"
        device.bus = "pci"
        device.vendor.id = "8086"
        device.vendor.name = "Intel Corporation"
        device.product.id = "8d20"
        device.product.name = "Wellsburg HD Audio Controller"
        device.form_factor = "internal"
        device.string = "front:0"
        device.buffering.buffer_size = "65536"
        device.buffering.fragment_size = "32768"
        device.access_mode = "mmap+timer"
        device.profile.name = "analog-stereo"
        device.profile.description = "Analog Stereo"
        device.description = "Built-in Audio Analog Stereo"
        alsa.mixer_name = "Realtek ALC1150"
        alsa.components = "HDA:10ec0900,1462d885,00100001"
        module-udev-detect.discovered = "1"
        device.icon_name = "audio-card-pci"
    ports:
        analog-output: Analog Output (priority 9900, latency offset 0 usec, available: unknown)
            properties:
                
        analog-output-headphones: Headphones (priority 9000, latency offset 0 usec, available: no)
            properties:
                device.icon_name = "audio-headphones"
    active port: <analog-output>
>>> sjl@videoeditor:~$ 
```

I tried naming the input from the info I have : "ffmpeg -f alsa -i <alsa_output.pci-0000_06_00.1.hdmi-stereo> -f x11grab ....... etc.   to no avail. invalid input source.

I found lots of info on screencasting with multiple inputs and using sinks, etc. but not working for me. 
Any advice welcomed.

---

### Post by dave_anderson2 on 2015-11-14
The only thing I've gotten to partially function is: ```
ffmpeg -f pulse -itsoffset 0.320 -ac 2 -i default -f x11grab....
```

The resulting output will gradually cause the loopback module to lose the delay after about 1 minute of recording. The output of the ffmpeg (.mp4) has the delay constant.
I'm at a loss as to why the delay goes away....

---

### Post by dave_anderson2 on 2015-11-19
I found a workable solution... I opened a virtual sound card with :

```
pactl load-module module-loopback latency_msec="insert delay here"
```

That gave me audio at the output (speakers)

Add delay to the ffmpeg command:

```
ffmpeg -f pulse -itsoffset 0."insert delay here" -ac 2 -i default -f x11grab....
```

It works. Just DON'T have Pulse audio volume open, doing so will cause the delay to deteriorate. Dunno why, just does.

---

