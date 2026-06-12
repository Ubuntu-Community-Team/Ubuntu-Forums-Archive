---
title: "Re: Cant Use External mic, using hw mic jack"
date: 2019-01-15
forum: MINT
---

### Post by emint on 2019-01-15
[COLOR=#000000]Hi, Mi Name is Emilio, i came here (To Ubuntu father) cause i cant solve an issue in Linux Mint [/COLOR][https://forums.linuxmint.com/viewtop...?f=48&t=285121]("https://forums.linuxmint.com/viewtopic.php?f=48&t=285121")

[COLOR=#000000]The system is always recording audio from builtin mic, also if external mic is plugged, detected and selected in pulse audio input devices[/COLOR]

[COLOR=#333333]i force the headphones with this cmmd

[/COLOR][COLOR=#000000]
```

[COLOR=#2E8B57][FONT=Monaco]#Send Audio to Headphones
sudo hda-verb /dev/snd/hwC0D0 0x0f SET_PIN_WIDGET_CONTROL 0xc0
#Mute Audio of Headphones
sudo hda-verb /dev/snd/hwC0D0 0x0f SET_PIN_WIDGET_CONTROL 0x0
#Send Audio to Speakers
sudo hda-verb /dev/snd/hwC0D0 0x0b SET_PIN_WIDGET_CONTROL 0xc0
#Mute Audio of Speakers
sudo hda-verb /dev/snd/hwC0D0 0x0b SET_PIN_WIDGET_CONTROL 0x0
[/FONT][/COLOR]
```[/COLOR]
[COLOR=#333333]

[/COLOR][COLOR=#333333]but can figure out how to do the same to record from external mic, i dont undestand hda-verb

[/COLOR][COLOR=#000000]inxi -Fxz[/COLOR][COLOR=#333333]
[/COLOR][COLOR=#000000]
```

System:    Host: machinbe Kernel: 4.4.0-141-generic x86_64 (64 bit gcc: 5.4.0)
           Desktop: Cinnamon 3.4.4 (Gtk 3.18.9) Distro: Linux Mint 18 Sarah
Machine:   System: Alienware product: Alienware 15 R2 v: 1.2.14
           Mobo: Alienware model: Alienware 15 R2 v: A00 Bios: Alienware v: 1.2.14 date: 06/02/2016
CPU:       Quad core Intel Core i7-6700HQ (-HT-MCP-) cache: 6144 KB
           flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx) bmips: 20737
           clock speeds: max: 3500 MHz 1: 1768 MHz 2: 899 MHz 3: 899 MHz 4: 899 MHz 5: 899 MHz 6: 899 MHz
           7: 1341 MHz 8: 899 MHz
Graphics:  Card-1: Intel Skylake Integrated Graphics bus-ID: 00:02.0
           Card-2: NVIDIA GM204M [GeForce GTX 970M] bus-ID: 01:00.0
           Display Server: X.Org 1.18.4 drivers: intel (unloaded: fbdev,vesa) FAILED: nouveau
           Resolution: 1920x1080@60.02hz
           GLX Renderer: Mesa DRI Intel HD Graphics 530 (Skylake GT2)
           GLX Version: 3.0 Mesa 18.0.5 Direct Rendering: Yes
Audio:     Card Intel Sunrise Point-H HD Audio driver: snd_hda_intel bus-ID: 00:1f.3
           Sound: Advanced Linux Sound Architecture v: k4.4.0-141-generic
Network:   Card-1: Qualcomm Atheros Killer E2400 Gigabit Ethernet Controller
           driver: alx port: d000 bus-ID: 3b:00.0
           IF: enp59s0 state: down mac: <filter>
           Card-2: Intel Wireless 8260 driver: iwlwifi bus-ID: 3c:00.0
           IF: wlp60s0 state: up mac: <filter>
Drives:    HDD Total Size: 1000.2GB (22.6% used) ID-1: /dev/nvme0n1 model: N/A size: 256.1GB
           ID-2: /dev/nvme1n1 model: N/A size: 256.1GB ID-3: /dev/sda model: ST1000LM044_HN size: 1000.2GB
Partition: ID-1: / size: 172G used: 150G (93%) fs: ext4 dev: /dev/nvme0n1p3
           ID-2: swap-1 size: 68.72GB used: 0.00GB (0%) fs: swap dev: /dev/nvme0n1p2
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 55.0C mobo: N/A
           Fan Speeds (in rpm): cpu: N/A
Info:      Processes: 317 Uptime: 3:15 Memory: 4237.0/32042.5MB Init: systemd runlevel: 5 Gcc sys: 5.4.0
           Client: Shell (bash 4.3.481) inxi: 2.2.35

```[/COLOR]
[COLOR=#333333]

[/COLOR][COLOR=#000000]aplay -l

[/COLOR][COLOR=#000000]
```

**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: CA0132 Analog [CA0132 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```[/COLOR]```


```

[COLOR=#000000]arecord -l[/COLOR]
[COLOR=#000000]
```

**** List of CAPTURE Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: CA0132 Analog [CA0132 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 2: CA0132 Analog Mic-In2 [CA0132 Analog Mic-In2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 4: CA0132 What U Hear [CA0132 What U Hear]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```[/COLOR]

[COLOR=#000000]amixer -c0 controls | grep -i mic
[/COLOR][COLOR=#000000]
```
numid=28,iface=CARD,name='Internal Mic Phantom Jack'
numid=27,iface=CARD,name='Mic Jack'
numid=22,iface=MIXER,name='Mic SVM Capture Switch'
numid=9,iface=MIXER,name='Mic1-Boost (30dB) Capture Switch'
numid=13,iface=MIXER,name='AMic1/DMic Auto Detect Capture Switch'
numid=11,iface=MIXER,name='AMic1/DMic Capture Switch'
numid=6,iface=MIXER,name='Analog-Mic2 Capture Switch'
numid=5,iface=MIXER,name='Analog-Mic2 Capture Volume'
[/COLOR]


```

[COLOR=#000000]cat /proc/asound/card*/codec\#*
[/COLOR][COLOR=#000000]
```
Codec: Creative CA0132
Address: 0
AFG Function Id: 0x1 (unsol 1)
Vendor Id: 0x11020011
Subsystem Id: 0x10280708
Revision Id: 0x100918
No Modem Function Group found
Default PCM:
    rates [0x0]:
    bits [0x0]:
    formats [0x0]:
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
State of AFG node 0x01:
  Power states:  D0 D3 D3cold S3D3cold CLKSTOP EPSS
  Power: setting=D0, actual=D0
GPIO: io=0, o=0, i=0, unsolicited=1, wake=1
Node 0x02 [Audio Output] wcaps 0x49d: Stereo Amp-Out
  Device: name="CA0132 Analog", type="Audio", device=0
  Amp-Out caps: ofs=0x5a, nsteps=0x63, stepsize=0x03, mute=1
  Amp-Out vals:  [0x4b 0x4b]
  Converter: stream=0, channel=0
  PCM:
    rates [0x5e4]: 16000 44100 48000 88200 96000 192000
    bits [0x1f]: 8 16 20 24 32
    formats [0x1]: PCM
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x03 [Audio Output] wcaps 0x49d: Stereo Amp-Out
  Amp-Out caps: ofs=0x5a, nsteps=0x63, stepsize=0x03, mute=1
  Amp-Out vals:  [0x5a 0x5a]
  Converter: stream=0, channel=0
  PCM:
    rates [0x5e4]: 16000 44100 48000 88200 96000 192000
    bits [0x1f]: 8 16 20 24 32
    formats [0x1]: PCM
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x04 [Audio Output] wcaps 0x49d: Stereo Amp-Out
  Amp-Out caps: ofs=0x5a, nsteps=0x63, stepsize=0x03, mute=1
  Amp-Out vals:  [0x5a 0x5a]
  Converter: stream=0, channel=0
  PCM:
    rates [0x5e4]: 16000 44100 48000 88200 96000 192000
    bits [0x1f]: 8 16 20 24 32
    formats [0x1]: PCM
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x05 [Audio Output] wcaps 0x691: Stereo Digital
  Converter: stream=0, channel=0
  Digital:
  Digital category: 0x0
  IEC Coding Type: 0x0
  PCM:
    rates [0x5e0]: 44100 48000 88200 96000 192000
    bits [0x1e]: 16 20 24 32
    formats [0x5]: PCM AC3
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x06 [Audio Output] wcaps 0x691: Stereo Digital
  Converter: stream=0, channel=0
  Digital:
  Digital category: 0x0
  IEC Coding Type: 0x0
  PCM:
    rates [0x5e0]: 44100 48000 88200 96000 192000
    bits [0x1e]: 16 20 24 32
    formats [0x5]: PCM AC3
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x07 [Audio Input] wcaps 0x100591: Stereo
  Device: name="CA0132 Analog", type="Audio", device=0
  Converter: stream=0, channel=0
  SDI-Select: 0
  PCM:
    rates [0x1e4]: 16000 44100 48000 88200 96000
    bits [0x1f]: 8 16 20 24 32
    formats [0x1]: PCM
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 1
     0x12
Node 0x08 [Audio Input] wcaps 0x10059b: Stereo Amp-In
  Control: name="Analog-Mic2 Capture Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Control: name="Analog-Mic2 Capture Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Device: name="CA0132 Analog Mic-In2", type="Audio", device=2
  Amp-In caps: ofs=0x5a, nsteps=0x63, stepsize=0x03, mute=1
  Amp-In vals:  [0x5a 0x5a]
  Converter: stream=0, channel=0
  SDI-Select: 0
  PCM:
    rates [0x1e4]: 16000 44100 48000 88200 96000
    bits [0x1f]: 8 16 20 24 32
    formats [0x1]: PCM
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 1
     0x11
Node 0x09 [Audio Input] wcaps 0x100791: Stereo Digital
  Converter: stream=0, channel=0
  SDI-Select: 0
  Digital:
  Digital category: 0x0
  IEC Coding Type: 0x0
  PCM:
    rates [0x1f0]: 32000 44100 48000 88200 96000
    bits [0x1a]: 16 24 32
    formats [0x1]: PCM
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 1
     0x0e
Node 0x0a [Audio Input] wcaps 0x10079b: Stereo Digital Amp-In
  Control: name="What U Hear Capture Volume", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Control: name="What U Hear Capture Switch", index=0, device=0
    ControlAmp: chs=3, dir=In, idx=0, ofs=0
  Device: name="CA0132 What U Hear", type="Audio", device=4
  Amp-In caps: ofs=0x5a, nsteps=0x63, stepsize=0x03, mute=1
  Amp-In vals:  [0x5a 0x5a]
  Converter: stream=0, channel=0
  SDI-Select: 0
  Digital:
  Digital category: 0x0
  IEC Coding Type: 0x0
  PCM:
    rates [0x1ec]: 16000 22050 44100 48000 88200 96000
    bits [0x1b]: 8 16 24 32
    formats [0x1]: PCM
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 1
     0x13
Node 0x0b [Pin Complex] wcaps 0x400581: Stereo
  Pincap 0x00010014: OUT EAPD Detect
  EAPD 0x2: EAPD
  Pin Default 0x01014010: [Jack] Line Out at Ext Rear
    Conn = 1/8, Color = Green
    DefAssociation = 0x1, Sequence = 0x0
  Pin-ctls: 0x40: OUT
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 1
     0x02
Node 0x0c [Pin Complex] wcaps 0x400701: Stereo Digital
  Pincap 0x00000010: OUT
  Pin Default 0x014580f0: [Jack] SPDIF Out at Ext Rear
    Conn = Optical, Color = Purple
    DefAssociation = 0xf, Sequence = 0x0
  Pin-ctls: 0x00:
  Power states:  D0 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 1
     0x05
Node 0x0d [Pin Complex] wcaps 0x400701: Stereo Digital
  Pincap 0x00000010: OUT
  Pin Default 0x014570f0: [Jack] SPDIF Out at Ext Rear
    Conn = Optical, Color = Yellow
    DefAssociation = 0xf, Sequence = 0x0
  Pin-ctls: 0x00:
  Power states:  D0 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 1
     0x06
Node 0x0e [Pin Complex] wcaps 0x400681: Stereo Digital
  Pincap 0x00000020: IN
  Pin Default 0x01c530f0: [Jack] SPDIF In at Ext Rear
    Conn = Optical, Color = Blue
    DefAssociation = 0xf, Sequence = 0x0
  Pin-ctls: 0x00:
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x0f [Pin Complex] wcaps 0x400581: Stereo
  Pincap 0x0000001c: OUT HP Detect
  Pin Default 0x0221401f: [Jack] HP Out at Ext Front
    Conn = 1/8, Color = Green
    DefAssociation = 0x1, Sequence = 0xf
  Pin-ctls: 0x00:
  Unsolicited: tag=01, enabled=1
  Power states:  D0 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 1
     0x02
Node 0x10 [Pin Complex] wcaps 0x400581: Stereo
  Pincap 0x0000001c: OUT HP Detect
  Pin Default 0x02216011: [Jack] HP Out at Ext Front
    Conn = 1/8, Color = Orange
    DefAssociation = 0x1, Sequence = 0x1
  Pin-ctls: 0x00:
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 1
     0x03
Node 0x11 [Pin Complex] wcaps 0x40058b: Stereo Amp-In
  Amp-In caps: ofs=0x00, nsteps=0x03, stepsize=0x27, mute=0
  Amp-In vals:  [0x00 0x00]
  Pincap 0x00000134: IN OUT Detect
    Vref caps: HIZ
  Pin Default 0x02012014: [Jack] Line Out at Ext Front
    Conn = 1/8, Color = Grey
    DefAssociation = 0x1, Sequence = 0x4
  Pin-ctls: 0x20: IN VREF_HIZ
  Unsolicited: tag=02, enabled=1
  Power states:  D0 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 1
     0x04
Node 0x12 [Pin Complex] wcaps 0x400481: Stereo
  Control: name="Mic1-Boost (30dB) Capture Switch", index=0, device=0
    ControlAmp: chs=1, dir=In, idx=0, ofs=0
  Pincap 0x00003724: IN Detect
    Vref caps: HIZ 50 GRD 80 100
  Pin Default 0x37a791f0: [Jack] Mic at Oth Mobile-In
    Conn = Analog, Color = Pink
    DefAssociation = 0xf, Sequence = 0x0
    Misc = NO_PRESENCE
  Pin-ctls: 0x24: IN VREF_80
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x13 [Pin Complex] wcaps 0x400681: Stereo Digital
  Pincap 0x00000020: IN
  Pin Default 0x908700f0: [Fixed] Line In at Int N/A
    Conn = Analog, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
  Pin-ctls: 0x20: IN
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x14 [Beep Generator Widget] wcaps 0x70040c: Mono Amp-Out
  Amp-Out caps: ofs=0x1f, nsteps=0x1f, stepsize=0x05, mute=1
  Amp-Out vals:  [0x1c]
  Power states:  D0 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x15 [Vendor Defined Widget] wcaps 0xf00600: Mono Digital
  Power states:  D0 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x16 [Vendor Defined Widget] wcaps 0xf00680: Mono Digital
  Unsolicited: tag=03, enabled=1
  Power states:  D0 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x17 [Audio Output] wcaps 0x49d: Stereo Amp-Out
  Amp-Out caps: ofs=0x5a, nsteps=0x63, stepsize=0x03, mute=1
  Amp-Out vals:  [0x5a 0x5a]
  Converter: stream=0, channel=0
  PCM:
    rates [0x5ec]: 16000 22050 44100 48000 88200 96000 192000
    bits [0x1f]: 8 16 20 24 32
    formats [0x1]: PCM
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x18 [Pin Complex] wcaps 0x400581: Stereo
  Pincap 0x00000010: OUT
  Pin Default 0x500000f0: [N/A] Line Out at Int N/A
    Conn = Unknown, Color = Unknown
    DefAssociation = 0xf, Sequence = 0x0
  Pin-ctls: 0x00:
  Unsolicited: tag=00, enabled=0
  Power states:  D0 D3 EPSS
  Power: setting=D0, actual=D0
  Connection: 1
     0x17
Codec: Intel Skylake HDMI
Address: 2
AFG Function Id: 0x1 (unsol 0)
Vendor Id: 0x80862809
Subsystem Id: 0x80860101
Revision Id: 0x100000
No Modem Function Group found
Default PCM:
    rates [0x0]:
    bits [0x0]:
    formats [0x0]:
Default Amp-In caps: N/A
Default Amp-Out caps: N/A
State of AFG node 0x01:
  Power states:  D0 D3 CLKSTOP EPSS
  Power: setting=D0, actual=D0, Clock-stop-OK
GPIO: io=0, o=0, i=0, unsolicited=0, wake=0
Node 0x02 [Audio Output] wcaps 0x6611: 8-Channels Digital
  Converter: stream=0, channel=0
  Digital: KAE
  Digital category: 0x0
  IEC Coding Type: 0x0
  PCM:
    rates [0x7f0]: 32000 44100 48000 88200 96000 176400 192000
    bits [0x1a]: 16 24 32
    formats [0x5]: PCM AC3
  Power states:  D0 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x03 [Audio Output] wcaps 0x6611: 8-Channels Digital
  Converter: stream=0, channel=0
  Digital: Enabled KAE
  Digital category: 0x0
  IEC Coding Type: 0x0
  PCM:
    rates [0x7f0]: 32000 44100 48000 88200 96000 176400 192000
    bits [0x1a]: 16 24 32
    formats [0x5]: PCM AC3
  Power states:  D0 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x04 [Audio Output] wcaps 0x6611: 8-Channels Digital
  Converter: stream=0, channel=0
  Digital: Enabled KAE
  Digital category: 0x0
  IEC Coding Type: 0x0
  PCM:
    rates [0x7f0]: 32000 44100 48000 88200 96000 176400 192000
    bits [0x1a]: 16 24 32
    formats [0x5]: PCM AC3
  Power states:  D0 D3 EPSS
  Power: setting=D0, actual=D0
Node 0x05 [Pin Complex] wcaps 0x40778d: 8-Channels Digital Amp-Out CP
  Control: name="IEC958 Playback Con Mask", index=0, device=0
  Control: name="IEC958 Playback Pro Mask", index=0, device=0
  Control: name="IEC958 Playback Default", index=0, device=0
  Control: name="IEC958 Playback Switch", index=0, device=0
  Control: name="ELD", index=0, device=3
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x0b000094: OUT Detect HBR HDMI DP
  Pin Default 0x18560010: [Jack] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0x1, Sequence = 0x0
  Pin-ctls: 0x00:
  Unsolicited: tag=01, enabled=1
  Power states:  D0 D3 EPSS
  Power: setting=D0, actual=D0
  Devices: 0
  Connection: 0
  In-driver Connection: 3
     0x02 0x03 0x04
Node 0x06 [Pin Complex] wcaps 0x40778d: 8-Channels Digital Amp-Out CP
  Control: name="IEC958 Playback Con Mask", index=1, device=0
  Control: name="IEC958 Playback Pro Mask", index=1, device=0
  Control: name="IEC958 Playback Default", index=1, device=0
  Control: name="IEC958 Playback Switch", index=1, device=0
  Control: name="ELD", index=0, device=7
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x0b000094: OUT Detect HBR HDMI DP
  Pin Default 0x18560010: [Jack] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0x1, Sequence = 0x0
  Pin-ctls: 0x00:
  Unsolicited: tag=02, enabled=1
  Power states:  D0 D3 EPSS
  Power: setting=D0, actual=D0
  Devices: 0
  Connection: 0
  In-driver Connection: 3
     0x02 0x03 0x04
Node 0x07 [Pin Complex] wcaps 0x40778d: 8-Channels Digital Amp-Out CP
  Control: name="IEC958 Playback Con Mask", index=2, device=0
  Control: name="IEC958 Playback Pro Mask", index=2, device=0
  Control: name="IEC958 Playback Default", index=2, device=0
  Control: name="IEC958 Playback Switch", index=2, device=0
  Control: name="ELD", index=0, device=8
  Amp-Out caps: ofs=0x00, nsteps=0x00, stepsize=0x00, mute=1
  Amp-Out vals:  [0x00 0x00]
  Pincap 0x0b000094: OUT Detect HBR HDMI DP
  Pin Default 0x18560010: [Jack] Digital Out at Int HDMI
    Conn = Digital, Color = Unknown
    DefAssociation = 0x1, Sequence = 0x0
  Pin-ctls: 0x00:
  Unsolicited: tag=03, enabled=1
  Power states:  D0 D3 EPSS
  Power: setting=D0, actual=D0
  Devices: 0
  Connection: 0
  In-driver Connection: 3
     0x02 0x03 0x04
Node 0x08 [Vendor Defined Widget] wcaps 0xf00000: Mono
```
[/COLOR]
[COLOR=#000000]/etc/modprobe.d/alsa-base.conf[/COLOR]
[COLOR=#000000]
```
# autoloader aliases
install sound-slot-0 /sbin/modprobe snd-card-0
install sound-slot-1 /sbin/modprobe snd-card-1
install sound-slot-2 /sbin/modprobe snd-card-2
install sound-slot-3 /sbin/modprobe snd-card-3
install sound-slot-4 /sbin/modprobe snd-card-4
install sound-slot-5 /sbin/modprobe snd-card-5
install sound-slot-6 /sbin/modprobe snd-card-6
install sound-slot-7 /sbin/modprobe snd-card-7


# Cause optional modules to be loaded above generic modules
install snd /sbin/modprobe --ignore-install snd $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-ioctl32 ; /sbin/modprobe --quiet --use-blacklist snd-seq ; }
#
# Workaround at bug #499695 (reverted in Ubuntu see LP #319505)
install snd-pcm /sbin/modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-pcm-oss ; : ; }
install snd-mixer /sbin/modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-mixer-oss ; : ; }
install snd-seq /sbin/modprobe --ignore-install snd-seq $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; /sbin/modprobe --quiet --use-blacklist snd-seq-oss ; : ; }
#
install snd-rawmidi /sbin/modprobe --ignore-install snd-rawmidi $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq-midi ; : ; }
# Cause optional modules to be loaded above sound card driver modules
install snd-emu10k1 /sbin/modprobe --ignore-install snd-emu10k1 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-emu10k1-synth ; }
install snd-via82xx /sbin/modprobe --ignore-install snd-via82xx $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist snd-seq ; }


# Load saa7134-alsa instead of saa7134 (which gets dragged in by it anyway)
install saa7134 /sbin/modprobe --ignore-install saa7134 $CMDLINE_OPTS && { /sbin/modprobe --quiet --use-blacklist saa7134-alsa ; : ; }
# Prevent abnormal drivers from grabbing index 0
options bt87x index=-2
options cx88_alsa index=-2
options saa7134-alsa index=-2
options snd-atiixp-modem index=-2
options snd-intel8x0m index=-2
options snd-via82xx-modem index=-2
options snd-usb-audio index=-2
options snd-usb-caiaq index=-2
options snd-usb-ua101 index=-2
options snd-usb-us122l index=-2
options snd-usb-usx2y index=-2
# Ubuntu #62691, enable MPU for snd-cmipci
options snd-cmipci mpu_port=0x330 fm_port=0x388
# Keep snd-pcsp from being loaded as first soundcard
options snd-pcsp index=-2
# Keep snd-usb-audio from beeing loaded as first soundcard
options snd-usb-audio index=-2


# emi test
#alias snd-card-0 snd-hda-intel
#options snd-hda-intel model=dell-m4-1 enable_msi=1


# emi fix audio recording test 2
#rmmod snd_hda_intel
#modprobe snd_hda_intel model=generic


#other test emi
#options snd-hda-intel position_fix=1

```[/COLOR]

[ATTACH]282211[/ATTACH]

[ATTACH]282212[/ATTACH]

[http://www.mediafire.com/file/g4bl1bp509thf4g/alsa-info.txt/file](http://www.mediafire.com/file/g4bl1bp509thf4g/alsa-info.txt/file)

---

### Post by mikasu on 2019-01-15
It is common to see trrs jacks not working completely on recent hardware. I have a similar issue with my ALC283 on my laptop with 2015 hardware in it. Even very recent hardware doesn't have the best compatibility when it comes to microphones. Most of the time, if you don't have a Dell or another brand reputed to build their systems to be able to run Linux if the user wants to install it, you're screwed when it comes to full compatibility.

Try "model=dell-headset-multi" maybe, it apparently fixes some of the issues with sound chip compatibility. Don't forget to reboot to see if anything changes.

I just saw, did you try double-clicking the audio device in your distro's default control panel? (or selecting it) Or does it never shows up?

---

### Post by emint on 2019-01-15
> **mikasu said:**
> I just saw, did you try double-clicking the audio device in your distro's default control panel? (or selecting it) Or does it never shows up?

yes its selected.. here there are several trials y did [https://forums.linuxmint.com/viewtopic.php?f=48&t=285121&p=1580543#p1580543](https://forums.linuxmint.com/viewtopic.php?f=48&t=285121&p=1580543#p1580543)

---

### Post by mikasu on 2019-01-16
Okay... well, sad for you and it's actually the same end for me : buy a USB sound card that doesn't require a driver. Like UGreen USB jack adapters... There is not much we can do about the recent onboard sound chips... even when you report them to Canonical, they mostly end up in "Can't fix" state because it requires reverse engineering that not everybody is able to do. Since the USB interface is non-proprietary in any way, USB sound cards will work all the time (unless there is a driver, then you need to look for Linux compatibility). It sucks but that's what it is...

---

### Post by emint on 2019-01-16
> **mikasu said:**
> It is common to see trrs jacks not working completely on recent hardware. I have a similar issue with my ALC283 on my laptop with 2015 hardware in it. Even very recent hardware doesn't have the best compatibility when it comes to microphones. Most of the time, if you don't have a Dell or another brand reputed to build their systems to be able to run Linux if the user wants to install it, you're screwed when it comes to full compatibility.

Try "model=dell-headset-multi" maybe, it apparently fixes some of the issues with sound chip compatibility. Don't forget to reboot to see if anything changes.

like that at the end of the file?

```

alias snd-card-0 snd-hda-intel
options snd-hda-intel model=dell-headset-multi

```

didnt work

---

### Post by howefield on 2019-01-16
Thread moved to the "*MINT*" forum.

---

### Post by emint on 2019-01-17
:( this laptop is 3 years old. does it aplly to recent hw?

---

### Post by emint on 2019-01-17
i think the node is 0x07 as running  python run.py --monitor from HDA analyzer produces this output when unplugging and plugging the mic


```

 ======================================
Diff for codec 0/0 (0x11020011):
--- 
+++ 
@@ -60,17 +60,17 @@
   PCM:
     rates [0x5e0]: 44100 48000 88200 96000 192000
     bits [0x1e]: 16 20 24 32
     formats [0x5]: PCM AC3
   Unsolicited: tag=0x00, enabled=0
   Power: setting=D0, actual=D0
 Node 0x07 [Audio Input] wcaps 0x100599: Stereo
   Device: name="CA0132 Analog", type="Audio", device=0
-  Converter: stream=1, channel=0
+  Converter: stream=0, channel=0
   SDI-Select: 0
   PCM:
     rates [0x1e4]: 16000 44100 48000 88200 96000
     bits [0x1f]: 8 16 20 24 32
     formats [0x1]: PCM
   Unsolicited: tag=0x00, enabled=0
   Power: setting=D0, actual=D0
   Connection: 1
======================================
Diff for codec 0/0 (0x11020011):
--- 
+++ 
@@ -60,17 +60,17 @@
   PCM:
     rates [0x5e0]: 44100 48000 88200 96000 192000
     bits [0x1e]: 16 20 24 32
     formats [0x5]: PCM AC3
   Unsolicited: tag=0x00, enabled=0
   Power: setting=D0, actual=D0
 Node 0x07 [Audio Input] wcaps 0x100599: Stereo
   Device: name="CA0132 Analog", type="Audio", device=0
-  Converter: stream=0, channel=0
+  Converter: stream=1, channel=0
   SDI-Select: 0
   PCM:
     rates [0x1e4]: 16000 44100 48000 88200 96000
     bits [0x1f]: 8 16 20 24 32
     formats [0x1]: PCM
   Unsolicited: tag=0x00, enabled=0
   Power: setting=D0, actual=D0
   Connection: 1
======================================

```


so y tried ruuning


```

sudo hda-verb /dev/snd/hwC0D0 0x07 SET_PIN_WIDGET_CONTROL 0x24

```


but output is


```

open: Device or resource busy

```

---

### Post by mörgæs on 2019-01-22
When dealing with problems like this I recommend trying the latest Mint or Buntu release. Kernel 4.4.0 is old.

---

### Post by emint on 2019-01-23
yes u r right! but its a machine used dalily for working purposes, and it has installed an LTS version which im not supposed to update until the LTS ends :/

---

