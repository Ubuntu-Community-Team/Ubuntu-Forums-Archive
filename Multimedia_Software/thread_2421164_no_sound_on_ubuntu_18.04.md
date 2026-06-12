---
title: "no sound on ubuntu 18.04"
date: 2019-06-17
forum: Multimedia Software
---

### Post by ines-k on 2019-06-17
Hello there,

I have been featsing on the wealth of information that exists on this topic. Despite all that info, I have only managed to get rid of "Dummy Output" in my sound settings to "HDMI/Display POrt - Built-in Audio" but still no sound. 

Some helpful outputs from some commands:

```
pulseaudio
```  E: [pulseaudio] pid.c: Daemon already running.  
E: [pulseaudio] main.c: pa_pid_file_create() failed.


```
lspci -nnk | grep -A2 Audio
```
00:03.0 Audio device [0403]: Intel Corporation Haswell-ULT HD Audio Controller [8086:0a0c] (rev 09)
    Subsystem: Dell Haswell-ULT HD Audio Controller [1028:05e3]
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd_hda_intel


```

inxi -GAz
```
Graphics:  Card: Intel Haswell-ULT Integrated Graphics Controller
           Display Server: x11 (X.Org 1.19.6 ) driver: i915
           Resolution: 1920x1080@59.93hz
           OpenGL: renderer: Mesa DRI Intel Haswell Mobile
           version: 4.5 Mesa 18.2.8
Audio:     Card Intel Haswell-ULT HD Audio Controller driver: snd_hda_intel
           Sound: Advanced Linux Sound Architecture v: k4.15.0-51-generic

```
aplay -l
```
**** List of PLAYBACK Hardware Devices ****
card 0: HDMI [HDA Intel HDMI], device 3: Generic Digital [Generic Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```
lsmod | grep snd
```
snd_hda_codec_hdmi     49152  0
snd_hda_codec_generic    73728  1
snd_hda_intel          45056  1
snd_hda_codec         126976  3 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_intel
snd_hda_core           81920  4 snd_hda_codec_generic,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_hwdep              20480  1 snd_hda_codec
snd_pcm                98304  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hda_core
snd_seq_midi           16384  0
snd_seq_midi_event     16384  1 snd_seq_midi
snd_rawmidi            32768  1 snd_seq_midi
snd_seq                65536  2 snd_seq_midi,snd_seq_midi_event
snd_seq_device         16384  3 snd_seq,snd_seq_midi,snd_rawmidi
snd_timer              32768  2 snd_seq,snd_pcm
snd                    81920  12 snd_hda_codec_generic,snd_seq,snd_seq_device,snd_hda_codec_hdmi,snd_hwdep,snd_hda_intel,snd_hda_codec,snd_timer,snd_pcm,snd_rawmidi
soundcore              16384  1 snd


```
pactl list
```
Module #0
    Name: module-device-restore
    Argument: 
    Usage counter: n/a
    Properties:
        module.author = "Lennart Poettering"
        module.description = "Automatically restore the volume/mute state of devices"
        module.version = "11.1"

Module #1
    Name: module-stream-restore
    Argument: 
    Usage counter: n/a
    Properties:
        module.author = "Lennart Poettering"
        module.description = "Automatically restore the volume/mute/device state of streams"
        module.version = "11.1"

Module #2
    Name: module-card-restore
    Argument: 
    Usage counter: n/a
    Properties:
        module.author = "Lennart Poettering"
        module.description = "Automatically restore profile of cards"
        module.version = "11.1"

Module #3
    Name: module-augment-properties
    Argument: 
    Usage counter: n/a
    Properties:
        module.author = "Lennart Poettering"
        module.description = "Augment the property sets of streams with additional static information"
        module.version = "11.1"

Module #4
    Name: module-switch-on-port-available
    Argument: 
    Usage counter: n/a
    Properties:
        

Module #5
    Name: module-switch-on-connect
    Argument: 
    Usage counter: n/a
    Properties:
        module.author = "Michael Terry"
        module.description = "When a sink/source is added, switch to it or conditionally switch to it"
        module.version = "11.1"

Module #6
    Name: module-udev-detect
    Argument: 
    Usage counter: n/a
    Properties:
        module.author = "Lennart Poettering"
        module.description = "Detect available audio hardware and load matching drivers"
        module.version = "11.1"

Module #7
    Name: module-native-protocol-unix
    Argument: 
    Usage counter: n/a
    Properties:
        module.author = "Lennart Poettering"
        module.description = "Native protocol (UNIX sockets)"
        module.version = "11.1"

Module #8
    Name: module-default-device-restore
    Argument: 
    Usage counter: n/a
    Properties:
        module.author = "Lennart Poettering"
        module.description = "Automatically restore the default sink and source"
        module.version = "11.1"

Module #9
    Name: module-rescue-streams
    Argument: 
    Usage counter: n/a
    Properties:
        module.author = "Lennart Poettering"
        module.description = "When a sink/source is removed, try to move its streams to the default sink/source"
        module.version = "11.1"

Module #10
    Name: module-always-sink
    Argument: 
    Usage counter: n/a
    Properties:
        module.author = "Colin Guthrie"
        module.description = "Always keeps at least one sink loaded even if it's a null one"
        module.version = "11.1"

Module #12
    Name: module-intended-roles
    Argument: 
    Usage counter: n/a
    Properties:
        module.author = "Lennart Poettering"
        module.description = "Automatically set device of streams based on intended roles of devices"
        module.version = "11.1"

Module #13
    Name: module-suspend-on-idle
    Argument: 
    Usage counter: n/a
    Properties:
        module.author = "Lennart Poettering"
        module.description = "When a sink/source is idle for too long, suspend it"
        module.version = "11.1"

Module #14
    Name: module-console-kit
    Argument: 
    Usage counter: n/a
    Properties:
        module.author = "Lennart Poettering"
        module.description = "Create a client for each ConsoleKit session of this user"
        module.version = "11.1"

Module #15
    Name: module-systemd-login
    Argument: 
    Usage counter: n/a
    Properties:
        module.author = "Lennart Poettering"
        module.description = "Create a client for each login session of this user"
        module.version = "11.1"

Module #16
    Name: module-position-event-sounds
    Argument: 
    Usage counter: n/a
    Properties:
        module.author = "Lennart Poettering"
        module.description = "Position event sounds between L and R depending on the position on screen of the widget triggering them."
        module.version = "11.1"

Module #17
    Name: module-role-cork
    Argument: 
    Usage counter: n/a
    Properties:
        module.author = "Lennart Poettering"
        module.description = "Mute & cork streams with certain roles while others exist"
        module.version = "11.1"

Module #18
    Name: module-filter-heuristics
    Argument: 
    Usage counter: n/a
    Properties:
        module.author = "Colin Guthrie"
        module.description = "Detect when various filters are desirable"
        module.version = "11.1"

Module #19
    Name: module-filter-apply
    Argument: 
    Usage counter: n/a
    Properties:
        module.author = "Colin Guthrie"
        module.description = "Load filter sinks automatically when needed"
        module.version = "11.1"

Module #20
    Name: module-x11-publish
    Argument: display=:0
    Usage counter: n/a
    Properties:
        module.author = "Lennart Poettering"
        module.description = "X11 credential publisher"
        module.version = "11.1"

Module #21
    Name: module-x11-bell
    Argument: display=:0 sample=bell.ogg
    Usage counter: n/a
    Properties:
        module.author = "Lennart Poettering"
        module.description = "X11 bell interceptor"
        module.version = "11.1"

Module #22
    Name: module-x11-cork-request
    Argument: display=:0
    Usage counter: n/a
    Properties:
        module.author = "Lennart Poettering"
        module.description = "Synthesize X11 media key events when cork/uncork is requested"
        module.version = "11.1"

Module #23
    Name: module-x11-xsmp
    Argument: display=:0 session_manager=local/cybengal:@/tmp/.ICE-unix/1470,unix/cybengal:/tmp/.ICE-unix/1470
    Usage counter: n/a
    Properties:
        module.author = "Lennart Poettering"
        module.description = "X11 session management"
        module.version = "11.1"

Module #24
    Name: module-alsa-card
    Argument: device_id="0" name="pci-0000_00_03.0" card_name="alsa_card.pci-0000_00_03.0" namereg_fail=false tsched=yes fixed_latency_range=no ignore_dB=no deferred_volume=yes use_ucm=yes card_properties="module-udev-detect.discovered=1"
    Usage counter: 0
    Properties:
        module.author = "Lennart Poettering"
        module.description = "ALSA Card"
        module.version = "11.1"

Sink #1
    State: SUSPENDED
    Name: alsa_output.pci-0000_00_03.0.hdmi-stereo
    Description: Built-in Audio Digital Stereo (HDMI)
    Driver: module-alsa-card.c
    Sample Specification: s16le 2ch 44100Hz
    Channel Map: front-left,front-right
    Owner Module: 24
    Mute: no
    Volume: front-left: 99957 / 153% / 11.00 dB,   front-right: 99957 / 153% / 11.00 dB
            balance 0.00
    Base Volume: 65536 / 100% / 0.00 dB
    Monitor Source: alsa_output.pci-0000_00_03.0.hdmi-stereo.monitor
    Latency: 0 usec, configured 0 usec
    Flags: HARDWARE DECIBEL_VOLUME LATENCY SET_FORMATS 
    Properties:
        alsa.resolution_bits = "16"
        device.api = "alsa"
        device.class = "sound"
        alsa.class = "generic"
        alsa.subclass = "generic-mix"
        alsa.name = "Generic Digital"
        alsa.id = "Generic Digital"
        alsa.subdevice = "0"
        alsa.subdevice_name = "subdevice #0"
        alsa.device = "3"
        alsa.card = "0"
        alsa.card_name = "HDA Intel HDMI"
        alsa.long_card_name = "HDA Intel HDMI at 0xf7d10000 irq 58"
        alsa.driver_name = "snd_hda_intel"
        device.bus_path = "pci-0000:00:03.0"
        sysfs.path = "/devices/pci0000:00/0000:00:03.0/sound/card0"
        device.bus = "pci"
        device.vendor.id = "8086"
        device.vendor.name = "Intel Corporation"
        device.product.id = "0a0c"
        device.product.name = "Haswell-ULT HD Audio Controller"
        device.form_factor = "internal"
        device.string = "hdmi:0"
        device.buffering.buffer_size = "65536"
        device.buffering.fragment_size = "32768"
        device.access_mode = "mmap+timer"
        device.profile.name = "hdmi-stereo"
        device.profile.description = "Digital Stereo (HDMI)"
        device.description = "Built-in Audio Digital Stereo (HDMI)"
        alsa.mixer_name = "Intel Generic"
        alsa.components = "HDA:80862807,80860101,00100000"
        module-udev-detect.discovered = "1"
        device.icon_name = "audio-card-pci"
    Ports:
        hdmi-output-0: HDMI / DisplayPort (priority: 5900)
    Active Port: hdmi-output-0
    Formats:
        pcm

Source #1
    State: SUSPENDED
    Name: alsa_output.pci-0000_00_03.0.hdmi-stereo.monitor
    Description: Monitor of Built-in Audio Digital Stereo (HDMI)
    Driver: module-alsa-card.c
    Sample Specification: s16le 2ch 44100Hz
    Channel Map: front-left,front-right
    Owner Module: 24
    Mute: no
    Volume: front-left: 65536 / 100% / 0.00 dB,   front-right: 65536 / 100% / 0.00 dB
            balance 0.00
    Base Volume: 65536 / 100% / 0.00 dB
    Monitor of Sink: alsa_output.pci-0000_00_03.0.hdmi-stereo
    Latency: 0 usec, configured 0 usec
    Flags: DECIBEL_VOLUME LATENCY 
    Properties:
        device.description = "Monitor of Built-in Audio Digital Stereo (HDMI)"
        device.class = "monitor"
        alsa.card = "0"
        alsa.card_name = "HDA Intel HDMI"
        alsa.long_card_name = "HDA Intel HDMI at 0xf7d10000 irq 58"
        alsa.driver_name = "snd_hda_intel"
        device.bus_path = "pci-0000:00:03.0"
        sysfs.path = "/devices/pci0000:00/0000:00:03.0/sound/card0"
        device.bus = "pci"
        device.vendor.id = "8086"
        device.vendor.name = "Intel Corporation"
        device.product.id = "0a0c"
        device.product.name = "Haswell-ULT HD Audio Controller"
        device.form_factor = "internal"
        device.string = "0"
        module-udev-detect.discovered = "1"
        device.icon_name = "audio-card-pci"
    Formats:
        pcm

Client #0
    Driver: module-systemd-login.c
    Owner Module: 15
    Properties:
        application.name = "Login Session 2"
        systemd-login.session = "2"

Client #1
    Driver: protocol-native.c
    Owner Module: 7
    Properties:
        application.name = "GNOME Shell Volume Control"
        native-protocol.peer = "UNIX socket client"
        native-protocol.version = "32"
        application.id = "org.gnome.VolumeControl"
        application.icon_name = "multimedia-volume-control"
        application.version = "3.28.4"
        application.process.id = "1594"
        application.process.user = "ines"
        application.process.host = "cybengal"
        application.process.binary = "gnome-shell"
        application.language = "en_US.UTF-8"
        window.x11.display = ":0"
        application.process.machine_id = "86cac673c2614684b0cf95cae2a0c981"
        application.process.session_id = "2"

Client #7
    Driver: module-x11-xsmp.c
    Owner Module: 23
    Properties:
        application.name = "XSMP Session on gnome-session as 109bd8a60abedf39cf156078370376921800000014700060"
        xsmp.vendor = "gnome-session"
        xsmp.client.id = "109bd8a60abedf39cf156078370376921800000014700060"

Client #8
    Driver: protocol-native.c
    Owner Module: 7
    Properties:
        application.name = "GNOME Volume Control Media Keys"
        native-protocol.peer = "UNIX socket client"
        native-protocol.version = "32"
        application.id = "org.gnome.VolumeControl"
        application.icon_name = "multimedia-volume-control"
        application.version = ""
        application.process.id = "1776"
        application.process.user = "ines"
        application.process.host = "cybengal"
        application.process.binary = "gsd-media-keys"
        application.language = "en_US.UTF-8"
        window.x11.display = ":0"
        application.process.machine_id = "86cac673c2614684b0cf95cae2a0c981"
        application.process.session_id = "2"

Client #22
    Driver: protocol-native.c
    Owner Module: 7
    Properties:
        application.name = "pactl"
        native-protocol.peer = "UNIX socket client"
        native-protocol.version = "32"
        application.process.id = "4036"
        application.process.user = "ines"
        application.process.host = "cybengal"
        application.process.binary = "pactl"
        application.language = "en_US.UTF-8"
        window.x11.display = ":0"
        application.process.machine_id = "86cac673c2614684b0cf95cae2a0c981"
        application.process.session_id = "2"

Sample #0
    Name: bell.ogg
    Sample Specification: float32le 1ch 44100Hz
    Channel Map: mono
    Volume: (invalid)
            balance 0.00
    Duration: 0.2s
    Size: 34.5 KiB
    Lazy: no
    Filename: n/a
    Properties:
        media.role = "event"
        media.name = "bell.ogg"
        application.name = "pactl"
        native-protocol.peer = "UNIX socket client"
        native-protocol.version = "32"
        application.process.id = "1766"
        application.process.user = "ines"
        application.process.host = "cybengal"
        application.process.binary = "pactl"
        application.language = "en_US.UTF-8"
        window.x11.display = ":0"
        application.process.machine_id = "86cac673c2614684b0cf95cae2a0c981"
        application.process.session_id = "2"

Card #0
    Name: alsa_card.pci-0000_00_03.0
    Driver: module-alsa-card.c
    Owner Module: 24
    Properties:
        alsa.card = "0"
        alsa.card_name = "HDA Intel HDMI"
        alsa.long_card_name = "HDA Intel HDMI at 0xf7d10000 irq 58"
        alsa.driver_name = "snd_hda_intel"
        device.bus_path = "pci-0000:00:03.0"
        sysfs.path = "/devices/pci0000:00/0000:00:03.0/sound/card0"
        device.bus = "pci"
        device.vendor.id = "8086"
        device.vendor.name = "Intel Corporation"
        device.product.id = "0a0c"
        device.product.name = "Haswell-ULT HD Audio Controller"
        device.form_factor = "internal"
        device.string = "0"
        device.description = "Built-in Audio"
        module-udev-detect.discovered = "1"
        device.icon_name = "audio-card-pci"
    Profiles:
        output:hdmi-stereo: Digital Stereo (HDMI) Output (sinks: 1, sources: 0, priority: 5400, available: yes)
        off: Off (sinks: 0, sources: 0, priority: 0, available: yes)
    Active Profile: output:hdmi-stereo
    Ports:
        hdmi-output-0: HDMI / DisplayPort (priority: 5900, latency offset: 0 usec)
            Properties:
                device.icon_name = "video-display"
            Part of profile(s): output:hdmi-stereo

---

