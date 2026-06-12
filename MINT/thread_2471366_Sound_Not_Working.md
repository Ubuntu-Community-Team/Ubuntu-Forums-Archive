---
title: "Sound Not Working"
date: 2022-01-28
forum: MINT
---

### Post by Jorge_Calderon on 2022-01-28
I'm having a problem with my built-in microphone.  I can use a 3.5mm headset, but when I try to use the build-in microphone without the 3.5mm jack, I get no recording.

```

inxi -Fxxxrz
System:
  Kernel: 5.11.0-44-generic x86_64 bits: 64 compiler: N/A 
  Desktop: Cinnamon 4.6.7 wm: muffin 4.6.3 dm: LightDM 1.30.0 
  Distro: Linux Mint 20 Ulyana base: Ubuntu 20.04 focal 
Machine:
  Type: Laptop System: SAMSUNG product: 900X5N v: P05AGA serial: <filter> 
  Chassis: type: 10 serial: <filter> 
  Mobo: SAMSUNG model: NP900X5N-X01US 
  v: SGL9020A0E-C01-G001-S0001+10.0.15063 serial: <filter> 
  UEFI: American Megatrends v: P05AGA.040.180306.MK date: 03/06/2018 
Battery:
  ID-1: BAT1 charge: 23.2 Wh condition: 49.4/66.7 Wh (74%) volts: 11.2/11.5 
  model: SAMSUNG Electronics SR Real Battery type: Li-ion serial: <filter> 
  status: Discharging cycles: 649 
CPU:
  Topology: Dual Core model: Intel Core i7-7500U bits: 64 type: MT MCP 
  arch: Amber Lake rev: 9 L2 cache: 4096 KiB 
  flags: avx avx2 lm nx pae sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx 
  bogomips: 23199 
  Speed: 900 MHz min/max: 400/3500 MHz Core speeds (MHz): 1: 900 2: 900 
  3: 1498 4: 900 
Graphics:
  Device-1: Intel HD Graphics 620 vendor: Samsung Co driver: i915 v: kernel 
  bus ID: 00:02.0 chip ID: 8086:5916 
  Device-2: NVIDIA GM108M [GeForce 940MX] vendor: Samsung Co driver: nvidia 
  v: 470.86 bus ID: 01:00.0 chip ID: 10de:134d 
  Display: x11 server: X.Org 1.20.13 driver: modesetting,nvidia 
  unloaded: fbdev,nouveau,vesa resolution: 1920x1080~60Hz 
  OpenGL: renderer: NVIDIA GeForce 940MX/PCIe/SSE2 v: 4.6.0 NVIDIA 470.86 
  direct render: Yes 
Audio:
  Device-1: Intel Sunrise Point-LP HD Audio vendor: Samsung Co 
  driver: snd_hda_intel v: kernel bus ID: 00:1f.3 chip ID: 8086:9d71 
  Sound Server: ALSA v: k5.11.0-44-generic 
Network:
  Device-1: Intel Wireless 8265 / 8275 driver: iwlwifi v: kernel port: e000 
  bus ID: 02:00.0 chip ID: 8086:24fd 
  IF: wlp2s0 state: up mac: <filter> 
  IF-ID-1: docker0 state: down mac: <filter> 
Drives:
  Local Storage: total: 238.47 GiB used: 88.12 GiB (36.9%) 
  ID-1: /dev/nvme0n1 vendor: Samsung model: MZVLW256HEHP-000 
  size: 238.47 GiB speed: 31.6 Gb/s lanes: 4 serial: <filter> rev: CXB70K1Q 
  scheme: GPT 
Partition:
  ID-1: / size: 97.93 GiB used: 88.07 GiB (89.9%) fs: ext4 
  dev: /dev/nvme0n1p7 
Sensors:
  System Temperatures: cpu: 64.0 C mobo: 64.0 C gpu: nvidia temp: 48 C 
  Fan Speeds (RPM): N/A 
Repos:
  No active apt repos in: /etc/apt/sources.list 
  Active apt repos in: /etc/apt/sources.list.d/audio-recorder-ppa-focal.list 
  1: deb http://ppa.launchpad.net/audio-recorder/ppa/ubuntu focal main
  Active apt repos in: /etc/apt/sources.list.d/berglh-pulseaudio-a2dp-focal.list 
  1: deb http://ppa.launchpad.net/berglh/pulseaudio-a2dp/ubuntu focal main
  Active apt repos in: /etc/apt/sources.list.d/inkscape_dev-stable-1_1-focal.list 
  1: deb http://ppa.launchpad.net/inkscape.dev/stable-1.1/ubuntu focal main
  Active apt repos in: /etc/apt/sources.list.d/official-package-repositories.list 
  1: deb http://packages.linuxmint.com ulyana main upstream import backport
  2: deb http://archive.ubuntu.com/ubuntu focal main restricted universe multiverse
  3: deb http://archive.ubuntu.com/ubuntu focal-updates main restricted universe multiverse
  4: deb http://archive.ubuntu.com/ubuntu focal-backports main restricted universe multiverse
  5: deb http://security.ubuntu.com/ubuntu/ focal-security main restricted universe multiverse
  6: deb http://archive.canonical.com/ubuntu/ focal partner
  Active apt repos in: /etc/apt/sources.list.d/skype-stable.list 
  1: deb [arch=amd64] https://repo.skype.com/deb stable main
  Active apt repos in: /etc/apt/sources.list.d/smoser-bluetooth-focal.list 
  1: deb http://ppa.launchpad.net/smoser/bluetooth/ubuntu focal main
  Active apt repos in: /etc/apt/sources.list.d/vscode.list 
  1: deb [arch=amd64,arm64,armhf] http://packages.microsoft.com/repos/code stable main
Info:
  Processes: 262 Uptime: 8m Memory: 15.54 GiB used: 2.29 GiB (14.8%) 
  Init: systemd v: 245 runlevel: 5 Compilers: gcc: 9.3.0 alt: 7/9 
  Shell: bash v: 5.0.17 running in: gnome-terminal inxi: 3.0.38
```

```
dmesg | grep snd 
[    6.123928] snd_hda_intel 0000:00:1f.3: enabling device (0000 -> 0002)
[    6.124080] snd_hda_intel 0000:00:1f.3: bound 0000:00:02.0 (ops i915_audio_component_bind_ops [i915])
[    6.163481] snd_hda_codec_realtek hdaudioC0D0: autoconfig for ALC256: line_outs=1 (0x14/0x0/0x0/0x0/0x0) type:speaker
[    6.163486] snd_hda_codec_realtek hdaudioC0D0:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[    6.163489] snd_hda_codec_realtek hdaudioC0D0:    hp_outs=1 (0x21/0x0/0x0/0x0/0x0)
[    6.163492] snd_hda_codec_realtek hdaudioC0D0:    mono: mono_out=0x0
[    6.163493] snd_hda_codec_realtek hdaudioC0D0:    inputs:
[    6.163495] snd_hda_codec_realtek hdaudioC0D0:      Mic=0x18
[    6.163497] snd_hda_codec_realtek hdaudioC0D0:      Internal Mic=0x19
[    6.163499] snd_hda_codec_realtek hdaudioC0D0:      Internal Mic=0x12

```

```
pacmd list-sources
2 source(s) available.
    index: 0
    name: <alsa_output.pci-0000_00_1f.3.analog-stereo.monitor>
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
    sample spec: s16le 2ch 48000Hz
    channel map: front-left,front-right
                 Stereo
    used by: 0
    linked by: 0
    configured latency: 0.00 ms; range is 0.50 .. 1837.50 ms
    monitor_of: 0
    card: 0 <alsa_card.pci-0000_00_1f.3>
    module: 7
    properties:
        device.description = "Monitor of Built-in Audio Analog Stereo"
        device.class = "monitor"
        alsa.card = "0"
        alsa.card_name = "HDA Intel PCH"
        alsa.long_card_name = "HDA Intel PCH at 0xf5328000 irq 135"
        alsa.driver_name = "snd_hda_intel"
        device.bus_path = "pci-0000:00:1f.3"
        sysfs.path = "/devices/pci0000:00/0000:00:1f.3/sound/card0"
        device.bus = "pci"
        device.vendor.id = "8086"
        device.vendor.name = "Intel Corporation"
        device.product.id = "9d71"
        device.product.name = "Sunrise Point-LP HD Audio"
        device.form_factor = "internal"
        device.string = "0"
        module-udev-detect.discovered = "1"
        device.icon_name = "audio-card-pci"
  * index: 1
    name: <alsa_input.pci-0000_00_1f.3.analog-stereo>
    driver: <module-alsa-card.c>
    flags: HARDWARE HW_MUTE_CTRL HW_VOLUME_CTRL DECIBEL_VOLUME LATENCY DYNAMIC_LATENCY
    state: SUSPENDED
    suspend cause: IDLE
    priority: 9039
    volume: front-left: 65540 / 100% / 0.00 dB,   front-right: 65540 / 100% / 0.00 dB
            balance 0.00
    base volume: 6554 /  10% / -60.00 dB
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
    card: 0 <alsa_card.pci-0000_00_1f.3>
    module: 7
    properties:
        alsa.resolution_bits = "16"
        device.api = "alsa"
        device.class = "sound"
        alsa.class = "generic"
        alsa.subclass = "generic-mix"
        alsa.name = "ALC256 Analog"
        alsa.id = "ALC256 Analog"
        alsa.subdevice = "0"
        alsa.subdevice_name = "subdevice #0"
        alsa.device = "0"
        alsa.card = "0"
        alsa.card_name = "HDA Intel PCH"
        alsa.long_card_name = "HDA Intel PCH at 0xf5328000 irq 135"
        alsa.driver_name = "snd_hda_intel"
        device.bus_path = "pci-0000:00:1f.3"
        sysfs.path = "/devices/pci0000:00/0000:00:1f.3/sound/card0"
        device.bus = "pci"
        device.vendor.id = "8086"
        device.vendor.name = "Intel Corporation"
        device.product.id = "9d71"
        device.product.name = "Sunrise Point-LP HD Audio"
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
    ports:
        analog-input-internal-mic: Internal Microphone (priority 8900, latency offset 0 usec, available: unknown)
            properties:
                device.icon_name = "audio-input-microphone"
        analog-input-mic: Microphone (priority 8700, latency offset 0 usec, available: no)
            properties:
                device.icon_name = "audio-input-microphone"
    active port: <analog-input-internal-mic>
```


```

pacmd list-cards
1 card(s) available.
    index: 0
    name: <alsa_card.pci-0000_00_1f.3>
    driver: <module-alsa-card.c>
    owner module: 7
    properties:
        alsa.card = "0"
        alsa.card_name = "HDA Intel PCH"
        alsa.long_card_name = "HDA Intel PCH at 0xf5328000 irq 135"
        alsa.driver_name = "snd_hda_intel"
        device.bus_path = "pci-0000:00:1f.3"
        sysfs.path = "/devices/pci0000:00/0000:00:1f.3/sound/card0"
        device.bus = "pci"
        device.vendor.id = "8086"
        device.vendor.name = "Intel Corporation"
        device.product.id = "9d71"
        device.product.name = "Sunrise Point-LP HD Audio"
        device.form_factor = "internal"
        device.string = "0"
        device.description = "Built-in Audio"
        module-udev-detect.discovered = "1"
        device.icon_name = "audio-card-pci"
    profiles:
        input:analog-stereo: Analog Stereo Input (priority 32833, available: unknown)
        output:analog-stereo: Analog Stereo Output (priority 39268, available: unknown)
        output:analog-stereo+input:analog-stereo: Analog Stereo Duplex (priority 39333, available: unknown)
        output:hdmi-stereo: Digital Stereo (HDMI) Output (priority 5900, available: no)
        output:hdmi-stereo+input:analog-stereo: Digital Stereo (HDMI) Output + Analog Stereo Input (priority 5965, available: unknown)
        output:hdmi-surround: Digital Surround 5.1 (HDMI) Output (priority 800, available: no)
        output:hdmi-surround+input:analog-stereo: Digital Surround 5.1 (HDMI) Output + Analog Stereo Input (priority 865, available: unknown)
        output:hdmi-surround71: Digital Surround 7.1 (HDMI) Output (priority 800, available: no)
        output:hdmi-surround71+input:analog-stereo: Digital Surround 7.1 (HDMI) Output + Analog Stereo Input (priority 865, available: unknown)
        output:hdmi-stereo-extra1: Digital Stereo (HDMI 2) Output (priority 5700, available: no)
        output:hdmi-stereo-extra1+input:analog-stereo: Digital Stereo (HDMI 2) Output + Analog Stereo Input (priority 5765, available: unknown)
        output:hdmi-surround-extra1: Digital Surround 5.1 (HDMI 2) Output (priority 600, available: no)
        output:hdmi-surround-extra1+input:analog-stereo: Digital Surround 5.1 (HDMI 2) Output + Analog Stereo Input (priority 665, available: unknown)
        output:hdmi-surround71-extra1: Digital Surround 7.1 (HDMI 2) Output (priority 600, available: no)
        output:hdmi-surround71-extra1+input:analog-stereo: Digital Surround 7.1 (HDMI 2) Output + Analog Stereo Input (priority 665, available: unknown)
        output:hdmi-stereo-extra2: Digital Stereo (HDMI 3) Output (priority 5700, available: no)
        output:hdmi-stereo-extra2+input:analog-stereo: Digital Stereo (HDMI 3) Output + Analog Stereo Input (priority 5765, available: unknown)
        output:hdmi-surround-extra2: Digital Surround 5.1 (HDMI 3) Output (priority 600, available: no)
        output:hdmi-surround-extra2+input:analog-stereo: Digital Surround 5.1 (HDMI 3) Output + Analog Stereo Input (priority 665, available: unknown)
        output:hdmi-surround71-extra2: Digital Surround 7.1 (HDMI 3) Output (priority 600, available: no)
        output:hdmi-surround71-extra2+input:analog-stereo: Digital Surround 7.1 (HDMI 3) Output + Analog Stereo Input (priority 665, available: unknown)
        output:hdmi-stereo-extra3: Digital Stereo (HDMI 4) Output (priority 5700, available: no)
        output:hdmi-stereo-extra3+input:analog-stereo: Digital Stereo (HDMI 4) Output + Analog Stereo Input (priority 5765, available: unknown)
        output:hdmi-surround-extra3: Digital Surround 5.1 (HDMI 4) Output (priority 600, available: no)
        output:hdmi-surround-extra3+input:analog-stereo: Digital Surround 5.1 (HDMI 4) Output + Analog Stereo Input (priority 665, available: unknown)
        output:hdmi-surround71-extra3: Digital Surround 7.1 (HDMI 4) Output (priority 600, available: no)
        output:hdmi-surround71-extra3+input:analog-stereo: Digital Surround 7.1 (HDMI 4) Output + Analog Stereo Input (priority 665, available: unknown)
        output:hdmi-stereo-extra4: Digital Stereo (HDMI 5) Output (priority 5700, available: no)
        output:hdmi-stereo-extra4+input:analog-stereo: Digital Stereo (HDMI 5) Output + Analog Stereo Input (priority 5765, available: unknown)
        output:hdmi-surround-extra4: Digital Surround 5.1 (HDMI 5) Output (priority 600, available: no)
        output:hdmi-surround-extra4+input:analog-stereo: Digital Surround 5.1 (HDMI 5) Output + Analog Stereo Input (priority 665, available: unknown)
        output:hdmi-surround71-extra4: Digital Surround 7.1 (HDMI 5) Output (priority 600, available: no)
        output:hdmi-surround71-extra4+input:analog-stereo: Digital Surround 7.1 (HDMI 5) Output + Analog Stereo Input (priority 665, available: unknown)
        off: Off (priority 0, available: unknown)
    active profile: <output:analog-stereo+input:analog-stereo>
    sinks:
        alsa_output.pci-0000_00_1f.3.analog-stereo/#0: Built-in Audio Analog Stereo
    sources:
        alsa_output.pci-0000_00_1f.3.analog-stereo.monitor/#0: Monitor of Built-in Audio Analog Stereo
        alsa_input.pci-0000_00_1f.3.analog-stereo/#1: Built-in Audio Analog Stereo
    ports:
        analog-input-internal-mic: Internal Microphone (priority 8900, latency offset 0 usec, available: unknown)
            properties:
                device.icon_name = "audio-input-microphone"
        analog-input-mic: Microphone (priority 8700, latency offset 0 usec, available: no)
            properties:
                device.icon_name = "audio-input-microphone"
        analog-output-speaker: Speakers (priority 10000, latency offset 0 usec, available: unknown)
            properties:
                device.icon_name = "audio-speakers"
        analog-output-headphones: Headphones (priority 9900, latency offset 0 usec, available: no)
            properties:
                device.icon_name = "audio-headphones"
        hdmi-output-0: HDMI / DisplayPort (priority 5900, latency offset 0 usec, available: no)
            properties:
                device.icon_name = "video-display"
        hdmi-output-1: HDMI / DisplayPort 2 (priority 5800, latency offset 0 usec, available: no)
            properties:
                device.icon_name = "video-display"
        hdmi-output-2: HDMI / DisplayPort 3 (priority 5700, latency offset 0 usec, available: no)
            properties:
                device.icon_name = "video-display"
        hdmi-output-3: HDMI / DisplayPort 4 (priority 5600, latency offset 0 usec, available: no)
            properties:
                device.icon_name = "video-display"
        hdmi-output-4: HDMI / DisplayPort 5 (priority 5500, latency offset 0 usec, available: no)
            properties:
                device.icon_name = "video-display"
```

---

### Post by deadflowr on 2022-01-28
*Thread moved to **MINT***

---

