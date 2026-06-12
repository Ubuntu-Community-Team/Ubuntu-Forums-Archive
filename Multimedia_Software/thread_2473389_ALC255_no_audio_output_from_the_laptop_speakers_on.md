---
title: "ALC255 no audio output from the laptop speakers on Acer Predator Helios 300"
date: 2022-04-03
forum: Multimedia Software
---

### Post by dibyendu-deogharia on 2022-04-03
Hi everyone,

I have Acer Predator Helios 300. I recently installed Lubuntu but to my surprise I had no sound. I searched for the solutions and tried each and every "[SOLVED]" issues. But stil I dont have any output from my laptop speakers. I have output from the headphone jack tho.
Most recently I installed "hdajackretask" and got the status of my sound card to "RUNNING" and in the settings menu, "Speakers(Unavailable)" changed to "Speakers"


The details are as follows - 

pactl list sinks ; aplay -lSink #0
        State: RUNNING
        Name: alsa_output.pci-0000_00_1f.3.analog-stereo
        Description: Built-in Audio Analog Stereo
        Driver: module-alsa-card.c
        Sample Specification: s16le 2ch 48000Hz
        Channel Map: front-left,front-right
        Owner Module: 8
        Mute: no
        Volume: front-left: 65536 / 100% / 0.00 dB,   front-right: 65536 / 100% / 0.00 dB
                balance 0.00
        Base Volume: 65536 / 100% / 0.00 dB
        Monitor Source: alsa_output.pci-0000_00_1f.3.analog-stereo.monitor
        Latency: 39958 usec, configured 40000 usec
        Flags: HARDWARE HW_MUTE_CTRL HW_VOLUME_CTRL DECIBEL_VOLUME LATENCY 
        Properties:
                alsa.resolution_bits = "16"
                device.api = "alsa"
                device.class = "sound"
                alsa.class = "generic"
                alsa.subclass = "generic-mix"
                alsa.name = "ALC255 Analog"
                alsa.id = "ALC255 Analog"
                alsa.subdevice = "0"
                alsa.subdevice_name = "subdevice #0"
                alsa.device = "0"
                alsa.card = "0"
                alsa.card_name = "HDA Intel PCH"
                alsa.long_card_name = "HDA Intel PCH at 0xa439c000 irq 138"
                alsa.driver_name = "snd_hda_intel"
                device.bus_path = "pci-0000:00:1f.3"
                sysfs.path = "/devices/pci0000:00/0000:00:1f.3/sound/card0"
                device.bus = "pci"
                device.vendor.id = "8086"
                device.vendor.name = "Intel Corporation"
                device.product.id = "a348"
                device.product.name = "Cannon Lake PCH cAVS"
                device.form_factor = "internal"
                device.string = "front:0"
                device.buffering.buffer_size = "352800"
                device.buffering.fragment_size = "176400"
                device.access_mode = "mmap+timer"
                device.profile.name = "analog-stereo"
                device.profile.description = "Analog Stereo"
                device.description = "Built-in Audio Analog Stereo"
                module-udev-detect.discovered = "1"
                device.icon_name = "audio-card-pci"
        Ports:
                analog-output-speaker: Speakers (priority: 10000)
                analog-output-headphones: Headphones (priority: 9900)
        Active Port: analog-output-speaker
        Formats:
                pcm
**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: ALC255 Analog [ALC255 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 9: HDMI 3 [HDMI 3]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

lspci | grep -i audio
00:1f.3 Audio device: Intel Corporation Cannon Lake PCH cAVS (rev 10)
01:00.1 Audio device: NVIDIA Corporation GP107GL High Definition Audio Controller (rev a1)

Please help me with the issue as I am stuck for past 1 week with a very little success. My knowledge of linux is limited but I would love to share any more details if required to make my issue more clear. 

Thank you

---

### Post by guiverc on 2022-04-03
You've not provided any release details; if it's a LTS release; there will be two kernel stack choices available, the default stack is chosen by your installation media with Lubuntu. The relevance of this, is *drivers* are actually kernel modules; so using the other stack choice means different *drivers* will be used (*and you can have both stacks installed! though only one can be used at a time**; though use of some closed-source video drivers will prevent both kernel stacks from co-existing*).

Did you try using `pavucontrol` ?  as that's where I always start.  In the manual, the page is here - [https://manual.lubuntu.me/stable/2/2.5/2.5.2/pulseaudio_volume_control.html](https://manual.lubuntu.me/stable/2/2.5/2.5.2/pulseaudio_volume_control.html) as it provides pretty easy control for most hardware on which output device/channel is being used.

Note: *As I don't know your release, I've provided the link for the latest **stable****release which currently is Lubuntu 21.10. The URL can be adjusted if you're using a different release.*

---

