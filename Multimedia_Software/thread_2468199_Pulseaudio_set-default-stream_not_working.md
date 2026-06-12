---
title: "Pulseaudio set-default-stream not working"
date: 2021-10-21
forum: Multimedia Software
---

### Post by pbn5012 on 2021-10-21
As is common on this forum, the specific question that I am asking here  is not really the problem I want to solve, and the real solution to my  problem may involve a totally different tactic. Furthermore I think I do  understand why my approach isn't working, so this question might be a  waste of time, but I want to explain my approach so someone can suggest  how I can adapt it or modify it to achieve the same end.

Regardless of whether the specific problem I'm asking is insurmountable  as construed in the most narrow sense I will start with the specific  question rather than the general question.

```
 Ubuntu Release:    21.10
Codename:    impish

Pulseaudio version 15.0

pactl 15.0
Compiled with libpulse 15.0.0
Linked with libpulse 15.0.0

pacmd 15.0
Compiled with libpulse 15.0.0
Linked with libpulse 15.0.0
```

I am trying to change the default sink in Pulseaudio but nothing happens.

Initial status:

```
$ pacmd list-sinks

pacmd list-sinks
4 sink(s) available.
    index: 0
    name: <alsa_output.pci-0000_00_1f.3-platform-skl_hda_dsp_generic.HiFi__hw_sofhdadsp_5__sink>
    driver: <module-alsa-card.c>
    flags: HARDWARE DECIBEL_VOLUME LATENCY DYNAMIC_LATENCY
    state: IDLE
    suspend cause: (none)
    priority: 9037
    volume: front-left: 65536 / 100% / 0.00 dB,   front-right: 65536 / 100% / 0.00 dB
            balance 0.00
    base volume: 65536 / 100% / 0.00 dB
    volume steps: 65537
    muted: no
    current latency: 32.28 ms
    max request: 7 KiB
    max rewind: 7 KiB
    monitor source: 0
    sample spec: s16le 2ch 48000Hz
    channel map: front-left,front-right
                 Stereo
    used by: 0
    linked by: 1
    configured latency: 40.00 ms; range is 0.50 .. 341.33 ms
    card: 0 <alsa_card.pci-0000_00_1f.3-platform-skl_hda_dsp_generic>
    module: 6
    properties:
        alsa.resolution_bits = "16"
        device.api = "alsa"
        device.class = "sound"
        alsa.class = "generic"
        alsa.subclass = "generic-mix"
        alsa.name = ""
        alsa.id = "HDMI3 (*)"
        alsa.subdevice = "0"
        alsa.subdevice_name = "subdevice #0"
        alsa.device = "5"
        alsa.card = "0"
        alsa.card_name = "sof-hda-dsp"
        alsa.long_card_name = "LENOVO-81TD-LenovoYogaC740_15IML-LNVNB161216"
        alsa.driver_name = "snd_soc_skl_hda_dsp"
        device.bus_path = "pci-0000:00:1f.3-platform-skl_hda_dsp_generic"
        sysfs.path = "/devices/pci0000:00/0000:00:1f.3/skl_hda_dsp_generic/sound/card0"
        device.bus = "pci"
        device.vendor.id = "8086"
        device.vendor.name = "Intel Corporation"
        device.product.id = "02c8"
        device.product.name = "Comet Lake PCH-LP cAVS"
        device.string = "hw:sofhdadsp,5"
        device.buffering.buffer_size = "65536"
        device.buffering.fragment_size = "16384"
        device.access_mode = "mmap+timer"
        device.profile.name = "HiFi: hw:sofhdadsp,5: sink"
        device.profile.description = "HDMI3 Output"
        alsa.mixer_device = "hw:sofhdadsp"
        device.description = "Comet Lake PCH-LP cAVS HDMI3 Output"
        module-udev-detect.discovered = "1"
        device.icon_name = "audio-card-pci"
    ports:
        [Out] HDMI3: HDMI3 Output (priority 700, latency offset 0 usec, available: no)
            properties:
                
    active port: <[Out] HDMI3>
    index: 1
    name: <alsa_output.pci-0000_00_1f.3-platform-skl_hda_dsp_generic.HiFi__hw_sofhdadsp_4__sink>
    driver: <module-alsa-card.c>
    flags: HARDWARE DECIBEL_VOLUME LATENCY DYNAMIC_LATENCY
    state: IDLE
    suspend cause: (none)
    priority: 9036
    volume: front-left: 65536 / 100% / 0.00 dB,   front-right: 65536 / 100% / 0.00 dB
            balance 0.00
    base volume: 65536 / 100% / 0.00 dB
    volume steps: 65537
    muted: no
    current latency: 37.70 ms
    max request: 7 KiB
    max rewind: 7 KiB
    monitor source: 1
    sample spec: s16le 2ch 48000Hz
    channel map: front-left,front-right
                 Stereo
    used by: 0
    linked by: 1
    configured latency: 40.00 ms; range is 0.50 .. 341.33 ms
    card: 0 <alsa_card.pci-0000_00_1f.3-platform-skl_hda_dsp_generic>
    module: 6
    properties:
        alsa.resolution_bits = "16"
        device.api = "alsa"
        device.class = "sound"
        alsa.class = "generic"
        alsa.subclass = "generic-mix"
        alsa.name = ""
        alsa.id = "HDMI2 (*)"
        alsa.subdevice = "0"
        alsa.subdevice_name = "subdevice #0"
        alsa.device = "4"
        alsa.card = "0"
        alsa.card_name = "sof-hda-dsp"
        alsa.long_card_name = "LENOVO-81TD-LenovoYogaC740_15IML-LNVNB161216"
        alsa.driver_name = "snd_soc_skl_hda_dsp"
        device.bus_path = "pci-0000:00:1f.3-platform-skl_hda_dsp_generic"
        sysfs.path = "/devices/pci0000:00/0000:00:1f.3/skl_hda_dsp_generic/sound/card0"
        device.bus = "pci"
        device.vendor.id = "8086"
        device.vendor.name = "Intel Corporation"
        device.product.id = "02c8"
        device.product.name = "Comet Lake PCH-LP cAVS"
        device.string = "hw:sofhdadsp,4"
        device.buffering.buffer_size = "65536"
        device.buffering.fragment_size = "16384"
        device.access_mode = "mmap+timer"
        device.profile.name = "HiFi: hw:sofhdadsp,4: sink"
        device.profile.description = "HDMI2 Output"
        alsa.mixer_device = "hw:sofhdadsp"
        device.description = "Comet Lake PCH-LP cAVS HDMI2 Output"
        module-udev-detect.discovered = "1"
        device.icon_name = "audio-card-pci"
    ports:
        [Out] HDMI2: HDMI2 Output (priority 600, latency offset 0 usec, available: no)
            properties:
                
    active port: <[Out] HDMI2>
    index: 2
    name: <alsa_output.pci-0000_00_1f.3-platform-skl_hda_dsp_generic.HiFi__hw_sofhdadsp_3__sink>
    driver: <module-alsa-card.c>
    flags: HARDWARE DECIBEL_VOLUME LATENCY DYNAMIC_LATENCY
    state: IDLE
    suspend cause: (none)
    priority: 9035
    volume: front-left: 10288 /  16% / -48.25 dB,   front-right: 10288 /  16% / -48.25 dB
            balance 0.00
    base volume: 65536 / 100% / 0.00 dB
    volume steps: 65537
    muted: no
    current latency: 32.37 ms
    max request: 7 KiB
    max rewind: 7 KiB
    monitor source: 2
    sample spec: s16le 2ch 48000Hz
    channel map: front-left,front-right
                 Stereo
    used by: 0
    linked by: 1
    configured latency: 40.00 ms; range is 0.50 .. 341.33 ms
    card: 0 <alsa_card.pci-0000_00_1f.3-platform-skl_hda_dsp_generic>
    module: 6
    properties:
        alsa.resolution_bits = "16"
        device.api = "alsa"
        device.class = "sound"
        alsa.class = "generic"
        alsa.subclass = "generic-mix"
        alsa.name = ""
        alsa.id = "HDMI1 (*)"
        alsa.subdevice = "0"
        alsa.subdevice_name = "subdevice #0"
        alsa.device = "3"
        alsa.card = "0"
        alsa.card_name = "sof-hda-dsp"
        alsa.long_card_name = "LENOVO-81TD-LenovoYogaC740_15IML-LNVNB161216"
        alsa.driver_name = "snd_soc_skl_hda_dsp"
        device.bus_path = "pci-0000:00:1f.3-platform-skl_hda_dsp_generic"
        sysfs.path = "/devices/pci0000:00/0000:00:1f.3/skl_hda_dsp_generic/sound/card0"
        device.bus = "pci"
        device.vendor.id = "8086"
        device.vendor.name = "Intel Corporation"
        device.product.id = "02c8"
        device.product.name = "Comet Lake PCH-LP cAVS"
        device.string = "hw:sofhdadsp,3"
        device.buffering.buffer_size = "65536"
        device.buffering.fragment_size = "16384"
        device.access_mode = "mmap+timer"
        device.profile.name = "HiFi: hw:sofhdadsp,3: sink"
        device.profile.description = "HDMI1 Output"
        alsa.mixer_device = "hw:sofhdadsp"
        device.description = "Comet Lake PCH-LP cAVS HDMI1 Output"
        module-udev-detect.discovered = "1"
        device.icon_name = "audio-card-pci"
    ports:
        [Out] HDMI1: HDMI1 Output (priority 500, latency offset 0 usec, available: no)
            properties:
                
    active port: <[Out] HDMI1>
  * index: 3
    name: <alsa_output.pci-0000_00_1f.3-platform-skl_hda_dsp_generic.HiFi__hw_sofhdadsp__sink>
    driver: <module-alsa-card.c>
    flags: HARDWARE HW_MUTE_CTRL HW_VOLUME_CTRL DECIBEL_VOLUME LATENCY DYNAMIC_LATENCY
    state: IDLE
    suspend cause: (none)
    priority: 9032
    volume: front-left: 6553 /  10% / -60.00 dB,   front-right: 6553 /  10% / -60.00 dB
            balance 0.00
    base volume: 65536 / 100% / 0.00 dB
    volume steps: 65537
    muted: no
    current latency: 30.67 ms
    max request: 7 KiB
    max rewind: 7 KiB
    monitor source: 3
    sample spec: s16le 2ch 48000Hz
    channel map: front-left,front-right
                 Stereo
    used by: 0
    linked by: 1
    configured latency: 40.00 ms; range is 0.50 .. 341.33 ms
    card: 0 <alsa_card.pci-0000_00_1f.3-platform-skl_hda_dsp_generic>
    module: 6
    properties:
        alsa.resolution_bits = "16"
        device.api = "alsa"
        device.class = "sound"
        alsa.class = "generic"
        alsa.subclass = "generic-mix"
        alsa.name = ""
        alsa.id = "HDA Analog (*)"
        alsa.subdevice = "0"
        alsa.subdevice_name = "subdevice #0"
        alsa.device = "0"
        alsa.card = "0"
        alsa.card_name = "sof-hda-dsp"
        alsa.long_card_name = "LENOVO-81TD-LenovoYogaC740_15IML-LNVNB161216"
        alsa.driver_name = "snd_soc_skl_hda_dsp"
        device.bus_path = "pci-0000:00:1f.3-platform-skl_hda_dsp_generic"
        sysfs.path = "/devices/pci0000:00/0000:00:1f.3/skl_hda_dsp_generic/sound/card0"
        device.bus = "pci"
        device.vendor.id = "8086"
        device.vendor.name = "Intel Corporation"
        device.product.id = "02c8"
        device.product.name = "Comet Lake PCH-LP cAVS"
        device.string = "hw:sofhdadsp"
        device.buffering.buffer_size = "65536"
        device.buffering.fragment_size = "16384"
        device.access_mode = "mmap+timer"
        device.profile.name = "HiFi: hw:sofhdadsp: sink"
        device.profile.description = "Speaker + Headphones"
        alsa.mixer_device = "hw:sofhdadsp"
        device.description = "Comet Lake PCH-LP cAVS Speaker + Headphones"
        module-udev-detect.discovered = "1"
        device.icon_name = "audio-card-pci"
    ports:
        [Out] Speaker: Speaker (priority 100, latency offset 0 usec, available: unknown)
            properties:
                
        [Out] Headphones: Headphones (priority 200, latency offset 0 usec, available: no)
            properties:
                
    active port: <[Out] Speaker>


```
As you can see there are four sinks. The default one has index 3, its  name is ```
alsa_output.pci-0000_00_1f.3-platform-skl_hda_dsp_generic.HiFi__hw_sofhdadsp__sink
```.
pactl also gives the same answer:

```
$ pactl get-default-sink
alsa_output.pci-0000_00_1f.3-platform-skl_hda_dsp_generic.HiFi__hw_sofhdadsp__sink

```
 I want to change the default sink to the one with index 2 whose name is ```

alsa_output.pci-0000_00_1f.3-platform-skl_hda_dsp_generic.HiFi__hw_sofhdadsp_3__sink
```
so I run
```
 $ pactl set-default-sink alsa_output.pci-0000_00_1f.3-platform-
skl_hda_dsp_generic.HiFi__hw_sofhdadsp_3__sink
```
or

```
$ pactl set-default-sink 2

```
but in both cases, nothing happens. The output in both cases is the same as before.

This answer: [https://askubuntu.com/questions/71863/how-to-change-pulseaudio-sink-with-pacmd-set-default-sink-during-playback](https://askubuntu.com/questions/71863/how-to-change-pulseaudio-sink-with-pacmd-set-default-sink-during-playback)
says > PulseAudio pacmd is not capable of switching the default sinks  while there is an actively playing stream to the sink input. However  there is a way to still achieve this.

As far as I know there is no actively playing streams to the sink input. For example, I have

```
$ pacmd list-sink-inputs
0 sink input(s) available.

```
I optimistically added the line
```
load-module module-stream-restore restore_device=false

```to my /etc/pulse/default.pa file and
and restarted pulseaudio, but this didn't solve the problem.

Now, I do think I understand why this is happening. The conversation here seems relevant:
[https://bugs.freedesktop.org/show_bug.cgi?id=102987](https://bugs.freedesktop.org/show_bug.cgi?id=102987)
As Nils Alex says,
 > This seems to be not a bug but desired behaviour. After  pa_core_set_configured_default_sink() has set up the new default sink,  the function pa_core_update_default_sink() is called. 
  If your new sink is not linked (that is, not SUSPENDED, IDLE or  RUNNING) or if it is linked but all outputs are unavailable, this  function will set a "better" sink as default sink.
  In my case, the new sink is an HDMI sink and I tried the command  while not being connected to any HDMI device.  pa_core_set_configured_default_sink() did what it should do, but  afterwards pa_core_update_default_sink() set the default sink to my old  one.

My case is similar to Nils's. I *do not* have a physical HDMI cable  actually plugged into my computer, which presumably explains why the  output reads
```
Ports:
        [Out] HDMI1: HDMI1 Output (type: HDMI, priority: 500, not available) 
[/CODE
]The reason I am doing this is that I want to mimic the setup suggested in the highest-voted answer to this question.

[https://superuser.com/questions/605445/how-to-stream-my-gnu-linux-audio-output-to-android-devices-over-wi-fi](https://superuser.com/questions/605445/how-to-stream-my-gnu-linux-audio-output-to-android-devices-over-wi-fi)

I was able to follow the instructions in the top answer easily, and  everything works. However, for the line in the suggested script
[CODE]
pactl load-module module-simple-protocol-tcp rate=48000 format=s16le  channels=2 source=<source_name_here> record=true port=8000

```
I want the source to be something other than the default speakers or  headphones, because I don't want the sound coming through the speakers  when I play music. So I want to set the HDMI1 as default precisely  *because* it's unavailable. I want a dummy sink which is connected to no  real output and only exists so the tcp protocol can stream it to wifi.

I can't figure out how to silence the speakers without muting the stream itself.

I *can* just move an existing audio stream from the default sink to the  HDMI sink, and that works fine. But it's really temperamental, because  anything that causes the stream to stop and restart (pausing the video,  etc.) causes the newly restarted stream to switch back to the default.  So I still would really prefer the default to be changed to HDMI1. Is  there any way to do this? If not, how would you recommend that I solve  the problem of pushing audio to wifi without it coming through the  speakers?

---

### Post by TheFu on 2021-10-21
```
$ pactl set-default-sink alsa_output.pci-0000_00_1f.3-platform-
skl_hda_dsp_generic.HiFi__hw_sofhdadsp_3__sink
```
won't work.  It needs to be all on one line:
```
 $ pactl set-default-sink alsa_output.pci-0000_00_1f.3-platform-skl_hda_dsp_generic.HiFi__hw_sofhdadsp_3__sink
```

Or you can use a line-wrap with 
```
 $ pactl set-default-sink [COLOR="#FF0000"]\[/COLOR]
   alsa_output.pci-0000_00_1f.3-platform-skl_hda_dsp_generic.HiFi__hw_sofhdadsp_3__sink
```
if you prefer.  The '\' cannot have any characters after it - no space or no tabs allowed.

Just tested this on 21.10. It worked.  I did need to go into **pavucontrol** and unmute the output.
```
$ pactl list short sinks
0       [COLOR="#FF0000"]alsa_output.pci-0000_00_04.0.analog-stereo[/COLOR]      module-alsa-card.c     s16le 2ch 44100Hz        RUNNING

$ pactl     set-default-sink    [COLOR="#FF0000"]alsa_output.pci-0000_00_04.0.analog-stereo[/COLOR]
$ pavucontrol &
```
Clearly, "[COLOR="#FF0000"]alsa_output.pci-0000_00_04.0.analog-stereo[/COLOR]" was in the list from the prior command. It wasn't "RUNNING" the first time, but I'm listening to some music through it now that I'm typing this up. ;)

---

### Post by Holger_Gehrke on 2021-10-21
Why don't you create a null-sink (a pseudo device that's connected to nothing) ?
```

pacmd load-module module-null-sink sink_name=simplenet

```
Then just set source to simplenet.monitor. This is the way it's described in the [pulseaudio documentation]("https://www.freedesktop.org/wiki/Software/PulseAudio/Documentation/User/Network/") in the section for rtp-streaming, should work the same with simple-protocol-tcp ...

Holger

---

