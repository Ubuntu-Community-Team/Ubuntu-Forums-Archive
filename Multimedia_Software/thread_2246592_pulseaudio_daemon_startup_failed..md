---
title: "pulseaudio daemon startup failed."
date: 2014-10-01
forum: Multimedia Software
---

### Post by vk8tmj on 2014-10-01
Hello,  

I have tried reading as much about other problems regarding pulseaudio within these forums but unfortunately have been unable to solve my problem.  

I have just upgraded from unbuntu 12.10(?) to 14.04 and found no speaker icon in the top toolbar.  A command line speaker-test produces audio, but when trying to start pulseaudio I get the following errors (see below).  Can someone please give me a clue how to fix this? 

~$ pulseaudio --start
E: [pulseaudio] main.c: Daemon startup failed.

or for more info 

~$ pulseaudio
E: [alsa-sink-ES1371/1] alsa-sink.c: ALSA woke us up to write new data to the device, but there was actually nothing to write!
E: [alsa-sink-ES1371/1] alsa-sink.c: Most likely this is a bug in the ALSA driver 'snd_ens1371'. Please report this issue to the ALSA developers.
E: [alsa-sink-ES1371/1] alsa-sink.c: We were woken up with POLLOUT set -- however a subsequent snd_pcm_avail() returned 0 or another value < min_avail.
E: [pulseaudio] ltdl-bind-now.c: Failed to open module module-console-kit.so: module-console-kit.so: cannot open shared object file: No such file or directory
E: [pulseaudio] module.c: Failed to open module "module-console-kit".
E: [pulseaudio] main.c: Module load failed.
E: [pulseaudio] main.c: Failed to initialise daemon.


and 

~$ pulseaudio -v
I: [pulseaudio] main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
I: [pulseaudio] main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
I: [pulseaudio] core-util.c: Successfully gained nice level -11.
I: [pulseaudio] main.c: This is PulseAudio 4.0
I: [pulseaudio] main.c: Page size is 4096 bytes
I: [pulseaudio] main.c: Machine ID is 628cda678f4bc951ffe1d9874948672d.
I: [pulseaudio] main.c: Session ID is c2.
I: [pulseaudio] main.c: Using runtime directory /run/user/1000/pulse.
I: [pulseaudio] main.c: Using state directory /home/roy/.pulse.
I: [pulseaudio] main.c: Using modules directory /usr/lib/pulse-4.0/modules.
I: [pulseaudio] main.c: Running in system mode: no
I: [pulseaudio] main.c: Fresh high-resolution timers available! Bon appetit!
I: [pulseaudio] cpu-x86.c: CPU flags: CMOV MMX SSE SSE2 SSE3 SSSE3 SSE4_1 
I: [pulseaudio] svolume_mmx.c: Initialising MMX optimized volume functions.
I: [pulseaudio] remap_mmx.c: Initialising MMX optimized remappers.
I: [pulseaudio] svolume_sse.c: Initialising SSE2 optimized volume functions.
I: [pulseaudio] remap_sse.c: Initialising SSE2 optimized remappers.
I: [pulseaudio] sconv_sse.c: Initialising SSE2 optimized conversions.
I: [pulseaudio] svolume_orc.c: Initialising ORC optimized volume functions.
I: [pulseaudio] module-device-restore.c: Successfully opened database file '/home/roy/.pulse/628cda678f4bc951ffe1d9874948672d-device-volumes'.
I: [pulseaudio] module.c: Loaded "module-device-restore" (index: #0; argument: "").
I: [pulseaudio] module-stream-restore.c: Successfully opened database file '/home/roy/.pulse/628cda678f4bc951ffe1d9874948672d-stream-volumes'.
I: [pulseaudio] module.c: Loaded "module-stream-restore" (index: #1; argument: "").
I: [pulseaudio] module-card-restore.c: Successfully opened database file '/home/roy/.pulse/628cda678f4bc951ffe1d9874948672d-card-database'.
I: [pulseaudio] module.c: Loaded "module-card-restore" (index: #2; argument: "").
I: [pulseaudio] module.c: Loaded "module-augment-properties" (index: #3; argument: "").
I: [pulseaudio] (alsa-lib)utils.c: could not open configuration file /usr/share/alsa/ucm/Ensoniq AudioPCI/Ensoniq AudioPCI.conf
I: [pulseaudio] (alsa-lib)parser.c: error: could not parse configuration for card Ensoniq AudioPCI
I: [pulseaudio] (alsa-lib)main.c: error: failed to import Ensoniq AudioPCI use case configuration -2
I: [pulseaudio] alsa-ucm.c: UCM not available for card Ensoniq AudioPCI
I: [pulseaudio] alsa-util.c: Successfully attached to mixer 'hw:0'
I: [pulseaudio] (alsa-lib)control.c: Invalid CTL front:0
I: [pulseaudio] alsa-util.c: Unable to attach to mixer front:0: No such file or directory
I: [pulseaudio] alsa-util.c: Successfully attached to mixer 'hw:0'
I: [pulseaudio] alsa-util.c: Failed to set hardware parameters on plug:hw:0: Invalid argument
I: [pulseaudio] (alsa-lib)setup.c: Cannot obtain info for CTL elem (PCM,'IEC958 Playback PCM Stream',0,0,0): No such file or directory
I: [pulseaudio] alsa-util.c: Error opening PCM device iec958:0: No such file or directory
I: [pulseaudio] alsa-util.c: Successfully attached to mixer 'hw:0'
I: [pulseaudio] (alsa-lib)control.c: Invalid CTL front:0
I: [pulseaudio] alsa-util.c: Unable to attach to mixer front:0: No such file or directory
I: [pulseaudio] alsa-util.c: Successfully attached to mixer 'hw:0'
I: [pulseaudio] (alsa-lib)setup.c: Cannot obtain info for CTL elem (MIXER,'AC97 2ch->4ch Copy Switch',0,0,0): No such file or directory
I: [pulseaudio] alsa-util.c: Error opening PCM device surround40:0: No such file or directory
I: [pulseaudio] (alsa-lib)conf.c: Unknown parameters 0
I: [pulseaudio] (alsa-lib)pcm.c: Unknown PCM surround41:0
I: [pulseaudio] alsa-util.c: Error opening PCM device surround41:0: Invalid argument
I: [pulseaudio] (alsa-lib)conf.c: Unknown parameters 0
I: [pulseaudio] (alsa-lib)pcm.c: Unknown PCM surround50:0
I: [pulseaudio] alsa-util.c: Error opening PCM device surround50:0: Invalid argument
I: [pulseaudio] (alsa-lib)conf.c: Unknown parameters 0
I: [pulseaudio] (alsa-lib)pcm.c: Unknown PCM surround51:0
I: [pulseaudio] alsa-util.c: Error opening PCM device surround51:0: Invalid argument
I: [pulseaudio] (alsa-lib)conf.c: Unknown parameters 0
I: [pulseaudio] (alsa-lib)pcm.c: Unknown PCM surround71:0
I: [pulseaudio] alsa-util.c: Error opening PCM device surround71:0: Invalid argument
I: [pulseaudio] (alsa-lib)setup.c: Cannot obtain info for CTL elem (PCM,'IEC958 Playback PCM Stream',0,0,0): No such file or directory
I: [pulseaudio] alsa-util.c: Error opening PCM device iec958:0: No such file or directory
I: [pulseaudio] (alsa-lib)pcm.c: Unknown PCM a52:0
I: [pulseaudio] alsa-util.c: Error opening PCM device a52:0: No such file or directory
I: [pulseaudio] (alsa-lib)pcm.c: Unknown PCM a52:0
I: [pulseaudio] alsa-util.c: Error opening PCM device a52:0: No such file or directory
I: [pulseaudio] (alsa-lib)pcm.c: Unknown PCM dca:0
I: [pulseaudio] alsa-util.c: Error opening PCM device dca:0: No such file or directory
I: [pulseaudio] (alsa-lib)conf.c: Unknown parameters 0
I: [pulseaudio] (alsa-lib)pcm.c: Unknown PCM hdmi:0
I: [pulseaudio] alsa-util.c: Error opening PCM device hdmi:0: Invalid argument
I: [pulseaudio] module-card-restore.c: Restoring port latency offsets for card alsa_card.pci-0000_02_02.0.
I: [pulseaudio] card.c: Created 0 "alsa_card.pci-0000_02_02.0"
I: [pulseaudio] alsa-sink.c: Successfully opened device front:0.
I: [pulseaudio] alsa-sink.c: Selected mapping 'Analogue Stereo' (analog-stereo).
I: [pulseaudio] alsa-sink.c: Successfully enabled mmap() mode.
I: [pulseaudio] (alsa-lib)control.c: Invalid CTL front:0
I: [pulseaudio] alsa-util.c: Unable to attach to mixer front:0: No such file or directory
I: [pulseaudio] alsa-util.c: Successfully attached to mixer 'hw:0'
I: [pulseaudio] module-device-restore.c: Restoring volume for sink alsa_output.pci-0000_02_02.0.analog-stereo.
I: [pulseaudio] module-device-restore.c: Restored volume: 0:  61% 1:  61%
I: [pulseaudio] module-device-restore.c: Restoring mute state for sink alsa_output.pci-0000_02_02.0.analog-stereo.
I: [pulseaudio] sink.c: Created sink 0 "alsa_output.pci-0000_02_02.0.analog-stereo" with sample spec s16le 2ch 44100Hz and channel map front-left,front-right
I: [pulseaudio] sink.c:     alsa.resolution_bits = "16"
I: [pulseaudio] sink.c:     device.api = "alsa"
I: [pulseaudio] sink.c:     device.class = "sound"
I: [pulseaudio] sink.c:     alsa.class = "generic"
I: [pulseaudio] sink.c:     alsa.subclass = "generic-mix"
I: [pulseaudio] sink.c:     alsa.name = "ES1371 DAC2/ADC"
I: [pulseaudio] sink.c:     alsa.id = "ES1371/1"
I: [pulseaudio] sink.c:     alsa.subdevice = "0"
I: [pulseaudio] sink.c:     alsa.subdevice_name = "subdevice #0"
I: [pulseaudio] sink.c:     alsa.device = "0"
I: [pulseaudio] sink.c:     alsa.card = "0"
I: [pulseaudio] sink.c:     alsa.card_name = "Ensoniq AudioPCI"
I: [pulseaudio] sink.c:     alsa.long_card_name = "Ensoniq AudioPCI ENS1371 at 0x2080, irq 16"
I: [pulseaudio] sink.c:     alsa.driver_name = "snd_ens1371"
I: [pulseaudio] sink.c:     device.bus_path = "pci-0000:02:02.0"
I: [pulseaudio] sink.c:     sysfs.path = "/devices/pci0000:00/0000:00:11.0/0000:02:02.0/sound/card0"
I: [pulseaudio] sink.c:     device.bus = "pci"
I: [pulseaudio] sink.c:     device.vendor.id = "1274"
I: [pulseaudio] sink.c:     device.vendor.name = "Ensoniq"
I: [pulseaudio] sink.c:     device.product.id = "1371"
I: [pulseaudio] sink.c:     device.product.name = "Creative Sound Blaster AudioPCI64V, AudioPCI128"
I: [pulseaudio] sink.c:     device.string = "front:0"
I: [pulseaudio] sink.c:     device.buffering.buffer_size = "14112"
I: [pulseaudio] sink.c:     device.buffering.fragment_size = "1764"
I: [pulseaudio] sink.c:     device.access_mode = "mmap"
I: [pulseaudio] sink.c:     device.profile.name = "analog-stereo"
I: [pulseaudio] sink.c:     device.profile.description = "Analogue Stereo"
I: [pulseaudio] sink.c:     device.description = "Creative Sound Blaster AudioPCI64V, AudioPCI128 Analogue Stereo"
I: [pulseaudio] sink.c:     alsa.mixer_name = "Cirrus Logic CS4297A rev 3"
I: [pulseaudio] sink.c:     alsa.components = "AC97a:43525913"
I: [pulseaudio] sink.c:     module-udev-detect.discovered = "1"
I: [pulseaudio] sink.c:     device.icon_name = "audio-card-pci"
I: [pulseaudio] source.c: Created source 0 "alsa_output.pci-0000_02_02.0.analog-stereo.monitor" with sample spec s16le 2ch 44100Hz and channel map front-left,front-right
I: [pulseaudio] source.c:     device.description = "Monitor of Creative Sound Blaster AudioPCI64V, AudioPCI128 Analogue Stereo"
I: [pulseaudio] source.c:     device.class = "monitor"
I: [pulseaudio] source.c:     alsa.card = "0"
I: [pulseaudio] source.c:     alsa.card_name = "Ensoniq AudioPCI"
I: [pulseaudio] source.c:     alsa.long_card_name = "Ensoniq AudioPCI ENS1371 at 0x2080, irq 16"
I: [pulseaudio] source.c:     alsa.driver_name = "snd_ens1371"
I: [pulseaudio] source.c:     device.bus_path = "pci-0000:02:02.0"
I: [pulseaudio] source.c:     sysfs.path = "/devices/pci0000:00/0000:00:11.0/0000:02:02.0/sound/card0"
I: [pulseaudio] source.c:     device.bus = "pci"
I: [pulseaudio] source.c:     device.vendor.id = "1274"
I: [pulseaudio] source.c:     device.vendor.name = "Ensoniq"
I: [pulseaudio] source.c:     device.product.id = "1371"
I: [pulseaudio] source.c:     device.product.name = "Creative Sound Blaster AudioPCI64V, AudioPCI128"
I: [pulseaudio] source.c:     device.string = "0"
I: [pulseaudio] source.c:     module-udev-detect.discovered = "1"
I: [pulseaudio] source.c:     device.icon_name = "audio-card-pci"
I: [pulseaudio] alsa-sink.c: Using 8.0 fragments of size 1764 bytes (10.00ms), buffer size is 14112 bytes (80.00ms)
I: [pulseaudio] alsa-sink.c: Successfully enabled deferred volume.
I: [pulseaudio] alsa-sink.c: Hardware volume ranges from -129.00 dB to 60.00 dB.
I: [pulseaudio] alsa-sink.c: Fixing base volume to -60.00 dB
I: [pulseaudio] alsa-sink.c: Using hardware volume control. Hardware dB scale supported.
I: [pulseaudio] alsa-sink.c: Using hardware mute control.
I: [alsa-sink-ES1371/1] core-util.c: Successfully enabled SCHED_RR scheduling for thread, with priority 5.
I: [alsa-sink-ES1371/1] alsa-sink.c: Starting playback.
E: [alsa-sink-ES1371/1] alsa-sink.c: ALSA woke us up to write new data to the device, but there was actually nothing to write!
E: [alsa-sink-ES1371/1] alsa-sink.c: Most likely this is a bug in the ALSA driver 'snd_ens1371'. Please report this issue to the ALSA developers.
E: [alsa-sink-ES1371/1] alsa-sink.c: We were woken up with POLLOUT set -- however a subsequent snd_pcm_avail() returned 0 or another value < min_avail.
I: [pulseaudio] alsa-source.c: Successfully opened device front:0.
I: [pulseaudio] alsa-source.c: Selected mapping 'Analogue Stereo' (analog-stereo).
I: [pulseaudio] alsa-source.c: Successfully enabled mmap() mode.
I: [pulseaudio] (alsa-lib)control.c: Invalid CTL front:0
I: [pulseaudio] alsa-util.c: Unable to attach to mixer front:0: No such file or directory
I: [pulseaudio] alsa-util.c: Successfully attached to mixer 'hw:0'
I: [pulseaudio] source.c: Created source 1 "alsa_input.pci-0000_02_02.0.analog-stereo" with sample spec s16le 2ch 44100Hz and channel map front-left,front-right
I: [pulseaudio] source.c:     alsa.resolution_bits = "16"
I: [pulseaudio] source.c:     device.api = "alsa"
I: [pulseaudio] source.c:     device.class = "sound"
I: [pulseaudio] source.c:     alsa.class = "generic"
I: [pulseaudio] source.c:     alsa.subclass = "generic-mix"
I: [pulseaudio] source.c:     alsa.name = "ES1371 DAC2/ADC"
I: [pulseaudio] source.c:     alsa.id = "ES1371/1"
I: [pulseaudio] source.c:     alsa.subdevice = "0"
I: [pulseaudio] source.c:     alsa.subdevice_name = "subdevice #0"
I: [pulseaudio] source.c:     alsa.device = "0"
I: [pulseaudio] source.c:     alsa.card = "0"
I: [pulseaudio] source.c:     alsa.card_name = "Ensoniq AudioPCI"
I: [pulseaudio] source.c:     alsa.long_card_name = "Ensoniq AudioPCI ENS1371 at 0x2080, irq 16"
I: [pulseaudio] source.c:     alsa.driver_name = "snd_ens1371"
I: [pulseaudio] source.c:     device.bus_path = "pci-0000:02:02.0"
I: [pulseaudio] source.c:     sysfs.path = "/devices/pci0000:00/0000:00:11.0/0000:02:02.0/sound/card0"
I: [pulseaudio] source.c:     device.bus = "pci"
I: [pulseaudio] source.c:     device.vendor.id = "1274"
I: [pulseaudio] source.c:     device.vendor.name = "Ensoniq"
I: [pulseaudio] source.c:     device.product.id = "1371"
I: [pulseaudio] source.c:     device.product.name = "Creative Sound Blaster AudioPCI64V, AudioPCI128"
I: [pulseaudio] source.c:     device.string = "front:0"
I: [pulseaudio] source.c:     device.buffering.buffer_size = "14112"
I: [pulseaudio] source.c:     device.buffering.fragment_size = "1764"
I: [pulseaudio] source.c:     device.access_mode = "mmap"
I: [pulseaudio] source.c:     device.profile.name = "analog-stereo"
I: [pulseaudio] source.c:     device.profile.description = "Analogue Stereo"
I: [pulseaudio] source.c:     device.description = "Creative Sound Blaster AudioPCI64V, AudioPCI128 Analogue Stereo"
I: [pulseaudio] source.c:     alsa.mixer_name = "Cirrus Logic CS4297A rev 3"
I: [pulseaudio] source.c:     alsa.components = "AC97a:43525913"
I: [pulseaudio] source.c:     module-udev-detect.discovered = "1"
I: [pulseaudio] source.c:     device.icon_name = "audio-card-pci"
I: [pulseaudio] alsa-source.c: Using 8.0 fragments of size 1764 bytes (10.00ms), buffer size is 14112 bytes (80.00ms)
I: [pulseaudio] alsa-source.c: Successfully enabled deferred volume.
I: [pulseaudio] alsa-source.c: Hardware volume ranges from 0.00 dB to 22.50 dB.
I: [pulseaudio] alsa-source.c: Fixing base volume to -22.50 dB
I: [pulseaudio] alsa-source.c: Using hardware volume control. Hardware dB scale supported.
I: [pulseaudio] alsa-source.c: Using hardware mute control.
I: [alsa-source-ES1371/1] core-util.c: Successfully enabled SCHED_RR scheduling for thread, with priority 5.
I: [alsa-source-ES1371/1] alsa-source.c: Starting capture.
I: [pulseaudio] module.c: Loaded "module-alsa-card" (index: #4; argument: "device_id="0" name="pci-0000_02_02.0" card_name="alsa_card.pci-0000_02_02.0" namereg_fail=false tsched=no fixed_latency_range=no ignore_dB=no deferred_volume=yes use_ucm=yes card_properties="module-udev-detect.discovered=1"").
I: [pulseaudio] module-udev-detect.c: Card /devices/pci0000:00/0000:00:11.0/0000:02:02.0/sound/card0 (alsa_card.pci-0000_02_02.0) module loaded.
I: [pulseaudio] module-udev-detect.c: Found 1 cards.
I: [pulseaudio] module.c: Loaded "module-udev-detect" (index: #5; argument: "tsched=0").
I: [pulseaudio] module.c: Loaded "module-bluetooth-discover" (index: #6; argument: "").
I: [pulseaudio] module.c: Loaded "module-esound-protocol-unix" (index: #7; argument: "").
I: [pulseaudio] module.c: Loaded "module-native-protocol-unix" (index: #8; argument: "").
I: [pulseaudio] module.c: Loaded "module-gconf" (index: #9; argument: "").
I: [pulseaudio] module-default-device-restore.c: Restored default sink 'alsa_output.pci-0000_02_02.0.analog-stereo'.
I: [pulseaudio] module-default-device-restore.c: Restored default source 'alsa_input.pci-0000_02_02.0.analog-stereo'.
I: [pulseaudio] module.c: Loaded "module-default-device-restore" (index: #10; argument: "").
I: [pulseaudio] module.c: Loaded "module-rescue-streams" (index: #11; argument: "").
I: [pulseaudio] module.c: Loaded "module-always-sink" (index: #12; argument: "").
I: [pulseaudio] module.c: Loaded "module-intended-roles" (index: #13; argument: "").
I: [pulseaudio] module.c: Loaded "module-suspend-on-idle" (index: #14; argument: "").
E: [pulseaudio] ltdl-bind-now.c: Failed to open module module-console-kit.so: module-console-kit.so: cannot open shared object file: No such file or directory
E: [pulseaudio] module.c: Failed to open module "module-console-kit".
E: [pulseaudio] main.c: Module load failed.
E: [pulseaudio] main.c: Failed to initialise daemon.
I: [pulseaudio] module.c: Unloading "module-suspend-on-idle" (index: #14).
I: [pulseaudio] module.c: Unloaded "module-suspend-on-idle" (index: #14).
I: [pulseaudio] module.c: Unloading "module-intended-roles" (index: #13).
I: [pulseaudio] module.c: Unloaded "module-intended-roles" (index: #13).
I: [pulseaudio] module.c: Unloading "module-always-sink" (index: #12).
I: [pulseaudio] module.c: Unloaded "module-always-sink" (index: #12).
I: [pulseaudio] module.c: Unloading "module-rescue-streams" (index: #11).
I: [pulseaudio] module.c: Unloaded "module-rescue-streams" (index: #11).
I: [pulseaudio] module.c: Unloading "module-default-device-restore" (index: #10).
I: [pulseaudio] module.c: Unloaded "module-default-device-restore" (index: #10).
I: [pulseaudio] module.c: Unloading "module-gconf" (index: #9).
I: [pulseaudio] module.c: Unloaded "module-gconf" (index: #9).
I: [pulseaudio] module.c: Unloading "module-native-protocol-unix" (index: #8).
I: [pulseaudio] module.c: Unloaded "module-native-protocol-unix" (index: #8).
I: [pulseaudio] module.c: Unloading "module-esound-protocol-unix" (index: #7).
I: [pulseaudio] module.c: Unloaded "module-esound-protocol-unix" (index: #7).
I: [pulseaudio] module.c: Unloading "module-bluetooth-discover" (index: #6).
I: [pulseaudio] module.c: Unloaded "module-bluetooth-discover" (index: #6).
I: [pulseaudio] module.c: Unloading "module-udev-detect" (index: #5).
I: [pulseaudio] module.c: Unloaded "module-udev-detect" (index: #5).
I: [pulseaudio] module.c: Unloading "module-alsa-card" (index: #4).
I: [pulseaudio] sink.c: Freeing sink 0 "alsa_output.pci-0000_02_02.0.analog-stereo"
I: [pulseaudio] source.c: Freeing source 0 "alsa_output.pci-0000_02_02.0.analog-stereo.monitor"
I: [pulseaudio] source.c: Freeing source 1 "alsa_input.pci-0000_02_02.0.analog-stereo"
I: [pulseaudio] card.c: Freed 0 "alsa_card.pci-0000_02_02.0"
I: [pulseaudio] module.c: Unloaded "module-alsa-card" (index: #4).
I: [pulseaudio] module.c: Unloading "module-augment-properties" (index: #3).
I: [pulseaudio] module.c: Unloaded "module-augment-properties" (index: #3).
I: [pulseaudio] module.c: Unloading "module-card-restore" (index: #2).
I: [pulseaudio] module.c: Unloaded "module-card-restore" (index: #2).
I: [pulseaudio] module.c: Unloading "module-stream-restore" (index: #1).
I: [pulseaudio] module.c: Unloaded "module-stream-restore" (index: #1).
I: [pulseaudio] module.c: Unloading "module-device-restore" (index: #0).
I: [pulseaudio] module.c: Unloaded "module-device-restore" (index: #0).
I: [pulseaudio] main.c: Daemon terminated.

---

