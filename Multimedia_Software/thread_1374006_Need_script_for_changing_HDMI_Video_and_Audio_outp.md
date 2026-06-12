---
title: "Need script for changing HDMI Video and Audio output"
date: 2010-01-06
forum: Multimedia Software
---

### Post by Audiophil on 2010-01-06
Hi there, 
I am interested in a script which adjusts my NVIDIA settings to HDMI and also my Audio output to my digital output. I feel its quite a lot of clicking to get my signal to my LCD.

So I hope somebody already had this idea and can give me the script or can assist me in writing it myself. I think its not a complicated script. i guess its only 2 lines. But i am not exactly a pro in Ubuntu..

So as i said i have a NVIDIA graphic card
and aplay -l  shows

**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC1200 Analog [ALC1200 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC1200 Digital [ALC1200 Digital]
  Subdevices: 0/1
  Subdevice #0: subdevice #0

so it should be over the second one when i run the script.
Thanks in advance

---

### Post by erktheerk on 2010-04-09
Bump

I am trying to find a script to quickly change between HDMI audio output and Avnera USB cordless headset for Skype. [http://share.skype.com/sites/skypegear/2009/11/skype_gear_roadtest_freetalk_f.html](http://share.skype.com/sites/skypegear/2009/11/skype_gear_roadtest_freetalk_f.html)

I have to keep Sound Preferences open on a adjacent workspace to switch between the two audio outputs when ever i receive or make a call. Unlike Windows Skype will not allow me to select a audio output other than the PulseAudio Default. Since I do not wish to have my call audio over my Television this has become quite tedious since switching to Ubuntu 9.1 Karmic. 

I hope someone can help me...point me toward something already writen that I can not find..or actually write a script. I am relative n00b but not unaware on how to do script and terminal commands. 

I found this site 
[http://vaioubuntu.wordpress.com/2009/07/08/hdmi-sound-output-switcher-for-pulseaudio/](http://vaioubuntu.wordpress.com/2009/07/08/hdmi-sound-output-switcher-for-pulseaudio/) 

and attempted to modify it with the specific audio name for my Freeagent Headset but could not get it to work

When i run* aplay -l* i get this

[B]**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: Device [Avnera Audio Device], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0[/B]


running from the script on link above

*aplay -l | grep -o -e "card [0-9]:.*[0-9]:" | sed -e "s/card \([0-9]\): \(.*\) \[.*device \([0-9]\).*/load-module module-alsa-sink device=hw:\1,\3 sink_name=\2/"*

I get this 

[B]load-module module-alsa-sink device=hw:0,0 sink_name=NVidia
load-module module-alsa-sink device=hw:0,1 sink_name=NVidia
load-module module-alsa-sink device=hw:1,3 sink_name=HDMI
load-module module-alsa-sink device=hw:2,0 sink_name=Device[/B]


and running *pacmd list-sinks* i get this

[B]**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC888 Digital [ALC888 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: Device [Avnera Audio Device], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
erk@LinuxBox:~$ list-sinks
list-sinks: command not found
erk@LinuxBox:~$ pacmd list-sinks
Welcome to PulseAudio! Use "help" for usage information.
>>> 3 sink(s) available.
    index: 0
    name: <alsa_output.pci-0000_00_07.0.analog-stereo>
    driver: <module-alsa-card.c>
    flags: HARDWARE HW_MUTE_CTRL HW_VOLUME_CTRL DECIBEL_VOLUME LATENCY DYNAMIC_LATENCY
    state: SUSPENDED
    suspend cause: IDLE 
    priority: 9959
    volume: 0:  50% 1:  50%
            0: -18.01 dB 1: -18.01 dB
            balance 0.00
    base volume: 100%
                 0.00 dB
    volume steps: 65537
    muted: no
    current latency: 0.00 ms
    max request: 64 KiB
    max rewind: 64 KiB
    monitor source: 0
    sample spec: s16le 2ch 44100Hz
    channel map: front-left,front-right
                 Stereo
    used by: 0
    linked by: 0
    configured latency: 0.00 ms; range is 56.00 .. 371.52 ms
    card: 0 <alsa_card.pci-0000_00_07.0>
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
        alsa.long_card_name = "HDA NVidia at 0xfe878000 irq 21"
        alsa.driver_name = "snd_hda_intel"
        device.bus_path = "pci-0000:00:07.0"
        sysfs.path = "/devices/pci0000:00/0000:00:07.0/sound/card0"
        device.bus = "pci"
        device.vendor.id = "10de"
        device.vendor.name = "nVidia Corporation"
        device.product.id = "0774"
        device.product.name = "MCP72XE/MCP72P/MCP78U/MCP78S High Definition Audio"
        device.form_factor = "internal"
        device.string = "front:0"
        device.buffering.buffer_size = "65536"
        device.buffering.fragment_size = "32768"
        device.access_mode = "mmap+timer"
        device.profile.name = "analog-stereo"
        device.profile.description = "Analog Stereo"
        device.description = "Internal Audio Analog Stereo"
        alsa.mixer_name = "Realtek ALC888"
        alsa.components = "HDA:10ec0888,103c2a93,00100202"
        module-udev-detect.discovered = "1"
        device.icon_name = "audio-card-pci"
    ports:
        analog-output: Analog Output (priority 10000)
        analog-output-headphones: Analog Headphones (priority 9000)
    active port: <analog-output>
  * index: 1
    name: <alsa_output.pci-0000_02_00.1.hdmi-stereo>
    driver: <module-alsa-card.c>
    flags: HARDWARE DECIBEL_VOLUME LATENCY DYNAMIC_LATENCY
    state: SUSPENDED
    suspend cause: IDLE 
    priority: 9050
    volume: 0: 100% 1: 100%
            0: 0.00 dB 1: 0.00 dB
            balance 0.00
    base volume: 100%
                 0.00 dB
    volume steps: 65537
    muted: no
    current latency: 0.00 ms
    max request: 64 KiB
    max rewind: 64 KiB
    monitor source: 2
    sample spec: s16le 2ch 44100Hz
    channel map: front-left,front-right
                 Stereo
    used by: 0
    linked by: 0
    configured latency: 0.00 ms; range is 46.00 .. 371.52 ms
    card: 1 <alsa_card.pci-0000_02_00.1>
    module: 5
    properties:
        alsa.resolution_bits = "16"
        device.api = "alsa"
        device.class = "sound"
        alsa.class = "generic"
        alsa.subclass = "generic-mix"
        alsa.name = "ATI HDMI"
        alsa.id = "ATI HDMI"
        alsa.subdevice = "0"
        alsa.subdevice_name = "subdevice #0"
        alsa.device = "3"
        alsa.card = "1"
        alsa.card_name = "HDA ATI HDMI"
        alsa.long_card_name = "HDA ATI HDMI at 0xfeaec000 irq 18"
        alsa.driver_name = "snd_hda_intel"
        device.bus_path = "pci-0000:02:00.1"
        sysfs.path = "/devices/pci0000:00/0000:00:10.0/0000:02:00.1/sound/card1"
        device.bus = "pci"
        device.vendor.id = "1002"
        device.vendor.name = "ATI Technologies Inc"
        device.product.id = "aa38"
        device.product.name = "R700 Audio Device [Radeon HD 4000 Series]"
        device.string = "hdmi:1"
        device.buffering.buffer_size = "65536"
        device.buffering.fragment_size = "32768"
        device.access_mode = "mmap+timer"
        device.profile.name = "hdmi-stereo"
        device.profile.description = "Digital Stereo (HDMI)"
        device.description = "R700 Audio Device [Radeon HD 4000 Series] Digital Stereo (HDMI)"
        alsa.mixer_name = "ATI R6xx HDMI"
        alsa.components = "HDA:1002aa01,00aa0100,00100100"
        module-udev-detect.discovered = "1"
        device.icon_name = "audio-card-pci"
    index: 2
    name: <alsa_output.usb-Avnera_Audio_Device_Avnera_Audio_Device-00.analog-stereo>
    driver: <module-alsa-card.c>
    flags: HARDWARE HW_MUTE_CTRL HW_VOLUME_CTRL DECIBEL_VOLUME LATENCY DYNAMIC_LATENCY
    state: SUSPENDED
    suspend cause: IDLE 
    priority: 9049
    volume: 0:  58% 1:  58%
            0: -14.00 dB 1: -14.00 dB
            balance 0.00
    base volume: 126%
                 6.00 dB
    volume steps: 65537
    muted: no
    current latency: 0.00 ms
    max request: 344 KiB
    max rewind: 344 KiB
    monitor source: 3
    sample spec: s16le 2ch 44100Hz
    channel map: front-left,front-right
                 Stereo
    used by: 0
    linked by: 0
    configured latency: 0.00 ms; range is 46.00 .. 2000.00 ms
    card: 2 <alsa_card.usb-Avnera_Audio_Device_Avnera_Audio_Device-00>
    module: 20
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
        alsa.card_name = "Avnera Audio Device"
        alsa.long_card_name = "Avnera Audio Device Avnera Audio Device at usb-0000:00:02.0-6, full speed"
        alsa.driver_name = "snd_usb_audio"
        device.bus_path = "pci-0000:00:02.0-usb-0:6:1.0"
        sysfs.path = "/devices/pci0000:00/0000:00:02.0/usb3/3-6/3-6:1.0/sound/card2"
        udev.id = "usb-Avnera_Audio_Device_Avnera_Audio_Device-00"
        device.bus = "usb"
        device.vendor.id = "170d"
        device.vendor.name = "Avnera"
        device.product.id = "0001"
        device.product.name = "Avnera_Audio_Device"
        device.serial = "Avnera_Audio_Device_Avnera_Audio_Device"
        device.string = "hw:2"
        device.buffering.buffer_size = "352800"
        device.buffering.fragment_size = "176400"
        device.access_mode = "mmap+timer"
        device.profile.name = "analog-stereo"
        device.profile.description = "Analog Stereo"
        device.description = "Avnera_Audio_Device Analog Stereo"
        alsa.mixer_name = "USB Mixer"
        alsa.components = "USB170d:0001"
        module-udev-detect.discovered = "1"
        device.icon_name = "audio-card-usb"[/B]

---

