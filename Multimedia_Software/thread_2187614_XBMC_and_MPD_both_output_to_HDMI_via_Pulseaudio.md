---
title: "XBMC and MPD both output to HDMI via Pulseaudio"
date: 2013-11-13
forum: Multimedia Software
---

### Post by cfbowin on 2013-11-13
I want to run XBMC and MPD at the same time outputing both sound sources to HDMI. I've failed so far and am in need of help!

Using Ubuntu 13.10 Desktop. Installed XBMC and MPD from standard repertoire.

**EDIT: Solution to the problem found in post #2**

So I try to use pulseaudio to send sound both from XBMC and MPD to the HDMI outpout.

/etc/mpd.conf:
```
music_directory            "~/music"
playlist_directory        "~/playlists"
db_file                "~/mpd.db"
log_file            "~/mpd.log"
pid_file            "~/mpd.pid"
state_file            "~/mpd.state"
sticker_file            "~/mpd.sticker.sql"

user                "user"
group                "user
bind_to_address            "any"
port                "6600"
log_level            "default"
gapless_mp3_playback        "yes"
restore_paused            "no"
auto_update            "yes"
follow_outside_symlinks        "yes"
follow_inside_symlinks        "yes"
metadata_to_use            "artist,album,title,track,name,genre,date,composer,performer,disc"

#audio_output {
#    type            "alsa"
#    name            "mpd ALSA"
#    device            "plughw:0,3"
#    format            "44100:16:2"
#    mixer_type        "hardware"
#    mixer_device        "default"
#}

audio_output {
    type            "pulse"
    name            "MPD PulseAudio Stream"
#    server            "localhost"
    sink            "alsa_output.pci-0000_00_08.0.hdmi-stereo"
}
```

I've also added a line to /etc/pulse/default.pa:
```
set-default-sink alsa_output.pci-0000_00_08.0.hdmi-stereo
```

If I login with normal Ubuntu it autodetects HDMI output, starts an extra pulseaudio and output for ps aux | grep pulse is:
```
user   1264  0.7  0.3 105828  5008 ?        Sl   04:38   0:00 /usr/bin/pulseaudio --start --log-target=syslog
user   1296  0.0  0.1  14492  2520 ?        S    04:38   0:00 /usr/lib/pulseaudio/pulse/gconf-helper
user   1910  1.6  0.3 101412  5628 ?        S<l  04:38   0:00 /usr/bin/pulseaudio --start --log-target=syslog
user   2041  0.1  0.1  14464  2520 ?        S    04:38   0:00 /usr/lib/pulseaudio/pulse/gconf-helper
```
Sound from MPD works fine here.

If I then logout and login into XBMC session the "Audio output device" is set to "PulseAudio Sound Server" and sound in XBMC works, but sound from MPD doesn't. If I change "Audio output device" to anything else but "PulseAudio Sound Server" sound from MPD starts working but sound from XBMC doesn't.

Okay so now I try reboot and autologin into XBMC session. Same error message from MPD as before, but this time XBMC can't output to pulseaudio, there is no "PulseAudio Sound Server" option for "Audio output device". I can now chose between my 3 outputs, 1 HDMI, 1 analog and 1 S/PDIF.

ps aux | grep pulse gives me:
```
user   1252  0.1  0.3 105828  5172 ?        Sl   04:47   0:00 /usr/bin/pulseaudio --start --log-target=syslog
user   1297  0.0  0.1  14492  2520 ?        S    04:47   0:00 /usr/lib/pulseaudio/pulse/gconf-helper
```

The thing is, if I know log out of XBMC session and into Ubuntu session again a new pulseaudio server starts, MPD now works. If I log out now and open a XBMC session sound will only work in XBMC, but if I go and change "Audio output device" to "PulseAudio Sound Server" I get sound from both MPD and XBMC. I can't manually start pulseaudio from ssh when in XBMC session, it doesn't show up as and audio output device. This breaks if I reboot.

There seems to be some kind of problem for XBMC to start a pulseaudio server. Is there some way to get XBMC to start a pulseaudio server when I log in with XBMC session?

Okay, so maybe if I run a pulseaudio --system, for system wide pulseaudio? Because it seems like there is a pulseaudio server from user that is always running. Maybe it's the one that uses HDMI out but can't be used by XBMC or pulseaudio so it binds to a new pulseaudio server which then when logging in with Ubuntu session takes over HDMI.

I edit /etc/pulse/system.pa and add the line:
```
set-default-sink alsa_output.pci-0000_00_08.0.hdmi-stereo
```
I also remove the same line from /etc/pulse/default.pa

I change in /etc/init.d/pulseaudio:
```
PULSEAUDIO_SYSTEM_START=1
```
user is also a member of the pulseaudio groups that it needs to use the system wide pulseaudio service.

ps aux | grep pulse now gives me:
```
pulse      947  0.5  0.2  97336  4616 ?        S<l  05:23   0:00 /usr/bin/pulseaudio --system --disallow-exit --disallow-module-loading=1 --daemonize --log-target=syslog --high-priority
```

All looks good, I chose "PulseAudio Sound Server" in XBMC but no sound. MPD doesn't work either. Okay, so maybe it didn't load the hdmi-output. I don't know how to check if that sink is loaded though, since its a service. Under a user I run "pacmd list-sinks" to see what sink is loaded.

So I run */etc/init.d/pulseaudio stop* and then *sudo pulseaudio --system* and I get the error:
```
Sink alsa_output.pci-0000_00_08.0.hdmi-stereo does not exist.
```

I run */etc/init.d/pulseaudio start* and then logout of XBMC session and login to Ubuntu session, goes to sound settings and chooses HDMI (analog output was selected).
ps aux | grep pulse gives me:
```
pulse     1951 14.7  0.3 100592  4924 ?        S<l  05:32   0:19 /usr/bin/pulseaudio --system --disallow-exit --disallow-module-loading=1 --daemonize --log-target=syslog --high-priority
```

Sound now works with MPD. I logout of Ubuntu session and sound still works, since it's running on system service so pulseaudio is still working. I login to XBMC session and MPD still plays and XBMC sound also works, this is what I want. I try to reboot to autologin into XBMC but this time audio doesn't work through pulseaudio.

I believe the problem is that the pulseaudio server doesn't set the right output, it sets to analog output instead of HDMI and when I log into Ubuntu session and change HDMI manually in the settings it gets the right output, which is *alsa_output.pci-0000_00_08.0.hdmi-stereo*.

I've also confirmed the problem by plugin in speakers to my analog output on the computer, sound works here when i do a fresh boot. This all tells me that pulseaudio fails to load the hdmi-output and falls back on the default analog output.

How can I make my hdmi-output my default output for pulseaudio? They way I have it know (which is what all guides I've found says) is the only way I know how to load the hdmi sink with pulseaudio.

Thanks! :)

I found some more stuff that might help

pactl stat:
```
Currently in use: 199 blocks containing 426,9 KiB bytes total.
Allocated during whole lifetime: 717528 blocks containing 938,4 MiB bytes total.
Sample cache size: 0 B
Server String: /var/run/pulse/native
Library Protocol Version: 28
Server Protocol Version: 28
Is Local: yes
Client Index: 25
Tile Size: 65496
User Name: pulse
Host Name: xbmc
Server Name: pulseaudio
Server Version: 4.0
Default Sample Specification: s16le 2ch 44100Hz
Default Channel Map: front-left,front-right
Default Sink: alsa_output.pci-0000_00_08.0.analog-stereo
Default Source: alsa_input.pci-0000_00_08.0.analog-stereo
Cookie: 9edd:1cb7
```
Here is says "analog-stereo" which apperently is the problem.

pactl list:
```
Module #0
    Name: module-alsa-card
    Argument: device_id="0" name="pci-0000_00_08.0" card_name="alsa_card.pci-0000_00_08.0" namereg_fail=false tsched=yes fixed_latency_range=no ignore_dB=no deferred_volume=yes use_ucm=yes card_properties="module-udev-detect.discovered=1"
    Usage counter: 2
    Properties:
        module.author = "Lennart Poettering"
        module.description = "ALSA Card"
        module.version = "4.0"

Module #1
    Name: module-udev-detect
    Argument: 
    Usage counter: n/a
    Properties:
        module.author = "Lennart Poettering"
        module.description = "Detect available audio hardware and load matching drivers"
        module.version = "4.0"

Module #2
    Name: module-native-protocol-unix
    Argument: 
    Usage counter: n/a
    Properties:
        module.author = "Lennart Poettering"
        module.description = "Native protocol (UNIX sockets)"
        module.version = "4.0"

Module #3
    Name: module-stream-restore
    Argument: 
    Usage counter: n/a
    Properties:
        module.author = "Lennart Poettering"
        module.description = "Automatically restore the volume/mute/device state of streams"
        module.version = "4.0"

Module #4
    Name: module-device-restore
    Argument: 
    Usage counter: n/a
    Properties:
        module.author = "Lennart Poettering"
        module.description = "Automatically restore the volume/mute state of devices"
        module.version = "4.0"

Module #5
    Name: module-default-device-restore
    Argument: 
    Usage counter: n/a
    Properties:
        module.author = "Lennart Poettering"
        module.description = "Automatically restore the default sink and source"
        module.version = "4.0"

Module #6
    Name: module-rescue-streams
    Argument: 
    Usage counter: n/a
    Properties:
        module.author = "Lennart Poettering"
        module.description = "When a sink/source is removed, try to move their streams to the default sink/source"
        module.version = "4.0"

Module #7
    Name: module-always-sink
    Argument: 
    Usage counter: n/a
    Properties:
        module.author = "Colin Guthrie"
        module.description = "Always keeps at least one sink loaded even if it's a null one"
        module.version = "4.0"

Module #8
    Name: module-suspend-on-idle
    Argument: 
    Usage counter: n/a
    Properties:
        module.author = "Lennart Poettering"
        module.description = "When a sink/source is idle for too long, suspend it"
        module.version = "4.0"

Module #9
    Name: module-position-event-sounds
    Argument: 
    Usage counter: n/a
    Properties:
        module.author = "Lennart Poettering"
        module.description = "Position event sounds between L and R depending on the position on screen of the widget triggering them."
        module.version = "4.0"

Sink #0
    State: RUNNING
    Name: alsa_output.pci-0000_00_08.0.analog-stereo
    Description: Built-in Audio Analog Stereo
    Driver: module-alsa-card.c
    Sample Specification: s16le 2ch 44100Hz
    Channel Map: front-left,front-right
    Owner Module: 0
    Mute: no
    Volume: 0: 100% 1: 100%
            0: 0,00 dB 1: 0,00 dB
            balance 0,00
    Base Volume: 100%
                 0,00 dB
    Monitor Source: alsa_output.pci-0000_00_08.0.analog-stereo.monitor
    Latency: 11400 usec, configured 11609 usec
    Flags: HARDWARE HW_MUTE_CTRL HW_VOLUME_CTRL DECIBEL_VOLUME LATENCY 
    Properties:
        alsa.resolution_bits = "16"
        device.api = "alsa"
        device.class = "sound"
        alsa.class = "generic"
        alsa.subclass = "generic-mix"
        alsa.name = "ALC662 rev1 Analog"
        alsa.id = "ALC662 rev1 Analog"
        alsa.subdevice = "0"
        alsa.subdevice_name = "subdevice #0"
        alsa.device = "0"
        alsa.card = "0"
        alsa.card_name = "HDA NVidia"
        alsa.long_card_name = "HDA NVidia at 0xf9f78000 irq 23"
        alsa.driver_name = "snd_hda_intel"
        device.bus_path = "pci-0000:00:08.0"
        sysfs.path = "/devices/pci0000:00/0000:00:08.0/sound/card0"
        device.bus = "pci"
        device.vendor.id = "10de"
        device.vendor.name = "NVIDIA Corporation"
        device.product.id = "0ac0"
        device.product.name = "MCP79 High Definition Audio"
        device.form_factor = "internal"
        device.string = "front:0"
        device.buffering.buffer_size = "65536"
        device.buffering.fragment_size = "32768"
        device.access_mode = "mmap+timer"
        device.profile.name = "analog-stereo"
        device.profile.description = "Analog Stereo"
        device.description = "Built-in Audio Analog Stereo"
        alsa.mixer_name = "Nvidia MCP79/7A HDMI"
        alsa.components = "HDA:10ec0662,10438376,00100101 HDA:10de0007,10de0101,00100100"
        module-udev-detect.discovered = "1"
        device.icon_name = "audio-card-pci"
    Ports:
        analog-output: Analog Output (priority: 9900)
        analog-output-headphones: Headphones (priority: 9000, not available)
    Active Port: analog-output
    Formats:
        pcm

Source #0
    State: IDLE
    Name: alsa_output.pci-0000_00_08.0.analog-stereo.monitor
    Description: Monitor of Built-in Audio Analog Stereo
    Driver: module-alsa-card.c
    Sample Specification: s16le 2ch 44100Hz
    Channel Map: front-left,front-right
    Owner Module: 0
    Mute: no
    Volume: 0: 100% 1: 100%
            0: 0,00 dB 1: 0,00 dB
            balance 0,00
    Base Volume: 100%
                 0,00 dB
    Monitor of Sink: alsa_output.pci-0000_00_08.0.analog-stereo
    Latency: 0 usec, configured 371519 usec
    Flags: DECIBEL_VOLUME LATENCY 
    Properties:
        device.description = "Monitor of Built-in Audio Analog Stereo"
        device.class = "monitor"
        alsa.card = "0"
        alsa.card_name = "HDA NVidia"
        alsa.long_card_name = "HDA NVidia at 0xf9f78000 irq 23"
        alsa.driver_name = "snd_hda_intel"
        device.bus_path = "pci-0000:00:08.0"
        sysfs.path = "/devices/pci0000:00/0000:00:08.0/sound/card0"
        device.bus = "pci"
        device.vendor.id = "10de"
        device.vendor.name = "NVIDIA Corporation"
        device.product.id = "0ac0"
        device.product.name = "MCP79 High Definition Audio"
        device.form_factor = "internal"
        device.string = "0"
        module-udev-detect.discovered = "1"
        device.icon_name = "audio-card-pci"
    Formats:
        pcm

Source #1
    State: SUSPENDED
    Name: alsa_input.pci-0000_00_08.0.analog-stereo
    Description: Built-in Audio Analog Stereo
    Driver: module-alsa-card.c
    Sample Specification: s16le 2ch 44100Hz
    Channel Map: front-left,front-right
    Owner Module: 0
    Mute: no
    Volume: 0:  45% 1:  45%
            0: -21,00 dB 1: -21,00 dB
            balance 0,00
    Base Volume:  28%
                 -33,00 dB
    Monitor of Sink: n/a
    Latency: 0 usec, configured 0 usec
    Flags: HARDWARE HW_MUTE_CTRL HW_VOLUME_CTRL DECIBEL_VOLUME LATENCY 
    Properties:
        alsa.resolution_bits = "16"
        device.api = "alsa"
        device.class = "sound"
        alsa.class = "generic"
        alsa.subclass = "generic-mix"
        alsa.name = "ALC662 rev1 Analog"
        alsa.id = "ALC662 rev1 Analog"
        alsa.subdevice = "0"
        alsa.subdevice_name = "subdevice #0"
        alsa.device = "0"
        alsa.card = "0"
        alsa.card_name = "HDA NVidia"
        alsa.long_card_name = "HDA NVidia at 0xf9f78000 irq 23"
        alsa.driver_name = "snd_hda_intel"
        device.bus_path = "pci-0000:00:08.0"
        sysfs.path = "/devices/pci0000:00/0000:00:08.0/sound/card0"
        device.bus = "pci"
        device.vendor.id = "10de"
        device.vendor.name = "NVIDIA Corporation"
        device.product.id = "0ac0"
        device.product.name = "MCP79 High Definition Audio"
        device.form_factor = "internal"
        device.string = "front:0"
        device.buffering.buffer_size = "65536"
        device.buffering.fragment_size = "32768"
        device.access_mode = "mmap+timer"
        device.profile.name = "analog-stereo"
        device.profile.description = "Analog Stereo"
        device.description = "Built-in Audio Analog Stereo"
        alsa.mixer_name = "Nvidia MCP79/7A HDMI"
        alsa.components = "HDA:10ec0662,10438376,00100101 HDA:10de0007,10de0101,00100100"
        module-udev-detect.discovered = "1"
        device.icon_name = "audio-card-pci"
    Ports:
        analog-input: Analog Input (priority: 10000)
        analog-input-microphone: Microphone (priority: 8700, not available)
    Active Port: analog-input
    Formats:
        pcm

Sink Input #1
    Driver: protocol-native.c
    Owner Module: 2
    Client: 6
    Sink: 0
    Sample Specification: float32le 2ch 44100Hz
    Channel Map: front-left,front-right
    Format: pcm, format.sample_format = "\"float32le\""  format.rate = "44100"  format.channels = "2"  format.channel_map = "\"front-left,front-right\""
    Corked: no
    Mute: no
    Volume: 0: 100% 1: 100%
            0: 0,00 dB 1: 0,00 dB
            balance 0,00
    Buffer Latency: 174784 usec
    Sink Latency: 10215 usec
    Resample method: copy
    Properties:
        media.name = "ALSA Playback"
        application.name = "ALSA plug-in [xbmc.bin]"
        native-protocol.peer = "UNIX socket client"
        native-protocol.version = "28"
        application.process.id = "1587"
        application.process.user = "cfbowin"
        application.process.host = "xbmc"
        application.process.binary = "xbmc.bin"
        application.language = "C"
        window.x11.display = ":0"
        application.process.machine_id = "2da4ab0f0eb1dde36b68d3d55282811a"
        application.process.session_id = "c1"
        module-stream-restore.id = "sink-input-by-application-name:ALSA plug-in [xbmc.bin]"

Sink Input #8
    Driver: protocol-native.c
    Owner Module: 2
    Client: 8
    Sink: 0
    Sample Specification: s16le 2ch 44100Hz
    Channel Map: front-left,front-right
    Format: pcm, format.sample_format = "\"s16le\""  format.rate = "44100"  format.channels = "2"  format.channel_map = "\"front-left,front-right\""
    Corked: no
    Mute: no
    Volume: 0:  76% 1:  76%
            0: -7,15 dB 1: -7,15 dB
            balance 0,00
    Buffer Latency: 245102 usec
    Sink Latency: 10016 usec
    Resample method: n/a
    Properties:
        media.name = "MPD PulseAudio Stream"
        application.name = "Music Player Daemon"
        native-protocol.peer = "UNIX socket client"
        native-protocol.version = "28"
        media.role = "music"
        application.process.id = "1987"
        application.process.user = "cfbowin"
        application.process.host = "xbmc"
        application.process.binary = "mpd"
        application.language = "C"
        window.x11.display = ":0"
        application.process.machine_id = "2da4ab0f0eb1dde36b68d3d55282811a"
        module-stream-restore.id = "sink-input-by-media-role:music"

Client #6
    Driver: protocol-native.c
    Owner Module: 2
    Properties:
        application.name = "ALSA plug-in [xbmc.bin]"
        native-protocol.peer = "UNIX socket client"
        native-protocol.version = "28"
        application.process.id = "1587"
        application.process.user = "cfbowin"
        application.process.host = "xbmc"
        application.process.binary = "xbmc.bin"
        application.language = "C"
        window.x11.display = ":0"
        application.process.machine_id = "2da4ab0f0eb1dde36b68d3d55282811a"
        application.process.session_id = "c1"

Client #8
    Driver: protocol-native.c
    Owner Module: 2
    Properties:
        application.name = "Music Player Daemon"
        native-protocol.peer = "UNIX socket client"
        native-protocol.version = "28"
        media.role = "music"
        application.process.id = "1987"
        application.process.user = "cfbowin"
        application.process.host = "xbmc"
        application.process.binary = "mpd"
        application.language = "C"
        window.x11.display = ":0"
        application.process.machine_id = "2da4ab0f0eb1dde36b68d3d55282811a"

Client #27
    Driver: protocol-native.c
    Owner Module: 2
    Properties:
        application.name = "pactl"
        native-protocol.peer = "UNIX socket client"
        native-protocol.version = "28"
        application.process.id = "2302"
        application.process.user = "cfbowin"
        application.process.host = "xbmc"
        application.process.binary = "pactl"
        application.language = "en_US.UTF-8"
        window.x11.display = ":0"
        application.process.machine_id = "2da4ab0f0eb1dde36b68d3d55282811a"
        application.process.session_id = "2"

Card #0
    Name: alsa_card.pci-0000_00_08.0
    Driver: module-alsa-card.c
    Owner Module: 0
    Properties:
        alsa.card = "0"
        alsa.card_name = "HDA NVidia"
        alsa.long_card_name = "HDA NVidia at 0xf9f78000 irq 23"
        alsa.driver_name = "snd_hda_intel"
        device.bus_path = "pci-0000:00:08.0"
        sysfs.path = "/devices/pci0000:00/0000:00:08.0/sound/card0"
        device.bus = "pci"
        device.vendor.id = "10de"
        device.vendor.name = "NVIDIA Corporation"
        device.product.id = "0ac0"
        device.product.name = "MCP79 High Definition Audio"
        device.form_factor = "internal"
        device.string = "0"
        device.description = "Built-in Audio"
        module-udev-detect.discovered = "1"
        device.icon_name = "audio-card-pci"
    Profiles:
        input:analog-stereo: Analog Stereo Input (sinks: 0, sources: 1, priority. 60)
        output:analog-stereo: Analog Stereo Output (sinks: 1, sources: 0, priority. 6000)
        output:analog-stereo+input:analog-stereo: Analog Stereo Duplex (sinks: 1, sources: 1, priority. 6060)
        output:iec958-stereo: Digital Stereo (IEC958) Output (sinks: 1, sources: 0, priority. 5500)
        output:iec958-stereo+input:analog-stereo: Digital Stereo (IEC958) Output + Analog Stereo Input (sinks: 1, sources: 1, priority. 5560)
        output:hdmi-stereo: Digital Stereo (HDMI) Output (sinks: 1, sources: 0, priority. 5400)
        output:hdmi-stereo+input:analog-stereo: Digital Stereo (HDMI) Output + Analog Stereo Input (sinks: 1, sources: 1, priority. 5460)
        output:hdmi-surround: Digital Surround 5.1 (HDMI) Output (sinks: 1, sources: 0, priority. 300)
        output:hdmi-surround+input:analog-stereo: Digital Surround 5.1 (HDMI) Output + Analog Stereo Input (sinks: 1, sources: 1, priority. 360)
        off: Off (sinks: 0, sources: 0, priority. 0)
    Active Profile: output:analog-stereo+input:analog-stereo
    Ports:
        analog-input: Analog Input (priority: 10000, latency offset: 0 usec)
            Part of profile(s): input:analog-stereo, output:analog-stereo+input:analog-stereo, output:iec958-stereo+input:analog-stereo, output:hdmi-stereo+input:analog-stereo, output:hdmi-surround+input:analog-stereo
        analog-input-microphone: Microphone (priority: 8700, latency offset: 0 usec, not available)
            Properties:
                device.icon_name = "audio-input-microphone"
            Part of profile(s): input:analog-stereo, output:analog-stereo+input:analog-stereo, output:iec958-stereo+input:analog-stereo, output:hdmi-stereo+input:analog-stereo, output:hdmi-surround+input:analog-stereo
        analog-output: Analog Output (priority: 9900, latency offset: 0 usec)
            Part of profile(s): output:analog-stereo, output:analog-stereo+input:analog-stereo
        analog-output-headphones: Headphones (priority: 9000, latency offset: 0 usec, not available)
            Properties:
                device.icon_name = "audio-headphones"
            Part of profile(s): output:analog-stereo, output:analog-stereo+input:analog-stereo
        iec958-stereo-output: Digital Output (S/PDIF) (priority: 0, latency offset: 0 usec)
            Part of profile(s): output:iec958-stereo, output:iec958-stereo+input:analog-stereo
        hdmi-output-0: HDMI / DisplayPort (priority: 5900, latency offset: 0 usec)
            Properties:
                device.icon_name = "video-display"
            Part of profile(s): output:hdmi-stereo, output:hdmi-stereo+input:analog-stereo, output:hdmi-surround, output:hdmi-surround+input:analog-stereo
```

I believe one of my problems is that the HDMI sink isn't even present, so therefor I can't load it. How do I get around this?

EDIT:

I also tried a new sink load form pulseaudio of the alsa.

Added to /etc/pulse/system.pa:
```
load-module module-alsa-sink device=plughw:0,3
set-default-sink alsa_output.plughw_0_3
```
and that works for MPD! (Also edited MPD to listen for alsa_output.plughw_0_3) but no sound in XBMC :( Even though it's set to send sound ti pulseaudio.

---

### Post by cfbowin on 2013-11-13
Okay so after some more research I've come up with a solution! Though I should share it with everyone if you ever encouter the same problem.

So basically what I did was that I told pulseaudio to use the tcp module and not require authentication.

So to make this work:

Add the following to /etc/pulse/system.pa:
```
load-module module-native-protocol-tcp auth-anonymous=1
load-module module-alsa-sink device=plughw:0,3
set-default-sink alsa_output.plughw_0_3
```
This is to make it possible to connect to the pulseaudio server without authentication so I don't have to specify the output sink to use (see my previous post's mpd.conf where I specify the sink to use). I think the problem is that I couldn't specify the sink in XBMC so when I tried to use the pulseaudio server it failed since it didn't know what sink to output the sound to.

To choose your device, type the command *aplay -l* to the a list of available hardware.
```
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC662 rev1 Analog [ALC662 rev1 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC662 rev1 Digital [ALC662 rev1 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
```
In my case I want to use HDMI, so card 0 and device 3, which is 0,3. I also know its a plughw and not hw so my device is plughw:0,3. You can also try hw=0,3 if plughw doesn't work for you. You can try the output with *aplay -D plughw:0,3 /usr/share/sound/alsa/Front_Center.wav*.

Since I manually load my drivers for pulseaudio I commented out the following in /etc/pulse/system.pa:
```
### Automatically load driver modules depending on the hardware available
#.ifexists module-udev-detect.so
#load-module module-udev-detect
#.else
### Use the static hardware detection module (for systems that lack udev/hal su$
#load-module module-detect
#.endif
```
but I don't think this is nececarry.

Okay now we have set up the config file for starting pulseaudio at boot and make it a system wide service.

Go to /etc/init.d/pulseaudio and change PULSEAUDIO_SYSTEM_START to 1:
```
PULSEAUDIO_SYSTEM_START=1
```
Now pulseaudio will start as a system wide service so that both XBMC and MPD (and any other source) can use it.

Now to make MPD and XBMC use the pulseaudio server. In the /etc/mpd.conf change audio_output:
```
audio_output {
        type                    "pulse"
        name                    "MPD PulseAudio Stream"
        server                  "127.0.0.1"
}
```

and to get XBMC to use pulseaudio go to System->Settings->System->Audio output and change "Audio output device" to "PulseAudio Sound Server".

Sound should now work for both XBMC and MPD!

---

