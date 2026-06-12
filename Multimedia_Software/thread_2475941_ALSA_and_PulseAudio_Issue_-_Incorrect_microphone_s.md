---
title: "ALSA and PulseAudio Issue - Incorrect microphone selected when running pactl set-card"
date: 2022-06-12
forum: Multimedia Software
---

### Post by nectarinebandit on 2022-06-12
When I first start my laptop, which is running Ubuntu 22.04, and I run _pacmd list-sources_ I get 3 options for sources. For brevity, I use this command for shorter output: _pacmd list-sources | grep -e index -e name: -e muted -e device.description_

```
pacmd list-sources | grep -e index -e name: -e muted -e device.description
    index: 0
    name: <alsa_output.pci-0000_01_00.1.hdmi-stereo-extra1.monitor>
    muted: no
        device.description = "Monitor of GF108 High Definition Audio Controller Digital Stereo (HDMI 2)"
    index: 6
    name: <alsa_output.pci-0000_00_1b.0.analog-stereo.monitor>
    muted: no
        device.description = "Monitor of Built-in Audio Analog Stereo"
  * index: 13
    name: <alsa_input.pci-0000_00_1b.0.analog-stereo>
    muted: no
        device.description = "Built-in Audio Analog Stereo"

```

After I run _pactl set-card-profile_, now I get only 2 options. **Why is the third option (* index: 13) no longer listed?**

```
pactl set-card-profile "alsa_card.pci-0000_00_1b.0" "output:analog-stereo";


pacmd list-sources | grep -e index -e name: -e muted -e device.description
    index: 0
    name: <alsa_output.pci-0000_01_00.1.hdmi-stereo-extra1.monitor>
    muted: no
        device.description = "Monitor of GF108 High Definition Audio Controller Digital Stereo (HDMI 2)"
  * index: 6
    name: <alsa_output.pci-0000_00_1b.0.analog-stereo.monitor>
    muted: no
        device.description = "Monitor of Built-in Audio Analog Stereo"

```

To fix this, I need to open Settings > Sound and set "Input Device" to "Internal Microphone - Built-in Audio."

These are now my listed sources. The third option (now * index: 14) is listed as intended. **Why does _pactl set-card-profile_ cause only 2 sources to be listed when I want all 3 sources to be listed?**

```
pacmd list-sources | grep -e index -e name: -e muted -e device.description
    index: 0
    name: <alsa_output.pci-0000_01_00.1.hdmi-stereo-extra1.monitor>
    muted: no
        device.description = "Monitor of GF108 High Definition Audio Controller Digital Stereo (HDMI 2)"
    index: 6
    name: <alsa_output.pci-0000_00_1b.0.analog-stereo.monitor>
    muted: no
        device.description = "Monitor of Built-in Audio Analog Stereo"
  * index: 14
    name: <alsa_input.pci-0000_00_1b.0.analog-stereo>
    muted: no
        device.description = "Built-in Audio Analog Stereo"



```

The 3rd option, name: <alsa_input.pci-0000_00_1b.0.analog-stereo>, corresponds to the microphone jack on my laptop. Executing ** _pactl set-card-profile _**sets the source to a different source other than my microphone, and this is why I am asking why the 3rd option, my micropohne jack, is not listed.

---

