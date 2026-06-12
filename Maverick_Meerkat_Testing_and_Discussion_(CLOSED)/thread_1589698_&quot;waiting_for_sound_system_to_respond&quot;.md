---
title: "&quot;waiting for sound system to respond&quot;"
date: 2010-10-06
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by libihero on 2010-10-06
my sound does work, but the indicator applet shows it as muted, and when i click on sound preferences, it says "waiting for sound system to respond"

---

### Post by garvinrick4 on 2010-10-06
gksudo gedit /etc/pulse/default.pa
find the line:
load-module module-device-restore and comment it out. Put a # in front of line.
Has worked in past for fixing the sound in mute at boot.
Give it a try if makes no difference uncomment it.
Weird you say muted but works? Fancy audio system installed?

---

### Post by libihero on 2010-10-06
your thing didnt work :(

no fancy audio installed.  i dunno if it was because of a recent update of pulse audio that just happened....

---

### Post by garvinrick4 on 2010-10-06
You did save it after commenting out?
Do have a lot of Pulseaudio updates in maverick lately. No problems
here with intel.

---

### Post by 23dornot23d on 2010-10-06
It may be a new problem as the old problem never showed a message 
"waiting for sound system to respond"

Just was muted at the start of a session ....... you have to reboot to see if the above worked after saving the file with the line commented out ........

That was a old problem with muting though .... and has been fixed as far as I know.

---

### Post by libihero on 2010-10-06
i did reboot with it commented out and it didnt work
i have no clue what happened :(
i checked my download history and there is nothing installed or uninstalled related to sound (no pulseaudio or alsa or anything) besides that update today over the past three days

---

### Post by lidex on 2010-10-07
> **libihero said:**
> i did reboot with it commented out and it didnt work
i have no clue what happened :(
i checked my download history and there is nothing installed or uninstalled related to sound (no pulseaudio or alsa or anything) besides that update today over the past three days

So your sound works in everything? As a test:
```
pkill pulseaudio; sleep 2; pulseaudio -vv
```
Post the output please.

---

### Post by libihero on 2010-10-07
when i put that into the terminal it started working again, here is the output:

```
D: alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Invalid argument
D: alsa-util.c: Trying hw:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open hw:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Invalid argument
D: alsa-util.c: Trying plug:hw:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:hw:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Invalid argument
D: alsa-util.c: Trying plug:hw:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:hw:0
D: alsa-util.c: snd_pcm_hw_params_set_channels(1) failed: Invalid argument
I: alsa-util.c: Failed to set hardware parameters on plug:hw:0: Invalid argument
D: alsa-mixer.c: Looking at profile input:analog-stereo
D: alsa-mixer.c: Checking for recording on Analog Stereo (analog-stereo)
D: alsa-util.c: Trying front:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open front:0
D: alsa-util.c: Maximum hw buffer size is 23777 ms
D: alsa-util.c: Set buffer size first (to 3528 samples), period size second (to 441 samples).
D: alsa-mixer.c: Profile input:analog-stereo supported.
D: alsa-mixer.c: Looking at profile input:iec958-stereo
D: alsa-mixer.c: Checking for recording on Digital Stereo (IEC958) (iec958-stereo)
D: alsa-util.c: Trying iec958:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC0D1c' failed (-2)
I: alsa-util.c: Error opening PCM device iec958:0: No such file or directory
D: alsa-mixer.c: Looking at profile input:iec958-surround-40
D: alsa-mixer.c: Checking for recording on Digital Surround 4.0 (IEC958) (iec958-surround-40)
D: alsa-util.c: Trying iec958:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_hw.c: open '/dev/snd/pcmC0D1c' failed (-2)
I: alsa-util.c: Error opening PCM device iec958:0: No such file or directory
I: card.c: Created 1 "alsa_card.pci-0000_00_14.2"
D: reserve-wrap.c: Successfully create reservation lock monitor for device 'Audio0'
D: alsa-util.c: Trying front:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open front:0
D: alsa-util.c: Maximum hw buffer size is 23777 ms
D: alsa-util.c: Set buffer size first (to 88200 samples), period size second (to 88200 samples).
I: alsa-sink.c: Successfully opened device front:0.
I: alsa-sink.c: Selected mapping 'Analog Stereo' (analog-stereo).
I: alsa-sink.c: Successfully enabled mmap() mode.
I: alsa-sink.c: Successfully enabled timer-based scheduling mode.
I: (alsa-lib)control.c: Invalid CTL front:0
I: alsa-mixer.c: Unable to attach to mixer front:0: No such file or directory
I: alsa-mixer.c: Successfully attached to mixer 'hw:0'
D: alsa-mixer.c: Probing path 'analog-output'
D: alsa-mixer.c: Probing path 'analog-output-speaker'
D: alsa-mixer.c: Probing path 'analog-output-speaker'
D: alsa-mixer.c: Probe of element 'Desktop Speaker' failed.
D: alsa-mixer.c: Probing path 'analog-output-headphones'
D: alsa-mixer.c: Probing path 'analog-output-headphones'
D: alsa-mixer.c: Probe of element 'Headphone2' failed.
D: alsa-mixer.c: Probing path 'analog-output-mono'
D: alsa-mixer.c: Probe of element 'Master Mono' failed.
D: alsa-mixer.c: Probing path 'analog-output-lfe-on-mono'
D: alsa-mixer.c: Probe of element 'Master Mono' failed.
D: alsa-sink.c: Probed mixer paths:
D: alsa-mixer.c: Path Set 0x8cda178, direction=1, probed=yes
D: alsa-mixer.c: Path analog-output (Analog Output), direction=1, priority=99, probed=yes, supported=yes, has_mute=yes, has_volume=yes, has_dB=yes, min_volume=0, max_volume=64, min_dB=-99, max_dB=0
D: alsa-mixer.c: Element Master, direction=1, switch=1, volume=1, enumeration=0, required=0, required_absent=0, mask=0x7ffffffffffff, n_channels=1, override_map=yes
D: alsa-mixer.c: Element Headphone, direction=1, switch=1, volume=3, enumeration=0, required=0, required_absent=0, mask=0x6, n_channels=2, override_map=no
D: alsa-mixer.c: Element Speaker, direction=1, switch=1, volume=2, enumeration=0, required=0, required_absent=0, mask=0x6, n_channels=2, override_map=no
D: alsa-mixer.c: Element PCM, direction=1, switch=0, volume=1, enumeration=0, required=0, required_absent=0, mask=0x3600000000f66, n_channels=2, override_map=yes
D: alsa-mixer.c: Path analog-output-speaker (Analog Speakers), direction=1, priority=100, probed=yes, supported=yes, has_mute=yes, has_volume=yes, has_dB=yes, min_volume=0, max_volume=64, min_dB=-147, max_dB=0
D: alsa-mixer.c: Element Master, direction=1, switch=1, volume=1, enumeration=0, required=0, required_absent=0, mask=0x7ffffffffffff, n_channels=1, override_map=yes
D: alsa-mixer.c: Element Headphone, direction=1, switch=1, volume=3, enumeration=0, required=0, required_absent=0, mask=0x6, n_channels=2, override_map=no
D: alsa-mixer.c: Element Speaker, direction=1, switch=1, volume=1, enumeration=0, required=4, required_absent=0, mask=0x3600000000f66, n_channels=2, override_map=yes
D: alsa-mixer.c: Element PCM, direction=1, switch=0, volume=1, enumeration=0, required=0, required_absent=0, mask=0x3600000000f66, n_channels=2, override_map=yes
D: alsa-mixer.c: Path analog-output-headphones (Analog Headphones), direction=1, priority=90, probed=yes, supported=yes, has_mute=yes, has_volume=yes, has_dB=yes, min_volume=0, max_volume=64, min_dB=-147, max_dB=0
D: alsa-mixer.c: Element Master, direction=1, switch=1, volume=1, enumeration=0, required=0, required_absent=0, mask=0x7ffffffffffff, n_channels=1, override_map=yes
D: alsa-mixer.c: Element Headphone, direction=1, switch=1, volume=1, enumeration=0, required=4, required_absent=0, mask=0x3600000000f66, n_channels=2, override_map=yes
D: alsa-mixer.c: Element Speaker, direction=1, switch=2, volume=2, enumeration=0, required=0, required_absent=0, mask=0x6, n_channels=2, override_map=no
D: alsa-mixer.c: Element PCM, direction=1, switch=0, volume=1, enumeration=0, required=0, required_absent=0, mask=0x3600000000f66, n_channels=2, override_map=yes
D: alsa-mixer.c: Added 3 ports
D: core-subscribe.c: Dropped redundant event due to change event.
I: module-device-restore.c: Restoring port for sink sink:alsa_output.pci-0000_00_14.2.analog-stereo.
I: module-device-restore.c: Restoring volume for sink alsa_output.pci-0000_00_14.2.analog-stereo.
I: module-device-restore.c: Restoring mute state for sink alsa_output.pci-0000_00_14.2.analog-stereo.
I: sink.c: Created sink 1 "alsa_output.pci-0000_00_14.2.analog-stereo" with sample spec s16le 2ch 44100Hz and channel map front-left,front-right
I: sink.c:     alsa.resolution_bits = "16"
I: sink.c:     device.api = "alsa"
I: sink.c:     device.class = "sound"
I: sink.c:     alsa.class = "generic"
I: sink.c:     alsa.subclass = "generic-mix"
I: sink.c:     alsa.name = "STAC92xx Analog"
I: sink.c:     alsa.id = "STAC92xx Analog"
I: sink.c:     alsa.subdevice = "0"
I: sink.c:     alsa.subdevice_name = "subdevice #0"
I: sink.c:     alsa.device = "0"
I: sink.c:     alsa.card = "0"
I: sink.c:     alsa.card_name = "HDA ATI SB"
I: sink.c:     alsa.long_card_name = "HDA ATI SB at 0xf8500000 irq 16"
I: sink.c:     alsa.driver_name = "snd_hda_intel"
I: sink.c:     device.bus_path = "pci-0000:00:14.2"
I: sink.c:     sysfs.path = "/devices/pci0000:00/0000:00:14.2/sound/card0"
I: sink.c:     device.bus = "pci"
I: sink.c:     device.vendor.id = "1002"
I: sink.c:     device.vendor.name = "ATI Technologies Inc"
I: sink.c:     device.product.id = "4383"
I: sink.c:     device.product.name = "SBx00 Azalia (Intel HDA)"
I: sink.c:     device.form_factor = "internal"
I: sink.c:     device.string = "front:0"
I: sink.c:     device.buffering.buffer_size = "352768"
I: sink.c:     device.buffering.fragment_size = "176384"
I: sink.c:     device.access_mode = "mmap+timer"
I: sink.c:     device.profile.name = "analog-stereo"
I: sink.c:     device.profile.description = "Analog Stereo"
I: sink.c:     device.description = "Internal Audio Analog Stereo"
I: sink.c:     alsa.mixer_name = "SigmaTel STAC9205"
I: sink.c:     alsa.components = "HDA:838476a0,107b0381,00100204 HDA:11c11040,11c10001,00100200"
I: sink.c:     module-udev-detect.discovered = "1"
I: sink.c:     device.icon_name = "audio-card-pci"
D: core-subscribe.c: Dropped redundant event due to change event.
I: module-device-restore.c: Restoring mute state for source alsa_output.pci-0000_00_14.2.analog-stereo.monitor.
I: source.c: Created source 1 "alsa_output.pci-0000_00_14.2.analog-stereo.monitor" with sample spec s16le 2ch 44100Hz and channel map front-left,front-right
I: source.c:     device.description = "Monitor of Internal Audio Analog Stereo"
I: source.c:     device.class = "monitor"
I: source.c:     alsa.card = "0"
I: source.c:     alsa.card_name = "HDA ATI SB"
I: source.c:     alsa.long_card_name = "HDA ATI SB at 0xf8500000 irq 16"
I: source.c:     alsa.driver_name = "snd_hda_intel"
I: source.c:     device.bus_path = "pci-0000:00:14.2"
I: source.c:     sysfs.path = "/devices/pci0000:00/0000:00:14.2/sound/card0"
I: source.c:     device.bus = "pci"
I: source.c:     device.vendor.id = "1002"
I: source.c:     device.vendor.name = "ATI Technologies Inc"
I: source.c:     device.product.id = "4383"
I: source.c:     device.product.name = "SBx00 Azalia (Intel HDA)"
I: source.c:     device.form_factor = "internal"
I: source.c:     device.string = "0"
I: source.c:     module-udev-detect.discovered = "1"
I: source.c:     device.icon_name = "audio-card-pci"
I: alsa-sink.c: Using 2.0 fragments of size 176384 bytes (999.91ms), buffer size is 352768 bytes (1999.82ms)
I: alsa-sink.c: Time scheduling watermark is 20.00ms
D: alsa-sink.c: hwbuf_unused=0
D: alsa-sink.c: setting avail_min=87310
D: alsa-mixer.c: Activating path analog-output-speaker
D: alsa-mixer.c: Path analog-output-speaker (Analog Speakers), direction=1, priority=100, probed=yes, supported=yes, has_mute=yes, has_volume=yes, has_dB=yes, min_volume=0, max_volume=64, min_dB=-147, max_dB=0
D: alsa-mixer.c: Element Master, direction=1, switch=1, volume=1, enumeration=0, required=0, required_absent=0, mask=0x7ffffffffffff, n_channels=1, override_map=yes
D: alsa-mixer.c: Element Headphone, direction=1, switch=1, volume=3, enumeration=0, required=0, required_absent=0, mask=0x6, n_channels=2, override_map=no
D: alsa-mixer.c: Element Speaker, direction=1, switch=1, volume=1, enumeration=0, required=4, required_absent=0, mask=0x3600000000f66, n_channels=2, override_map=yes
D: alsa-mixer.c: Element PCM, direction=1, switch=0, volume=1, enumeration=0, required=0, required_absent=0, mask=0x3600000000f66, n_channels=2, override_map=yes
I: alsa-sink.c: Hardware volume ranges from -147.00 dB to 0.00 dB.
I: alsa-sink.c: No particular base volume set, fixing to 0 dB
I: alsa-sink.c: Using hardware volume control. Hardware dB scale supported.
I: alsa-sink.c: Using hardware mute control.
D: alsa-util.c: snd_pcm_dump():
D: alsa-util.c: Soft volume PCM
D: alsa-util.c: Control: PCM Playback Volume
D: alsa-util.c: min_dB: -51
D: alsa-util.c: max_dB: 0
D: alsa-util.c: resolution: 256
D: alsa-util.c: Its setup is:
D: alsa-util.c:   stream       : PLAYBACK
D: alsa-util.c:   access       : MMAP_INTERLEAVED
D: alsa-util.c:   format       : S16_LE
D: alsa-util.c:   subformat    : STD
D: alsa-util.c:   channels     : 2
D: alsa-util.c:   rate         : 44100
D: alsa-util.c:   exact rate   : 44100 (44100/1)
D: alsa-util.c:   msbits       : 16
D: alsa-util.c:   buffer_size  : 88192
D: alsa-util.c:   period_size  : 44096
D: alsa-util.c:   period_time  : 999909
D: alsa-util.c:   tstamp_mode  : ENABLE
D: alsa-util.c:   period_step  : 1
D: alsa-util.c:   avail_min    : 87310
D: alsa-util.c:   period_event : 0
D: alsa-util.c:   start_threshold  : -1
D: alsa-util.c:   stop_threshold   : 1444937728
D: alsa-util.c:   silence_threshold: 0
D: alsa-util.c:   silence_size : 0
D: alsa-util.c:   boundary     : 1444937728
D: alsa-util.c: Slave: Hardware PCM card 0 'HDA ATI SB' device 0 subdevice 0
D: alsa-util.c: Its setup is:
D: alsa-util.c:   stream       : PLAYBACK
D: alsa-util.c:   access       : MMAP_INTERLEAVED
D: alsa-util.c:   format       : S16_LE
D: alsa-util.c:   subformat    : STD
D: alsa-util.c:   channels     : 2
D: alsa-util.c:   rate         : 44100
D: alsa-util.c:   exact rate   : 44100 (44100/1)
D: alsa-util.c:   msbits       : 16
D: alsa-util.c:   buffer_size  : 88192
D: alsa-util.c:   period_size  : 44096
D: alsa-util.c:   period_time  : 999909
D: alsa-util.c:   tstamp_mode  : ENABLE
D: alsa-util.c:   period_step  : 1
D: alsa-util.c:   avail_min    : 87310
D: alsa-util.c:   period_event : 0
D: alsa-util.c:   start_threshold  : -1
D: alsa-util.c:   stop_threshold   : 1444937728
D: alsa-util.c:   silence_threshold: 0
D: alsa-util.c:   silence_size : 0
D: alsa-util.c:   boundary     : 1444937728
D: alsa-util.c:   appl_ptr     : 0
D: alsa-util.c:   hw_ptr       : 0
D: alsa-sink.c: Requested volume: 0:  80% 1:  80%
D: alsa-sink.c: Got hardware volume: 0:  81% 1:  81%
D: alsa-sink.c: Calculated software volume: 0:  99% 1:  99% (accurate-enough=yes)
D: alsa-sink.c: Thread starting up
D: core-util.c: RealtimeKit worked.
I: core-util.c: Successfully enabled SCHED_RR scheduling for thread, with priority 5.
I: alsa-sink.c: Starting playback.
D: alsa-sink.c: Cutting sleep time for the initial iterations by half.
D: alsa-sink.c: Cutting sleep time for the initial iterations by half.
D: alsa-sink.c: Cutting sleep time for the initial iterations by half.
D: alsa-util.c: Trying front:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open front:0
D: alsa-util.c: Maximum hw buffer size is 23777 ms
D: alsa-util.c: Set buffer size first (to 88200 samples), period size second (to 88200 samples).
I: alsa-source.c: Successfully opened device front:0.
I: alsa-source.c: Selected mapping 'Analog Stereo' (analog-stereo).
I: alsa-source.c: Successfully enabled mmap() mode.
I: alsa-source.c: Successfully enabled timer-based scheduling mode.
I: (alsa-lib)control.c: Invalid CTL front:0
I: alsa-mixer.c: Unable to attach to mixer front:0: No such file or directory
I: alsa-mixer.c: Successfully attached to mixer 'hw:0'
D: alsa-mixer.c: Probing path 'analog-input'
D: alsa-mixer.c: Probing path 'analog-input-microphone'
D: alsa-mixer.c: Probe of element 'Mic' failed.
D: alsa-mixer.c: Probing path 'analog-input-linein'
D: alsa-mixer.c: Probe of element 'Line' failed.
D: alsa-mixer.c: Probing path 'analog-input'
D: alsa-mixer.c: Probe of element 'Aux' failed.
D: alsa-mixer.c: Probing path 'analog-input-video'
D: alsa-mixer.c: Probe of element 'Video' failed.
D: alsa-mixer.c: Probing path 'analog-input-video'
D: alsa-mixer.c: Probe of element 'TV Tuner' failed.
D: alsa-mixer.c: Probing path 'analog-input-radio'
D: alsa-mixer.c: Probe of element 'FM' failed.
D: alsa-mixer.c: Probing path 'analog-input'
D: alsa-mixer.c: Probe of element 'Mic/Line' failed.
D: alsa-source.c: Probed mixer paths:
D: alsa-mixer.c: Path Set 0x8cd52a8, direction=2, probed=yes
D: alsa-mixer.c: Path analog-input (Analog Input), direction=2, priority=100, probed=yes, supported=yes, has_mute=yes, has_volume=yes, has_dB=yes, min_volume=0, max_volume=15, min_dB=0, max_dB=22.5
D: alsa-mixer.c: Element Capture, direction=2, switch=1, volume=1, enumeration=0, required=2, required_absent=0, mask=0x4037e00000000f66, n_channels=2, override_map=yes
D: alsa-mixer.c: Element Mic Jack Mode, direction=2, switch=0, volume=0, enumeration=1, required=0, required_absent=0, mask=0x0, n_channels=0, override_map=no
D: alsa-mixer.c: Option Mic In (input-microphone/Microphone) index=0, priority=0
D: alsa-mixer.c: Option Line In (input-linein/Line-In) index=1, priority=0
D: alsa-mixer.c: Setting input-microphone (Microphone) priority=0
D: alsa-mixer.c: Setting input-linein (Line-In) priority=0
D: alsa-mixer.c: Added 2 ports
D: core-subscribe.c: Dropped redundant event due to change event.
I: module-device-restore.c: Restoring port for source source:alsa_input.pci-0000_00_14.2.analog-stereo.
I: module-device-restore.c: Restoring volume for source alsa_input.pci-0000_00_14.2.analog-stereo.
I: module-device-restore.c: Restoring mute state for source alsa_input.pci-0000_00_14.2.analog-stereo.
I: source.c: Created source 2 "alsa_input.pci-0000_00_14.2.analog-stereo" with sample spec s16le 2ch 44100Hz and channel map front-left,front-right
I: source.c:     alsa.resolution_bits = "16"
I: source.c:     device.api = "alsa"
I: source.c:     device.class = "sound"
I: source.c:     alsa.class = "generic"
I: source.c:     alsa.subclass = "generic-mix"
I: source.c:     alsa.name = "STAC92xx Analog"
I: source.c:     alsa.id = "STAC92xx Analog"
I: source.c:     alsa.subdevice = "0"
I: source.c:     alsa.subdevice_name = "subdevice #0"
I: source.c:     alsa.device = "0"
I: source.c:     alsa.card = "0"
I: source.c:     alsa.card_name = "HDA ATI SB"
I: source.c:     alsa.long_card_name = "HDA ATI SB at 0xf8500000 irq 16"
I: source.c:     alsa.driver_name = "snd_hda_intel"
I: source.c:     device.bus_path = "pci-0000:00:14.2"
I: source.c:     sysfs.path = "/devices/pci0000:00/0000:00:14.2/sound/card0"
I: source.c:     device.bus = "pci"
I: source.c:     device.vendor.id = "1002"
I: source.c:     device.vendor.name = "ATI Technologies Inc"
I: source.c:     device.product.id = "4383"
I: source.c:     device.product.name = "SBx00 Azalia (Intel HDA)"
I: source.c:     device.form_factor = "internal"
I: source.c:     device.string = "front:0"
I: source.c:     device.buffering.buffer_size = "352768"
I: source.c:     device.buffering.fragment_size = "176384"
I: source.c:     device.access_mode = "mmap+timer"
I: source.c:     device.profile.name = "analog-stereo"
I: source.c:     device.profile.description = "Analog Stereo"
I: source.c:     device.description = "Internal Audio Analog Stereo"
I: source.c:     alsa.mixer_name = "SigmaTel STAC9205"
I: source.c:     alsa.components = "HDA:838476a0,107b0381,00100204 HDA:11c11040,11c10001,00100200"
I: source.c:     module-udev-detect.discovered = "1"
I: source.c:     device.icon_name = "audio-card-pci"
I: alsa-source.c: Using 2.0 fragments of size 176384 bytes (999.91ms), buffer size is 352768 bytes (1999.82ms)
I: alsa-source.c: Time scheduling watermark is 20.00ms
D: alsa-source.c: hwbuf_unused=0
D: alsa-source.c: setting avail_min=87310
D: alsa-mixer.c: Activating path analog-input
D: alsa-mixer.c: Path analog-input (Analog Input), direction=2, priority=100, probed=yes, supported=yes, has_mute=yes, has_volume=yes, has_dB=yes, min_volume=0, max_volume=15, min_dB=0, max_dB=22.5
D: alsa-mixer.c: Element Capture, direction=2, switch=1, volume=1, enumeration=0, required=2, required_absent=0, mask=0x4037e00000000f66, n_channels=2, override_map=yes
D: alsa-mixer.c: Element Mic Jack Mode, direction=2, switch=0, volume=0, enumeration=1, required=0, required_absent=0, mask=0x0, n_channels=0, override_map=no
D: alsa-mixer.c: Option Mic In (input-microphone/Microphone) index=0, priority=0
D: alsa-mixer.c: Option Line In (input-linein/Line-In) index=1, priority=0
D: alsa-mixer.c: Setting input-microphone (Microphone) priority=0
D: alsa-mixer.c: Setting input-linein (Line-In) priority=0
I: alsa-source.c: Hardware volume ranges from 0.00 dB to 22.50 dB.
I: alsa-source.c: Fixing base volume to -22.50 dB
I: alsa-source.c: Using hardware volume control. Hardware dB scale supported.
I: alsa-source.c: Using hardware mute control.
D: alsa-util.c: snd_pcm_dump():
D: alsa-util.c: Soft volume PCM
D: alsa-util.c: Control: PCM Playback Volume
D: alsa-util.c: min_dB: -51
D: alsa-util.c: max_dB: 0
D: alsa-util.c: resolution: 256
D: alsa-util.c: Its setup is:
D: alsa-util.c:   stream       : CAPTURE
D: alsa-util.c:   access       : MMAP_INTERLEAVED
D: alsa-util.c:   format       : S16_LE
D: alsa-util.c:   subformat    : STD
D: alsa-util.c:   channels     : 2
D: alsa-util.c:   rate         : 44100
D: alsa-util.c:   exact rate   : 44100 (44100/1)
D: alsa-util.c:   msbits       : 16
D: alsa-util.c:   buffer_size  : 88192
D: alsa-util.c:   period_size  : 44096
D: alsa-util.c:   period_time  : 999909
D: alsa-util.c:   tstamp_mode  : ENABLE
D: alsa-util.c:   period_step  : 1
D: alsa-util.c:   avail_min    : 87310
D: alsa-util.c:   period_event : 0
D: alsa-util.c:   start_threshold  : -1
D: alsa-util.c:   stop_threshold   : 1444937728
D: alsa-util.c:   silence_threshold: 0
D: alsa-util.c:   silence_size : 0
D: alsa-util.c:   boundary     : 1444937728
D: alsa-util.c: Slave: Hardware PCM card 0 'HDA ATI SB' device 0 subdevice 0
D: alsa-util.c: Its setup is:
D: alsa-util.c:   stream       : CAPTURE
D: alsa-util.c:   access       : MMAP_INTERLEAVED
D: alsa-util.c:   format       : S16_LE
D: alsa-util.c:   subformat    : STD
D: alsa-util.c:   channels     : 2
D: alsa-util.c:   rate         : 44100
D: alsa-util.c:   exact rate   : 44100 (44100/1)
D: alsa-util.c:   msbits       : 16
D: alsa-util.c:   buffer_size  : 88192
D: alsa-util.c:   period_size  : 44096
D: alsa-util.c:   period_time  : 999909
D: alsa-util.c:   tstamp_mode  : ENABLE
D: alsa-util.c:   period_step  : 1
D: alsa-util.c:   avail_min    : 87310
D: alsa-util.c:   period_event : 0
D: alsa-util.c:   start_threshold  : -1
D: alsa-util.c:   stop_threshold   : 1444937728
D: alsa-util.c:   silence_threshold: 0
D: alsa-util.c:   silence_size : 0
D: alsa-util.c:   boundary     : 1444937728
D: alsa-util.c:   appl_ptr     : 0
D: alsa-util.c:   hw_ptr       : 0
D: alsa-source.c: Requested volume: 0: 100% 1: 100%
D: alsa-source.c: Got hardware volume: 0: 100% 1: 100%
D: alsa-source.c: Calculated software volume: 0: 100% 1: 100% (accurate-enough=yes)
D: alsa-source.c: Thread starting up
D: core-util.c: RealtimeKit worked.
I: core-util.c: Successfully enabled SCHED_RR scheduling for thread, with priority 5.
I: alsa-source.c: Starting capture.
I: module.c: Loaded "module-alsa-card" (index: #5; argument: "device_id="0" name="pci-0000_00_14.2" card_name="alsa_card.pci-0000_00_14.2" tsched=yes ignore_dB=no card_properties="module-udev-detect.discovered=1"").
I: module-udev-detect.c: Card /devices/pci0000:00/0000:00:14.2/sound/card0 (alsa_card.pci-0000_00_14.2) module loaded.
I: module-udev-detect.c: Found 2 cards.
I: module.c: Loaded "module-udev-detect" (index: #6; argument: "").
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9.21/modules/module-bluetooth-discover.so': success
D: dbus-util.c: Successfully connected to D-Bus system bus 86261fe92f772f417370257e00000015 as :1.42
D: bluetooth-util.c: dbus: interface=org.freedesktop.DBus, path=/org/freedesktop/DBus, member=NameAcquired
D: bluetooth-util.c: Bluetooth daemon is apparently not available.
I: module.c: Loaded "module-bluetooth-discover" (index: #7; argument: "").
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9.21/modules/module-esound-protocol-unix.so': success
I: module.c: Loaded "module-esound-protocol-unix" (index: #8; argument: "").
I: module.c: Loaded "module-native-protocol-unix" (index: #9; argument: "").
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9.21/modules/module-gconf.so': success
I: module.c: Loaded "module-gconf" (index: #10; argument: "").
D: core-subscribe.c: Dropped redundant event due to change event.
I: module-default-device-restore.c: Restored default sink 'alsa_output.pci-0000_00_14.2.analog-stereo'.
D: core-subscribe.c: Dropped redundant event due to change event.
I: module-default-device-restore.c: Restored default source 'alsa_input.pci-0000_00_14.2.analog-stereo'.
I: module.c: Loaded "module-default-device-restore" (index: #11; argument: "").
I: module.c: Loaded "module-rescue-streams" (index: #12; argument: "").
I: module.c: Loaded "module-always-sink" (index: #13; argument: "").
I: module.c: Loaded "module-intended-roles" (index: #14; argument: "").
D: module-suspend-on-idle.c: Sink alsa_output.pci-0000_01_05.2.hdmi-stereo becomes idle, timeout in 5 seconds.
D: module-suspend-on-idle.c: Sink alsa_output.pci-0000_00_14.2.analog-stereo becomes idle, timeout in 5 seconds.
D: module-suspend-on-idle.c: Source alsa_input.pci-0000_00_14.2.analog-stereo becomes idle, timeout in 5 seconds.
I: module.c: Loaded "module-suspend-on-idle" (index: #15; argument: "").
I: client.c: Created 0 "ConsoleKit Session /org/freedesktop/ConsoleKit/Session1"
D: module-console-kit.c: Added new session /org/freedesktop/ConsoleKit/Session1
I: module.c: Loaded "module-console-kit" (index: #16; argument: "").
I: module.c: Loaded "module-position-event-sounds" (index: #17; argument: "").
D: main.c: Got org.pulseaudio.Server!
I: main.c: Daemon startup complete.
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC0 is accessible: yes
I: client.c: Created 1 "Native client (UNIX socket client)"
I: client.c: Created 2 "Native client (UNIX socket client)"
D: protocol-native.c: Protocol version: remote 16, local 16
I: protocol-native.c: Got credentials: uid=1000 gid=1000 success=1
D: protocol-native.c: SHM possible: yes
D: protocol-native.c: Negotiated SHM: yes
D: protocol-native.c: Protocol version: remote 16, local 16
I: protocol-native.c: Got credentials: uid=1000 gid=1000 success=1
D: protocol-native.c: SHM possible: yes
D: protocol-native.c: Negotiated SHM: yes
D: module-augment-properties.c: Looking for .desktop file for indicator-sound-service
D: alsa-sink.c: Cutting sleep time for the initial iterations by half.
D: alsa-sink.c: Cutting sleep time for the initial iterations by half.
D: alsa-sink.c: Cutting sleep time for the initial iterations by half.
D: alsa-sink.c: Cutting sleep time for the initial iterations by half.
D: module-augment-properties.c: Looking for .desktop file for gnome-settings-daemon
D: alsa-sink.c: Wakeup from ALSA!
I: alsa-sink.c: Underrun!
I: alsa-sink.c: Increasing wakeup watermark to 30.00 ms
W: ratelimit.c: 16 events suppressed
D: alsa-source.c: Wakeup from ALSA!
I: module-suspend-on-idle.c: Source alsa_input.pci-0000_00_14.2.analog-stereo idle for too long, suspending ...
D: source.c: Suspend cause of source alsa_input.pci-0000_00_14.2.analog-stereo is 0x0004, suspending
I: alsa-source.c: Device suspended...
I: module-suspend-on-idle.c: Sink alsa_output.pci-0000_00_14.2.analog-stereo idle for too long, suspending ...
D: sink.c: Suspend cause of sink alsa_output.pci-0000_00_14.2.analog-stereo is 0x0004, suspending
I: alsa-sink.c: Device suspended...
I: module-suspend-on-idle.c: Sink alsa_output.pci-0000_01_05.2.hdmi-stereo idle for too long, suspending ...
D: sink.c: Suspend cause of sink alsa_output.pci-0000_01_05.2.hdmi-stereo is 0x0004, suspending
I: alsa-sink.c: Device suspended...
D: reserve-wrap.c: Device lock status of reserve-monitor-wrapper@Audio0 changed: not busy
D: reserve-wrap.c: Device lock status of reserve-monitor-wrapper@Audio1 changed: not busy
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: yes
D: module-udev-detect.c: /dev/snd/controlC0 is accessible: yes


```

---

### Post by lidex on 2010-10-07
In 'System>Preferences>StartUp Programs' do you have an entry for 'PulseAudio Sound System'?

---

### Post by libihero on 2010-10-07
ya i do, it is checked to start but when i restart the computer it messes up again

---

