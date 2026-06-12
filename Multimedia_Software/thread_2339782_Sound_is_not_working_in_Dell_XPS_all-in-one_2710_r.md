---
title: "Sound is not working in Dell XPS all-in-one 2710 running Ubuntu 16.04"
date: 2016-10-12
forum: Multimedia Software
---

### Post by karam3 on 2016-10-12
Specifications

        PC: Dell XPS all-in-one 2710
        OS: Ubuntu 16.04

The sound from my speakers is not working by default until I install QasMixer or GNOME ALSA Mixer.

When I open gnome-alsamixer I find the speakers are not muted, and the headphones are muted. If I make the headphones unmuted, the speakers work, but I have to do that again every time I start up the computer.

Below is the output of lspci -nnk | grep -A Audio and aplay -l and pactl list sinks
linux@linux-XPS-One-2710:~$ lspci -nnk | grep -A Audio
grep: Audio: invalid context length argument  

linux@linux-XPS-One-2710:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: ALC3260 Analog [ALC3260 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

[HTML]linux@linux-XPS-One-2710:~$ pactl list sinks
Sink #0
    State: RUNNING
    Name: alsa_output.pci-0000_00_1b.0.analog-stereo
    Description: Built-in Audio Analog Stereo
    Driver: module-alsa-card.c
    Sample Specification: s16le 2ch 44100Hz
    Channel Map: front-left,front-right
    Owner Module: 6
    Mute: no
    Volume: front-left: 65536 / 100% / 0.00 dB,   front-right: 65536 / 100% / 0.00 dB
            balance 0.00
    Base Volume: 63069 /  96% / -1.00 dB
    Monitor Source: alsa_output.pci-0000_00_1b.0.analog-stereo.monitor
    Latency: 50769 usec, configured 56000 usec
    Flags: HARDWARE HW_MUTE_CTRL HW_VOLUME_CTRL DECIBEL_VOLUME LATENCY 
    Properties:
        alsa.resolution_bits = "16"
        device.api = "alsa"
        device.class = "sound"
        alsa.class = "generic"
        alsa.subclass = "generic-mix"
        alsa.name = "ALC3260 Analog"
        alsa.id = "ALC3260 Analog"
        alsa.subdevice = "0"
        alsa.subdevice_name = "subdevice #0"
        alsa.device = "0"
        alsa.card = "0"
        alsa.card_name = "HDA Intel PCH"
        alsa.long_card_name = "HDA Intel PCH at 0xf7c10000 irq 36"
        alsa.driver_name = "snd_hda_intel"
        device.bus_path = "pci-0000:00:1b.0"
        sysfs.path = "/devices/pci0000:00/0000:00:1b.0/sound/card0"
        device.bus = "pci"
        device.vendor.id = "8086"
        device.vendor.name = "Intel Corporation"
        device.product.id = "1e20"
        device.product.name = "7 Series/C210 Series Chipset Family High Definition Audio Controller"
        device.form_factor = "internal"
        device.string = "front:0"
        device.buffering.buffer_size = "65536"
        device.buffering.fragment_size = "32768"
        device.access_mode = "mmap+timer"
        device.profile.name = "analog-stereo"
        device.profile.description = "Analog Stereo"
        device.description = "Built-in Audio Analog Stereo"
        alsa.mixer_name = "Realtek ALC3260"
        alsa.components = "HDA:10ec0275,1028054b,00100008 HDA:80862806,80860101,00100000"
        module-udev-detect.discovered = "1"
        device.icon_name = "audio-card-pci"
    Ports:
        analog-output-speaker: Speakers (priority: 10000)
        analog-output-headphones: Headphones (priority: 9000, not available)
    Active Port: analog-output-speaker
    Formats:
        pcm[/HTML]

---

