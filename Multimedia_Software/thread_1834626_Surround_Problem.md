---
title: "Surround Problem"
date: 2011-08-27
forum: Multimedia Software
---

### Post by Zargar on 2011-08-27
I have Kubuntu 11.04 and I have a surround card and a virtual surround headphones, but both are detected as only having 2 channels, 

When I type aplay -l this is what I get
> **** Lista de Dispositivos de Hardware PLAYBACK ****
placa 0: Intel [HDA Intel], dispositivo 0: ALC889 Analog [ALC889 Analog]
  Subdispositivos: 0/1
  Subdispositivo #0: subdevice #0
placa 0: Intel [HDA Intel], dispositivo 1: ALC889 Digital [ALC889 Digital]
  Subdispositivos: 0/1
  Subdispositivo #0: subdevice #0
placa 1: G4ME1 [Sennheiser 3D G4ME1], dispositivo 0: USB Audio [USB Audio]
  Subdispositivos: 0/1
  Subdispositivo #0: subdevice #0
placa 2: Speakerphone [Logitech EasyCall Speakerphone], dispositivo 0: USB Audio [USB Audio]
  Subdispositivos: 0/1
  Subdispositivo #0: subdevice #0When I type pacmd list-sinks

> Welcome to PulseAudio! Use "help" for usage information.
>>> 3 sink(s) available.
    index: 0
        name: <alsa_output.usb-Logitech_Logitech_EasyCall_Speakerphone-00-Speakerphone.analog-stereo>
        driver: <module-alsa-card.c>
        flags: HARDWARE HW_MUTE_CTRL DECIBEL_VOLUME LATENCY DYNAMIC_LATENCY
        state: SUSPENDED
        suspend cause: IDLE 
        priority: 9549
        volume: 0: 100% 1: 100%
                0: 0,00 dB 1: 0,00 dB
                balance 0,00
        base volume: 100%
                     0,00 dB
        volume steps: 65537
        muted: no
        current latency: 0,00 ms
        max request: 0 KiB
        max rewind: 0 KiB
        monitor source: 0
        sample spec: s16le 2ch 44100Hz
        channel map: front-left,front-right
                     Estéreo
        used by: 0
        linked by: 0
        configured latency: 0,00 ms; range is 0,50 .. 2000,00 ms
        card: 0 <alsa_card.usb-Logitech_Logitech_EasyCall_Speakerphone-00-Speakerphone>
        module: 4
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
                alsa.card = "2"
                alsa.card_name = "Logitech EasyCall Speakerphone"
                alsa.long_card_name = "Logitech Logitech EasyCall Speakerphone at usb-0000:00:1a.2-2.2, full speed"
                alsa.driver_name = "snd_usb_audio"
                device.bus_path = "pci-0000:00:1a.2-usb-0:2.2:1.0"
                sysfs.path = "/devices/pci0000:00/0000:00:1a.2/usb5/5-2/5-2.2/5-2.2:1.0/sound/card2"
                udev.id = "usb-Logitech_Logitech_EasyCall_Speakerphone-00-Speakerphone"
                device.bus = "usb"
                device.vendor.id = "046d"
                device.vendor.name = "Logitech, Inc."
                device.product.id = "0a06"
                device.product.name = "Logitech EasyCall Speakerphone"
                device.serial = "Logitech_Logitech_EasyCall_Speakerphone"
                device.form_factor = "speaker"
                device.string = "front:2"
                device.buffering.buffer_size = "352800"
                device.buffering.fragment_size = "176400"
                device.access_mode = "mmap+timer"
                device.profile.name = "analog-stereo"
                device.profile.description = "Estéreo Analógico"
                device.description = "Logitech EasyCall Speakerphone Estéreo Analógico"
                alsa.mixer_name = "USB Mixer"
                alsa.components = "USB046d:0a06"
                module-udev-detect.discovered = "1"
                device.icon_name = "audio-speakers-usb"
        ports:
                analog-output;output-bass-boost-on: Entrada Analógica / Bass Boost (priority 9900)
                analog-output;output-bass-boost-off: Entrada Analógica / No Bass Boost (priority 9910)
                analog-output-speaker;output-bass-boost-on: Analog Speakers / Bass Boost (priority 10000)
                analog-output-speaker;output-bass-boost-off: Analog Speakers / No Bass Boost (priority 10010)
        active port: <analog-output-speaker;output-bass-boost-off>
  * index: 1
        name: <alsa_output.pci-0000_00_1b.0.analog-stereo>
        driver: <module-alsa-card.c>
        flags: HARDWARE HW_MUTE_CTRL HW_VOLUME_CTRL DECIBEL_VOLUME LATENCY DYNAMIC_LATENCY
        state: SUSPENDED
        suspend cause: IDLE 
        priority: 9959
        volume: 0:  25% 1:  25%
                0: -36,01 dB 1: -36,01 dB
                balance 0,00
        base volume:  86%
                     -4,00 dB
        volume steps: 65537
        muted: no
        current latency: 0,00 ms
        max request: 0 KiB
        max rewind: 0 KiB
        monitor source: 2
        sample spec: s16le 2ch 44100Hz
        channel map: front-left,front-right
                     Estéreo
        used by: 0
        linked by: 0
        configured latency: 0,00 ms; range is 0,50 .. 1999,82 ms
        card: 1 <alsa_card.pci-0000_00_1b.0>
        module: 5
        properties:
                alsa.resolution_bits = "16"
                device.api = "alsa"
                device.class = "sound"
                alsa.class = "generic"
                alsa.subclass = "generic-mix"
                alsa.name = "ALC889 Analog"
                alsa.id = "ALC889 Analog"
                alsa.subdevice = "0"
                alsa.subdevice_name = "subdevice #0"
                alsa.device = "0"
                alsa.card = "0"
                alsa.card_name = "HDA Intel"
                alsa.long_card_name = "HDA Intel at 0xf0000000 irq 54"
                alsa.driver_name = "snd_hda_intel"
                device.bus_path = "pci-0000:00:1b.0"
                sysfs.path = "/devices/pci0000:00/0000:00:1b.0/sound/card0"
                device.bus = "pci"
                device.vendor.id = "8086"
                device.vendor.name = "Intel Corporation"
                device.product.id = "3a3e"
                device.product.name = "82801JI (ICH10 Family) HD Audio Controller"
                device.form_factor = "internal"
                device.string = "front:0"
                device.buffering.buffer_size = "352768"
                device.buffering.fragment_size = "176384"
                device.access_mode = "mmap+timer"
                device.profile.name = "analog-stereo"
                device.profile.description = "Estéreo Analógico"
                device.description = "Áudio Interno Estéreo Analógico"
                alsa.mixer_name = "Realtek ALC889"
                alsa.components = "HDA:10ec0889,80860022,00100004"
                module-udev-detect.discovered = "1"
                device.icon_name = "audio-card-pci"
        ports:
                analog-output: Entrada Analógica (priority 9900)
                analog-output-speaker: Analog Speakers (priority 10000)
                analog-output-headphones: Auscultadores Analógicos (priority 9000)
        active port: <analog-output-speaker>
    index: 2
        name: <alsa_output.usb-Sennheiser_Sennheiser_3D_G4ME1-00-G4ME1.analog-stereo>
        driver: <module-alsa-card.c>
        flags: HARDWARE HW_MUTE_CTRL DECIBEL_VOLUME LATENCY DYNAMIC_LATENCY
        state: SUSPENDED
        suspend cause: IDLE 
        priority: 9049
        volume: 0: 100% 1: 100%
                0: 0,00 dB 1: 0,00 dB
                balance 0,00
        base volume: 100%
                     0,00 dB
        volume steps: 65537
        muted: no
        current latency: 0,00 ms
        max request: 0 KiB
        max rewind: 0 KiB
        monitor source: 4
        sample spec: s16le 2ch 44100Hz
        channel map: front-left,front-right
                     Estéreo
        used by: 0
        linked by: 0
        configured latency: 0,00 ms; range is 0,50 .. 2000,00 ms
        card: 2 <alsa_card.usb-Sennheiser_Sennheiser_3D_G4ME1-00-G4ME1>
        module: 6
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
                alsa.card_name = "Sennheiser 3D G4ME1"
                alsa.long_card_name = "Sennheiser Sennheiser 3D G4ME1 at usb-0000:00:1d.2-2, full speed"
                alsa.driver_name = "snd_usb_audio"
                device.bus_path = "pci-0000:00:1d.2-usb-0:2:1.0"
                sysfs.path = "/devices/pci0000:00/0000:00:1d.2/usb8/8-2/8-2:1.0/sound/card1"
                udev.id = "usb-Sennheiser_Sennheiser_3D_G4ME1-00-G4ME1"
                device.bus = "usb"
                device.vendor.id = "1395"
                device.vendor.name = "Sennheiser Communications"
                device.product.id = "1000"
                device.product.name = "Sennheiser 3D G4ME1"
                device.serial = "Sennheiser_Sennheiser_3D_G4ME1"
                device.string = "front:1"
                device.buffering.buffer_size = "352800"
                device.buffering.fragment_size = "176400"
                device.access_mode = "mmap+timer"
                device.profile.name = "analog-stereo"
                device.profile.description = "Estéreo Analógico"
                device.description = "Sennheiser 3D G4ME1 Estéreo Analógico"
                alsa.mixer_name = "USB Mixer"
                alsa.components = "USB1395:1000"
                module-udev-detect.discovered = "1"
                device.icon_name = "audio-card-usb"
        ports:
                analog-output: Entrada Analógica (priority 9900)
                analog-output-speaker: Analog Speakers (priority 10000)
        active port: <analog-output-speaker>

Any Idea on how to change the number of channels from card: 1 and 2 from only two too 6 and 8 respectively ?!

Also it was working fine a few updates ago, (the internal sound at least... now he decided i have a stereo card instead of a surround one...)

---

