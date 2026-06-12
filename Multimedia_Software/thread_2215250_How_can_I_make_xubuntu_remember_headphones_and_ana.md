---
title: "How can I make xubuntu remember headphones and analog settings?"
date: 2014-04-05
forum: Multimedia Software
---

### Post by cadogenwest on 2014-04-05
Searching through the forums, I could find results for setting default profiles and troubleshooting HDMI problems and so on. In my case, it isn't about a analog vs HDMI issue, but something within the analog profile. I need to manually switch between headphones and analog to get things working.

[CENTER][ATTACH=CONFIG]251756[/ATTACH]
(click to enlarge)

[/CENTER]
 [CENTER][COLOR=#008080]*Is there a way to automatically make Xubuntu 13.04 to remember the port settings?*[/COLOR]
[/CENTER]


[COLOR=#ff8c00]**pactl info**[/COLOR]
```
Server String: unix:/run/user/user1729/pulse/native
Library Protocol Version: 27
Server Protocol Version: 27
Is Local: yes
Client Index: 21
Tile Size: 65472
User Name: user1729
Host Name: user1729-System-Product-Name
Server Name: pulseaudio
Server Version: 3.0
Default Sample Specification: s16le 2ch 44100Hz
Default Channel Map: front-left,front-right
Default Sink: alsa_output.pci-0000_00_05.0.analog-stereo
Default Source: alsa_output.pci-0000_00_05.0.analog-stereo.monitor
Cookie: 1696:7975
user1729@user1729-System-Product-Name:~$ pactl list short sinks
0    alsa_output.pci-0000_00_05.0.analog-stereo    module-alsa-card.c    s16le 2ch 44100Hz    RUNNING
1    alsa_output.pci-0000_02_00.1.hdmi-stereo    module-alsa-card.c    s16le 2ch 44100Hz    SUSPENDED
```

[COLOR=#ff8c00]**pactl list cards**[/COLOR] 
```
Card #0
    Name: alsa_card.pci-0000_00_05.0
    Driver: module-alsa-card.c
    Owner Module: 4
    Properties:
        alsa.card = "0"
        alsa.card_name = "HDA NVidia"
        alsa.long_card_name = "HDA NVidia at 0xdfef4000 irq 22"
        alsa.driver_name = "snd_hda_intel"
        device.bus_path = "pci-0000:00:05.0"
        sysfs.path = "/devices/pci0000:00/0000:00:05.0/sound/card0"
        device.bus = "pci"
        device.vendor.id = "10de"
        device.vendor.name = "NVIDIA Corporation"
        device.product.name = "MCP61 High Definition Audio"
        device.form_factor = "internal"
        device.string = "0"
        device.description = "Built-in Audio"
        module-udev-detect.discovered = "1"
        device.icon_name = "audio-card-pci"
    Profiles:
        input:analog-stereo: Analog Stereo Input (sinks: 0, sources: 1, priority. 60)
        output:analog-stereo: Analog Stereo Output (sinks: 1, sources: 0, priority. 6000)
        output:analog-stereo+input:analog-stereo: Analog Stereo Duplex (sinks: 1, sources: 1, priority. 6060)
        output:analog-surround-40: Analog Surround 4.0 Output (sinks: 1, sources: 0, priority. 700)
        output:analog-surround-40+input:analog-stereo: Analog Surround 4.0 Output + Analog Stereo Input (sinks: 1, sources: 1, priority. 760)
        output:analog-surround-41: Analog Surround 4.1 Output (sinks: 1, sources: 0, priority. 800)
        output:analog-surround-41+input:analog-stereo: Analog Surround 4.1 Output + Analog Stereo Input (sinks: 1, sources: 1, priority. 860)
        output:analog-surround-50: Analog Surround 5.0 Output (sinks: 1, sources: 0, priority. 700)
        output:analog-surround-50+input:analog-stereo: Analog Surround 5.0 Output + Analog Stereo Input (sinks: 1, sources: 1, priority. 760)
        output:analog-surround-51: Analog Surround 5.1 Output (sinks: 1, sources: 0, priority. 800)
        output:analog-surround-51+input:analog-stereo: Analog Surround 5.1 Output + Analog Stereo Input (sinks: 1, sources: 1, priority. 860)
        output:iec958-stereo: Digital Stereo (IEC958) Output (sinks: 1, sources: 0, priority. 5500)
        output:iec958-stereo+input:analog-stereo: Digital Stereo (IEC958) Output + Analog Stereo Input (sinks: 1, sources: 1, priority. 5560)
        off: Off (sinks: 0, sources: 0, priority. 0)
    Active Profile: output:analog-stereo
    Ports:
        analog-input-microphone-front: Front Microphone (priority: 8500, latency offset: 0 usec, not available)
            Properties:
                device.icon_name = "audio-input-microphone"
            Part of profile(s): input:analog-stereo, output:analog-stereo+input:analog-stereo, output:analog-surround-40+input:analog-stereo, output:analog-surround-41+input:analog-stereo, output:analog-surround-50+input:analog-stereo, output:analog-surround-51+input:analog-stereo, output:iec958-stereo+input:analog-stereo
        analog-input-microphone-rear: Rear Microphone (priority: 8200, latency offset: 0 usec, not available)
            Properties:
                device.icon_name = "audio-input-microphone"
            Part of profile(s): input:analog-stereo, output:analog-stereo+input:analog-stereo, output:analog-surround-40+input:analog-stereo, output:analog-surround-41+input:analog-stereo, output:analog-surround-50+input:analog-stereo, output:analog-surround-51+input:analog-stereo, output:iec958-stereo+input:analog-stereo
        analog-input-linein: Line In (priority: 8100, latency offset: 0 usec, not available)
            Part of profile(s): input:analog-stereo, output:analog-stereo+input:analog-stereo, output:analog-surround-40+input:analog-stereo, output:analog-surround-41+input:analog-stereo, output:analog-surround-50+input:analog-stereo, output:analog-surround-51+input:analog-stereo, output:iec958-stereo+input:analog-stereo
        analog-output: Analog Output (priority: 9900, latency offset: 0 usec)
            Part of profile(s): output:analog-stereo, output:analog-stereo+input:analog-stereo, output:analog-surround-40, output:analog-surround-40+input:analog-stereo, output:analog-surround-41, output:analog-surround-41+input:analog-stereo, output:analog-surround-50, output:analog-surround-50+input:analog-stereo, output:analog-surround-51, output:analog-surround-51+input:analog-stereo
        analog-output-headphones: Headphones (priority: 9000, latency offset: 0 usec, not available)
            Properties:
                device.icon_name = "audio-headphones"
            Part of profile(s): output:analog-stereo, output:analog-stereo+input:analog-stereo
        iec958-stereo-output: Digital Output (S/PDIF) (priority: 0, latency offset: 0 usec)
            Part of profile(s): output:iec958-stereo, output:iec958-stereo+input:analog-stereo

Card #1
    Name: alsa_card.pci-0000_02_00.1
    Driver: module-alsa-card.c
    Owner Module: 5
    Properties:
        alsa.card = "1"
        alsa.card_name = "HD-Audio Generic"
        alsa.long_card_name = "HD-Audio Generic at 0xdffbc000 irq 43"
        alsa.driver_name = "snd_hda_intel"
        device.bus_path = "pci-0000:02:00.1"
        sysfs.path = "/devices/pci0000:00/0000:00:09.0/0000:02:00.1/sound/card1"
        device.bus = "pci"
        device.vendor.id = "1002"
        device.vendor.name = "Advanced Micro Devices [AMD] nee ATI"
        device.product.name = "Juniper HDMI Audio [Radeon HD 5700 Series]"
        device.string = "1"
        device.description = "Juniper HDMI Audio [Radeon HD 5700 Series]"
        module-udev-detect.discovered = "1"
        device.icon_name = "audio-card-pci"
    Profiles:
        output:hdmi-stereo: Digital Stereo (HDMI) Output (sinks: 1, sources: 0, priority. 5400)
        off: Off (sinks: 0, sources: 0, priority. 0)
    Active Profile: output:hdmi-stereo
    Ports:
        hdmi-output-0: HDMI / DisplayPort (priority: 5900, latency offset: 0 usec, available)
            Properties:
                device.icon_name = "video-display"
            Part of profile(s): output:hdmi-stereo


```

---

### Post by trag on 2014-04-13
this might be a partial solution,install sound switcher indicator. it will make switching a little less annoying

---

### Post by cadogenwest on 2014-04-14
It is a nice indicator, but doesn't show 'headphones'. I can only switch between analog and HDMI with it (but a nice app nonetheless).

---

