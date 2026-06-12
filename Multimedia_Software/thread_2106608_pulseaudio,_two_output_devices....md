---
title: "pulseaudio, two output devices..."
date: 2013-01-19
forum: Multimedia Software
---

### Post by wolfgentleman on 2013-01-19
I want to put communication applications such as TeamSpeak 3 or skype to my headphones (front panel) and everything else to my speakers (back panel). I was able to do it in windows, however on linux I can't seem to get it to work I managed to get simultaneous output by disabling auto mute mode. I was on the pulse audio IRC and had someone tell me: "you will have to try the multi channel stuff to see if you get different output, the controls are kind of ambiguous" but I don't understand what he was talking about let alone how to do it.
The output of:
```
amixer contents
```

Can be found at: [http://pastebin.com/YBnbcUqW](http://pastebin.com/YBnbcUqW)

---

### Post by wolfgentleman on 2013-01-19
I have it set where I am using "Analog Surround 4.0 Output + Analog Stereo Input" with 2 virtual devices:
```
pacmd load-module module-remap-sink sink_name=front_stereo master=alsa_output.pci-0000_00_05.0.analog-surround-40 channels=2 master_channel_map=front-left,front-right channel_map=front-left,front-right
```
```
pacmd load-module module-remap-sink sink_name=rear_stereo master=alsa_output.pci-0000_00_05.0.analog-surround-40 channels=2 master_channel_map=rear-left,rear-right channel_map=rear-left,rear-right
```

But it still plays it on both devices, even if I choose one of the remapped devices. I don't understand.

---

### Post by wolfgentleman on 2013-01-19
Just removed the virtual devices the re-added them but with remix set to no. Now the front audio plays on both and the rear does not play on any device.

---

### Post by wolfgentleman on 2013-01-20
bump

---

### Post by wolfgentleman on 2013-01-20
Output of: ```
pacmd list-sinks
```is:```
Welcome to PulseAudio! Use "help" for usage information.
>>> 3 sink(s) available.
    index: 4
        name: <alsa_output.pci-0000_00_05.0.analog-surround-40>
        driver: <module-alsa-card.c>
        flags: HARDWARE HW_MUTE_CTRL HW_VOLUME_CTRL DECIBEL_VOLUME LATENCY 
        state: RUNNING
        suspend cause: 
        priority: 9959
        volume: 0: 100% 1: 100% 2: 100% 3: 100%
                0: 0.00 dB 1: 0.00 dB 2: 0.00 dB 3: 0.00 dB
                balance 0.00
        base volume: 100%
                     0.00 dB
        volume steps: 65537
        muted: no
        current latency: 80.16 ms
        max request: 27 KiB
        max rewind: 27 KiB
        monitor source: 5
        sample spec: s16le 4ch 44100Hz
        channel map: front-left,front-right,rear-left,rear-right
                     Surround 4.0
        used by: 2
        linked by: 5
        fixed latency: 80.18 ms
        card: 0 <alsa_card.pci-0000_00_05.0>
        module: 4
        properties:
                alsa.resolution_bits = "16"
                device.api = "alsa"
                device.class = "sound"
                alsa.class = "generic"
                alsa.subclass = "generic-mix"
                alsa.name = "ALC888 Analog"
                alsa.id = "ALC888 Analog"
                alsa.subdevice = "0"
                alsa.subdevice_name = "subdevice #0"
                alsa.device = "0"
                alsa.card = "0"
                alsa.card_name = "HDA NVidia"
                alsa.long_card_name = "HDA NVidia at 0xdfd78000 irq 35"
                alsa.driver_name = "snd_hda_intel"
                device.bus_path = "pci-0000:00:05.0"
                sysfs.path = "/devices/pci0000:00/0000:00:05.0/sound/card0"
                device.bus = "pci"
                device.vendor.id = "10de"
                device.vendor.name = "NVIDIA Corporation"
                device.product.name = "MCP61 High Definition Audio"
                device.form_factor = "internal"
                device.string = "surround40:0"
                device.buffering.buffer_size = "28288"
                device.buffering.fragment_size = "2176"
                device.access_mode = "mmap"
                device.profile.name = "analog-surround-40"
                device.profile.description = "Analog Surround 4.0"
                device.description = "Built-in Audio Analog Surround 4.0"
                alsa.mixer_name = "Realtek ALC888"
                alsa.components = "HDA:10ec0888,14627309,00100202"
                module-udev-detect.discovered = "1"
                device.icon_name = "audio-card-pci"
        ports:
                analog-output: Analog Output (priority 9900, available: unknown)
                        properties:

        active port: <analog-output>
    index: 9
        name: <front_stereo>
        driver: <module-remap-sink.c>
        flags: DECIBEL_VOLUME LATENCY 
        state: RUNNING
        suspend cause: 
        priority: 1000
        volume: 0: 100% 1: 100%
                0: 0.00 dB 1: 0.00 dB
                balance 0.00
        base volume: 100%
                     0.00 dB
        volume steps: 65537
        muted: no
        current latency: 80.15 ms
        max request: 13 KiB
        max rewind: 13 KiB
        monitor source: 10
        sample spec: s16le 2ch 44100Hz
        channel map: front-left,front-right
                     Stereo
        used by: 1
        linked by: 3
        fixed latency: 80.18 ms
        module: 26
        properties:
                device.master_device = "alsa_output.pci-0000_00_05.0.analog-surround-40"
                device.class = "filter"
                device.description = "Remapped Built-in Audio Analog Surround 4.0"
                device.icon_name = "audio-card"
    index: 10
        name: <rear_stereo>
        driver: <module-remap-sink.c>
        flags: DECIBEL_VOLUME LATENCY 
        state: RUNNING
        suspend cause: 
        priority: 1000
        volume: 0: 100% 1: 100%
                0: -0.00 dB 1: -0.00 dB
                balance 0.00
        base volume: 100%
                     0.00 dB
        volume steps: 65537
        muted: no
        current latency: 80.17 ms
        max request: 13 KiB
        max rewind: 13 KiB
        monitor source: 11
        sample spec: s16le 2ch 44100Hz
        channel map: rear-left,rear-right
        used by: 1
        linked by: 3
        fixed latency: 80.18 ms
        module: 27
        properties:
                device.master_device = "alsa_output.pci-0000_00_05.0.analog-surround-40"
                device.class = "filter"
                device.description = "Remapped Built-in Audio Analog Surround 4.0"
                device.icon_name = "audio-card"
>>>
```

---

### Post by wolfgentleman on 2013-01-21
bump

---

### Post by wolfgentleman on 2013-01-23
bump

---

### Post by Yellow Pasque on 2013-01-23
I think you're getting confused with front/rear thinking that it means front or rear jacks when it really means front speakers and rear speakers in a surround speaker setup (at least, that's what it looks like).

Are you using USB headphones or do you have regular headphones plugged into the headphone jack?

---

### Post by wolfgentleman on 2013-01-24
Both the speakers and the headset are the 3.5mm jacks.

I put it on Analog Stereo Duplex and used pacmd list-sinks and got the following output:

```
Welcome to PulseAudio! Use "help" for usage information.
>>> 1 sink(s) available.
    index: 2
        name: <alsa_output.pci-0000_00_05.0.analog-stereo>
        driver: <module-alsa-card.c>
        flags: HARDWARE HW_MUTE_CTRL HW_VOLUME_CTRL DECIBEL_VOLUME LATENCY 
        state: SUSPENDED
        suspend cause: IDLE 
        priority: 9959
        volume: 0: 100% 1: 100%
                0: 0.00 dB 1: 0.00 dB
                balance 0.00
        base volume: 100%
                     0.00 dB
        volume steps: 65537
        muted: no
        current latency: 0.00 ms
        max request: 0 KiB
        max rewind: 0 KiB
        monitor source: 3
        sample spec: s16le 2ch 44100Hz
        channel map: front-left,front-right
                     Stereo
        used by: 0
        linked by: 0
        fixed latency: 79.82 ms
        card: 0 <alsa_card.pci-0000_00_05.0>
        module: 4
        properties:
                alsa.resolution_bits = "16"
                device.api = "alsa"
                device.class = "sound"
                alsa.class = "generic"
                alsa.subclass = "generic-mix"
                alsa.name = "ALC888 Analog"
                alsa.id = "ALC888 Analog"
                alsa.subdevice = "0"
                alsa.subdevice_name = "subdevice #0"
                alsa.device = "0"
                alsa.card = "0"
                alsa.card_name = "HDA NVidia"
                alsa.long_card_name = "HDA NVidia at 0xdfd78000 irq 35"
                alsa.driver_name = "snd_hda_intel"
                device.bus_path = "pci-0000:00:05.0"
                sysfs.path = "/devices/pci0000:00/0000:00:05.0/sound/card0"
                device.bus = "pci"
                device.vendor.id = "10de"
                device.vendor.name = "NVIDIA Corporation"
                device.product.name = "MCP61 High Definition Audio"
                device.form_factor = "internal"
                device.string = "front:0"
                device.buffering.buffer_size = "14080"
                device.buffering.fragment_size = "1408"
                device.access_mode = "mmap"
                device.profile.name = "analog-stereo"
                device.profile.description = "Analog Stereo"
                device.description = "Built-in Audio Analog Stereo"
                alsa.mixer_name = "Realtek ALC888"
                alsa.components = "HDA:10ec0888,14627309,00100202"
                module-udev-detect.discovered = "1"
                device.icon_name = "audio-card-pci"
        ports:
                analog-output: Analog Output (priority 9900, available: unknown)
                        properties:

                analog-output-headphones: Headphones (priority 9000, available: yes)
                        properties:

        active port: <analog-output-headphones>
>>>
```

I tested both ports and they both played on both devices.

---

### Post by wolfgentleman on 2013-01-25
bump

---

### Post by wolfgentleman on 2013-11-21
Ok, after all this time I finally figured out why it's not working, but not how to fix it. On Windows in Realtek HD Audio Manager there is a separate front and rear panels that you have to check. I will post a screenshot within 2 days.

---

### Post by jamesisin on 2013-11-21
I think Temüjin was correct in his assessment.  That being said, it would appear that the current driver is not offering the same granular control over the hardware as was the driver present in Windows.

If you are able to discover to which device these two jacks connect, then you can perhaps find a better driver (or possibly change some setting relating to the current driver).

---

