---
title: "Audio lost after a reboot, until speaker cable is removed and reinserted"
date: 2024-04-08
forum: MINT
---

### Post by tinker123 on 2024-04-08
Mint 21.2 Victoria
Cinnamon 5.8
Intel© Core™ i7-8700K CPU @ 3.70GHz × 6
Graphics Card: NVIDIA Corporation GP107 [GeForce GTX 1050]
Mother board: ASUSTeK COMPUTER INC. PRIME Z370-P Rev X.0x

Hello,

I lose audio after rebooting my computer.   It comes back if I remove my speaker cable from the jack ( in the computer, not the monitor ) and reinsert it.

It is a nuisance I would like to get rid of. :-)

Some more information about my system:

```
Mint21.2VictoriaCinnamon5.8> inxi -Fxz
System:
  Kernel: 5.15.0-101-generic x86_64 bits: 64 compiler: gcc v: 11.4.0
    Desktop: Cinnamon 5.8.4 Distro: Linux Mint 21.2 Victoria
    base: Ubuntu 22.04 jammy
Machine:
  Type: Desktop Mobo: ASUSTeK model: PRIME Z370-P v: Rev X.0x
    serial: <superuser required> UEFI: American Megatrends v: 0606
    date: 12/12/2017
CPU:
  Info: 6-core model: Intel Core i7-8700K bits: 64 type: MT MCP
    arch: Coffee Lake rev: A cache: L1: 384 KiB L2: 1.5 MiB L3: 12 MiB
  Speed (MHz): avg: 1784 high: 4432 min/max: 800/4700 cores: 1: 2824
    2: 1844 3: 1368 4: 4432 5: 3244 6: 2308 7: 1351 8: 800 9: 800 10: 800
    11: 839 12: 800 bogomips: 88796
  Flags: avx avx2 ht lm nx pae sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx
Graphics:
  Device-1: NVIDIA GP107 [GeForce GTX 1050] vendor: Micro-Star MSI
    driver: nouveau v: kernel bus-ID: 01:00.0
  Display: x11 server: X.Org v: 1.21.1.4 driver: X: loaded: modesetting
    unloaded: fbdev,vesa gpu: nouveau resolution: 1920x1080~60Hz
  OpenGL: renderer: NV137 v: 4.3 Mesa 23.2.1-1ubuntu3.1~22.04.2
    direct render: Yes
Audio:
  Device-1: Intel 200 Series PCH HD Audio vendor: ASUSTeK
    driver: snd_hda_intel v: kernel bus-ID: 00:1f.3
  Device-2: NVIDIA GP107GL High Definition Audio vendor: Micro-Star MSI
    driver: snd_hda_intel v: kernel bus-ID: 01:00.1
  Sound Server-1: ALSA v: k5.15.0-101-generic running: yes
  Sound Server-2: PulseAudio v: 15.99.1 running: yes
  Sound Server-3: PipeWire v: 0.3.48 running: yes
Network:
  Device-1: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet
    vendor: ASUSTeK PRIME B450M-A driver: r8169 v: kernel port: d000
    bus-ID: 04:00.0
  IF: enp4s0 state: up speed: 1000 Mbps duplex: full mac: <filter>
Drives:
  Local Storage: total: 4.78 TiB used: 1.86 TiB (38.9%)
  ID-1: /dev/sda vendor: Samsung model: SSD 860 EVO 250GB size: 232.89 GiB
  ID-2: /dev/sdb type: USB vendor: Toshiba model: External USB 3.0
    size: 3.64 TiB
  ID-3: /dev/sdc type: USB vendor: Seagate model: ST1000LM022-9XV155
    size: 931.51 GiB
Partition:
  ID-1: / size: 227.68 GiB used: 69.95 GiB (30.7%) fs: ext4 dev: /dev/sda2
  ID-2: /boot/efi size: 511 MiB used: 6.1 MiB (1.2%) fs: vfat
    dev: /dev/sda1
Swap:
  ID-1: swap-1 type: file size: 2 GiB used: 0 KiB (0.0%) file: /swapfile
Sensors:
  System Temperatures: cpu: 29.8 C mobo: 27.8 C gpu: nouveau temp: 31.0 C
  Fan Speeds (RPM): N/A
Info:
  Processes: 365 Uptime: 2d 17h 18m Memory: 15.54 GiB used: 5.76 GiB (37.0%)
  Init: systemd runlevel: 5 Compilers: gcc: 11.4.0 Packages: 2707 Shell: Bash
  v: 5.1.16 inxi: 3.3.13
Mint21.2VictoriaCinnamon5.8> 
```

and ...

```
Mint21.2VictoriaCinnamon5.8>  inxi -M
Machine:
  Type: Desktop Mobo: ASUSTeK model: PRIME Z370-P v: Rev X.0x
    serial: <superuser required> UEFI: American Megatrends v: 3004
    date: 07/12/2021
Mint21.2VictoriaCinnamon5.8> 

```

and ...
```

Mint21.2VictoriaCinnamon5.8> journalctl -k | grep -Ei "ALSA|HDA|sof[-]|HDMI|snd[_-]|sound|hda.codec|hda.intel"
Apr 07 19:05:31 Wisdom kernel: ACPI: SSDT 0x00000000B8350938 000141 (v02 INTEL  HdaDsp   00000000 INTL 20160422)
Apr 07 19:05:31 Wisdom kernel: ACPI: Added _OSI(Linux-Lenovo-NV-HDMI-Audio)
Apr 07 19:05:32 Wisdom kernel: snd_hda_intel 0000:00:1f.3: enabling device (0000 -> 0002)
Apr 07 19:05:32 Wisdom kernel: snd_hda_intel 0000:01:00.1: Disabling MSI
Apr 07 19:05:32 Wisdom kernel: snd_hda_intel 0000:01:00.1: Handle vga_switcheroo audio client
Apr 07 19:05:32 Wisdom kernel: snd_hda_intel 0000:01:00.1: bound 0000:01:00.0 (ops nv50_audio_component_bind_ops [nouveau])
Apr 07 19:05:32 Wisdom kernel: snd_hda_codec_realtek hdaudioC0D0: autoconfig for ALC887-VD: line_outs=1 (0x14/0x0/0x0/0x0/0x0) type:line
Apr 07 19:05:32 Wisdom kernel: snd_hda_codec_realtek hdaudioC0D0:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
Apr 07 19:05:32 Wisdom kernel: snd_hda_codec_realtek hdaudioC0D0:    hp_outs=1 (0x1b/0x0/0x0/0x0/0x0)
Apr 07 19:05:32 Wisdom kernel: snd_hda_codec_realtek hdaudioC0D0:    mono: mono_out=0x0
Apr 07 19:05:32 Wisdom kernel: snd_hda_codec_realtek hdaudioC0D0:    dig-out=0x11/0x0
Apr 07 19:05:32 Wisdom kernel: snd_hda_codec_realtek hdaudioC0D0:    inputs:
Apr 07 19:05:32 Wisdom kernel: snd_hda_codec_realtek hdaudioC0D0:      Front Mic=0x19
Apr 07 19:05:32 Wisdom kernel: snd_hda_codec_realtek hdaudioC0D0:      Rear Mic=0x18
Apr 07 19:05:32 Wisdom kernel: snd_hda_codec_realtek hdaudioC0D0:      Line=0x1a
Apr 07 19:05:32 Wisdom kernel: input: HDA NVidia HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input7
Apr 07 19:05:32 Wisdom kernel: input: HDA NVidia HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input8
Apr 07 19:05:32 Wisdom kernel: input: HDA NVidia HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input9
Apr 07 19:05:32 Wisdom kernel: input: HDA NVidia HDMI/DP,pcm=9 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input10
Apr 07 19:05:32 Wisdom kernel: input: HDA NVidia HDMI/DP,pcm=10 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input11
Apr 07 19:05:32 Wisdom kernel: input: HDA NVidia HDMI/DP,pcm=11 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input12
Apr 07 19:05:32 Wisdom kernel: input: HDA Intel PCH Front Mic as /devices/pci0000:00/0000:00:1f.3/sound/card0/input13
Apr 07 19:05:32 Wisdom kernel: input: HDA Intel PCH Rear Mic as /devices/pci0000:00/0000:00:1f.3/sound/card0/input14
Apr 07 19:05:32 Wisdom kernel: input: HDA Intel PCH Line as /devices/pci0000:00/0000:00:1f.3/sound/card0/input15
Apr 07 19:05:32 Wisdom kernel: input: HDA Intel PCH Line Out as /devices/pci0000:00/0000:00:1f.3/sound/card0/input16
Apr 07 19:05:32 Wisdom kernel: input: HDA Intel PCH Front Headphone as /devices/pci0000:00/0000:00:1f.3/sound/card0/input17
Apr 08 08:40:45 Wisdom kernel: snd_hda_codec_hdmi hdaudioC1D0: HDMI: pin NID 0x7 not registered
Apr 08 08:45:33 Wisdom kernel: snd_hda_codec_hdmi hdaudioC1D0: HDMI: pin NID 0x7 not registered
Apr 08 09:11:02 Wisdom kernel: snd_hda_codec_hdmi hdaudioC1D0: HDMI: pin NID 0x7 not registered
Apr 08 09:19:56 Wisdom kernel: snd_hda_codec_hdmi hdaudioC1D0: HDMI: pin NID 0x7 not registered
Apr 08 09:27:16 Wisdom kernel: snd_hda_codec_hdmi hdaudioC1D0: HDMI: pin NID 0x7 not registered
Apr 08 09:40:57 Wisdom kernel: snd_hda_codec_hdmi hdaudioC1D0: HDMI: pin NID 0x7 not registered
Apr 08 09:51:46 Wisdom kernel: snd_hda_codec_hdmi hdaudioC1D0: HDMI: pin NID 0x7 not registered
Apr 08 09:58:19 Wisdom kernel: snd_hda_codec_hdmi hdaudioC1D0: HDMI: pin NID 0x7 not registered
Apr 08 10:00:47 Wisdom kernel: snd_hda_codec_hdmi hdaudioC1D0: HDMI: pin NID 0x7 not registered
Apr 08 10:04:23 Wisdom kernel: snd_hda_codec_hdmi hdaudioC1D0: HDMI: pin NID 0x7 not registered
Apr 08 10:05:31 Wisdom kernel: snd_hda_codec_hdmi hdaudioC1D0: HDMI: pin NID 0x7 not registered
Apr 08 10:13:17 Wisdom kernel: snd_hda_codec_hdmi hdaudioC1D0: HDMI: pin NID 0x7 not registered
Apr 08 10:15:07 Wisdom kernel: snd_hda_codec_hdmi hdaudioC1D0: HDMI: pin NID 0x7 not registered
Apr 08 10:22:39 Wisdom kernel: snd_hda_codec_hdmi hdaudioC1D0: HDMI: pin NID 0x7 not registered
Apr 08 10:28:23 Wisdom kernel: snd_hda_codec_hdmi hdaudioC1D0: HDMI: pin NID 0x7 not registered
Apr 08 10:31:50 Wisdom kernel: snd_hda_codec_hdmi hdaudioC1D0: HDMI: pin NID 0x7 not registered
Apr 08 10:46:02 Wisdom kernel: snd_hda_codec_hdmi hdaudioC1D0: HDMI: pin NID 0x7 not registered
Apr 08 10:48:36 Wisdom kernel: snd_hda_codec_hdmi hdaudioC1D0: HDMI: pin NID 0x7 not registered
Apr 08 10:52:45 Wisdom kernel: snd_hda_codec_hdmi hdaudioC1D0: HDMI: pin NID 0x7 not registered
Apr 08 10:54:48 Wisdom kernel: snd_hda_codec_hdmi hdaudioC1D0: HDMI: pin NID 0x7 not registered
Apr 08 11:01:50 Wisdom kernel: snd_hda_codec_hdmi hdaudioC1D0: HDMI: pin NID 0x7 not registered
Mint21.2VictoriaCinnamon5.8> 

```

and ...


```
Mint21.2VictoriaCinnamon5.8> inxi -Aa
Audio:
  Device-1: Intel 200 Series PCH HD Audio vendor: ASUSTeK
    driver: snd_hda_intel v: kernel bus-ID: 00:1f.3 chip-ID: 8086:a2f0
    class-ID: 0403
  Device-2: NVIDIA GP107GL High Definition Audio vendor: Micro-Star MSI
    driver: snd_hda_intel v: kernel pcie: gen: 1 speed: 2.5 GT/s lanes: 16
    link-max: gen: 3 speed: 8 GT/s bus-ID: 01:00.1 chip-ID: 10de:0fb9
    class-ID: 0403
  Sound Server-1: ALSA v: k5.15.0-101-generic running: yes
  Sound Server-2: PulseAudio v: 15.99.1 running: yes
  Sound Server-3: PipeWire v: 0.3.48 running: yes
Mint21.2VictoriaCinnamon5.8> 
```


after rebooting:



```
Mint21.2VictoriaCinnamon5.8> systemctl --user restart pulseaudio.service
Mint21.2VictoriaCinnamon5.8> systemctl --user restart pulseaudio.socket
Mint21.2VictoriaCinnamon5.8> inxi -Ax
Audio:
  Device-1: Intel 200 Series PCH HD Audio vendor: ASUSTeK
    driver: snd_hda_intel v: kernel bus-ID: 00:1f.3
  Device-2: NVIDIA GP107GL High Definition Audio vendor: Micro-Star MSI
    driver: snd_hda_intel v: kernel bus-ID: 01:00.1
  Sound Server-1: ALSA v: k5.15.0-101-generic running: yes
  Sound Server-2: PulseAudio v: 15.99.1 running: yes
  Sound Server-3: PipeWire v: 0.3.48 running: yes
Mint21.2VictoriaCinnamon5.8> 
```


Thanks for any help!

---

### Post by tinker123 on 2024-04-09
**Fixed**

I tried the suggestions on this[  site](https://itsfoss.com/fix-sound-ubuntu-1304-quick-tip/).

This one worked:

1. sudo apt-get install --reinstall alsa-base pulseaudio
2. sudo alsa force-reload
3. Go to your home directory and then go to the hidden config directory. Rename the directory named pulse here:
4.  mv ~/.config/pulse ~/.config/old_pulse

---

