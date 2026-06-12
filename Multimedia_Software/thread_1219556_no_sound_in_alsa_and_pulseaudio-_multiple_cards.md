---
title: "no sound in alsa and pulseaudio- multiple cards"
date: 2009-07-21
forum: Multimedia Software
---

### Post by a_posse_ad_esse on 2009-07-21
This seems to be a common problem, but none of the solutions (a comprehensive list of what has been done can be found [here]("http://www.ubuntugeek.com/simple-guide-to-sound-solutions-for-hardyintrepid-and-jaunty-jackalope-users.html")) have helped.  

What puzzles me is that the sound worked out-of-the-box before, even while running Jaunty. I combined two of my systems into the current setup by moving the current motherboard into a new case, added peripherals, and reinstalled.  The wiring is correct as everything works except for the sound.  I added a pci soundcard to the setup and made it default with asoundconf, and have been met with the same silence.  The modules are loaded.

I'm sorry for the lengthy output, but this is the only thing that I've found that may be helpful.  

pkill pulseaudio; sleep 2; pulseaudio -vv yields (with sound event)
```

I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
D: main.c: Started as real root: no, suid root: yes
I: main.c: We're in the group 'pulse-rt', allowing high-priority scheduling.
I: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
I: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
I: core-util.c: Successfully gained nice level -11.
D: main.c: Can realtime: yes, can high-priority: yes
I: main.c: Giving up CAP_NICE
D: main.c: Can realtime: no, can high-priority: no
I: main.c: This is PulseAudio 0.9.14
D: main.c: Compilation host: i486-pc-linux-gnu
D: main.c: Compilation CFLAGS: -g -O2 -g -Wall -O3 -Wall -W -Wextra -pedantic -pipe -Wno-long-long -Wvla -Wno-overlength-strings -Wconversion -Wundef -Wformat -Wlogical-op -Wpacked -Wformat-security -Wmissing-include-dirs -Wformat-nonliteral -Wold-style-definition -Wdeclaration-after-statement -Wfloat-equal -Wmissing-declarations -Wmissing-prototypes -Wstrict-prototypes -Wredundant-decls -Wmissing-noreturn -Wshadow -Wendif-labels -Wpointer-arith -Wcast-align -Wwrite-strings -Wno-unused-parameter -ffast-math
D: main.c: Running on host: Linux i686 2.6.28-13-generic #45-Ubuntu SMP Tue Jun 30 19:49:51 UTC 2009
I: main.c: Page size is 4096 bytes
D: main.c: Compiled with Valgrind support: no
D: main.c: Running in valgrind mode: no
D: main.c: Optimized build: yes
I: main.c: Machine ID is d0640c25fe308adfc33f79f74a65e919.
I: main.c: Using runtime directory /home/tim/.pulse/d0640c25fe308adfc33f79f74a65e919:runtime.
I: main.c: Using state directory /home/tim/.pulse.
I: main.c: Running in system mode: no
I: main.c: Fresh high-resolution timers available! Bon appetit!
D: memblock.c: Using shared memory pool with 1024 slots of size 64.0 KiB each, total size is 64.0 MiB, maximum usable slot size is 65496
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9/modules/module-gconf.so': success
I: module.c: Loaded "module-gconf" (index: #0; argument: "").
I: module.c: Loaded "module-suspend-on-idle" (index: #1; argument: "").
I: module-device-restore.c: Sucessfully opened database file '/home/tim/.pulse/d0640c25fe308adfc33f79f74a65e919:device-volumes.i486-pc-linux-gnu.gdbm'.
I: module.c: Loaded "module-device-restore" (index: #2; argument: "").
I: module-stream-restore.c: Sucessfully opened database file '/home/tim/.pulse/d0640c25fe308adfc33f79f74a65e919:stream-volumes.i486-pc-linux-gnu.gdbm'.
I: module.c: Loaded "module-stream-restore" (index: #3; argument: "").
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9/modules/module-hal-detect.so': success
I: module-hal-detect.c: Trying capability alsa
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/computer_alsa_timer
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/computer_alsa_sequencer
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_1106_3059_sound_card_0_alsa_playback_1
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_1106_3059_sound_card_0_alsa_capture_1
D: module-hal-detect.c: Loading module-alsa-sink with arguments 'device_id=0 sink_name=alsa_output.pci_1106_3059_sound_card_0_alsa_playback_0 tsched=0'
D: alsa-util.c: Trying front:0 with SND_PCM_NO_AUTO_FORMAT ...
I: module-alsa-sink.c: Successfully opened device front:0.
I: module-alsa-sink.c: Successfully enabled mmap() mode.
I: (alsa-lib)control.c: Invalid CTL front:0
I: alsa-util.c: Unable to attach to mixer front:0: No such file or directory
I: alsa-util.c: Successfully attached to mixer 'hw:0'
I: alsa-util.c: Using mixer control "Master".
I: module-device-restore.c: Restoring volume for sink alsa_output.pci_1106_3059_sound_card_0_alsa_playback_0.
I: module-device-restore.c: Restoring mute state for sink alsa_output.pci_1106_3059_sound_card_0_alsa_playback_0.
I: sink.c: Created sink 0 "alsa_output.pci_1106_3059_sound_card_0_alsa_playback_0" with sample spec s16le 2ch 44100Hz and channel map front-left,front-right
I: module-device-restore.c: Restoring volume for source alsa_output.pci_1106_3059_sound_card_0_alsa_playback_0.monitor.
I: module-device-restore.c: Restoring mute state for source alsa_output.pci_1106_3059_sound_card_0_alsa_playback_0.monitor.
I: source.c: Created source 0 "alsa_output.pci_1106_3059_sound_card_0_alsa_playback_0.monitor" with sample spec s16le 2ch 44100Hz and channel map front-left,front-right
I: module-alsa-sink.c: Using 8 fragments of size 1764 bytes, buffer time is 80.00ms
D: module-alsa-sink.c: hwbuf_unused=0
D: module-alsa-sink.c: setting avail_min=1
I: module-alsa-sink.c: Volume ranges from 0 to 63.
I: module-alsa-sink.c: Volume ranges from -94.50 dB to 0.00 dB.
I: alsa-util.c: All 2 channels can be mapped to mixer channels.
I: module-alsa-sink.c: Using hardware volume control. Hardware dB scale supported.
D: alsa-util.c: snd_pcm_dump():
D: alsa-util.c: Hardware PCM card 0 'VIA 8237' device 0 subdevice 0
D: alsa-util.c: Its setup is:
D: alsa-util.c:   stream       : PLAYBACK
D: alsa-util.c:   access       : MMAP_INTERLEAVED
D: alsa-util.c:   format       : S16_LE
D: alsa-util.c:   subformat    : STD
D: alsa-util.c:   channels     : 2
D: alsa-util.c:   rate         : 44100
D: alsa-util.c:   exact rate   : 44100 (44100/1)
D: alsa-util.c:   msbits       : 16
D: alsa-util.c:   buffer_size  : 3528
D: alsa-util.c:   period_size  : 441
D: alsa-util.c:   period_time  : 10000
D: alsa-util.c:   tstamp_mode  : ENABLE
D: alsa-util.c:   period_step  : 1
D: alsa-util.c:   avail_min    : 441
D: alsa-util.c:   period_event : 0
D: alsa-util.c:   start_threshold  : -1
D: alsa-util.c:   stop_threshold   : 1849688064
D: alsa-util.c:   silence_threshold: 0
D: alsa-util.c:   silence_size : 0
D: alsa-util.c:   boundary     : 1849688064
D: module-alsa-sink.c: Thread starting up
D: rtpoll.c: Acquired POSIX realtime signal SIGRTMIN+29
D: module-alsa-sink.c: Requested volume: 0:  69% 1:  69%
D: module-alsa-sink.c: Got hardware volume: 0:  69% 1:  69%
D: module-alsa-sink.c: Calculated software volume: 0: 100% 1: 100%
I: module-alsa-sink.c: Starting playback.
D: module-suspend-on-idle.c: Source alsa_output.pci_1106_3059_sound_card_0_alsa_playback_0.monitor becomes idle.
D: module-suspend-on-idle.c: Sink alsa_output.pci_1106_3059_sound_card_0_alsa_playback_0 becomes idle.
I: module.c: Loaded "module-alsa-sink" (index: #4; argument: "device_id=0 sink_name=alsa_output.pci_1106_3059_sound_card_0_alsa_playback_0 tsched=0").
D: module-hal-detect.c: Loading module-alsa-source with arguments 'device_id=0 source_name=alsa_input.pci_1106_3059_sound_card_0_alsa_capture_0 tsched=0'
D: alsa-util.c: Trying front:0 with SND_PCM_NO_AUTO_FORMAT ...
I: module-alsa-source.c: Successfully opened device front:0.
I: module-alsa-source.c: Successfully enabled mmap() mode.
I: (alsa-lib)control.c: Invalid CTL front:0
I: alsa-util.c: Unable to attach to mixer front:0: No such file or directory
I: alsa-util.c: Successfully attached to mixer 'hw:0'
I: alsa-util.c: Using mixer control "Capture".
I: module-device-restore.c: Restoring volume for source alsa_input.pci_1106_3059_sound_card_0_alsa_capture_0.
I: module-device-restore.c: Restoring mute state for source alsa_input.pci_1106_3059_sound_card_0_alsa_capture_0.
I: source.c: Created source 1 "alsa_input.pci_1106_3059_sound_card_0_alsa_capture_0" with sample spec s16le 2ch 44100Hz and channel map front-left,front-right
I: module-alsa-source.c: Using 8 fragments of size 1764 bytes, buffer time is 80.00ms
D: module-alsa-source.c: hwbuf_unused=0
D: module-alsa-source.c: setting avail_min=1
I: module-alsa-source.c: Volume ranges from 0 to 15.
I: module-alsa-source.c: Volume ranges from 0.00 dB to 22.50 dB.
I: alsa-util.c: All 2 channels can be mapped to mixer channels.
I: module-alsa-source.c: Using hardware volume control. Hardware dB scale supported.
D: alsa-util.c: snd_pcm_dump():
D: alsa-util.c: Hardware PCM card 0 'VIA 8237' device 0 subdevice 0
D: alsa-util.c: Its setup is:
D: alsa-util.c:   stream       : CAPTURE
D: alsa-util.c:   access       : MMAP_INTERLEAVED
D: alsa-util.c:   format       : S16_LE
D: alsa-util.c:   subformat    : STD
D: alsa-util.c:   channels     : 2
D: alsa-util.c:   rate         : 44100
D: alsa-util.c:   exact rate   : 44100 (44100/1)
D: alsa-util.c:   msbits       : 16
D: alsa-util.c:   buffer_size  : 3528
D: alsa-util.c:   period_size  : 441
D: alsa-util.c:   period_time  : 10000
D: alsa-util.c:   tstamp_mode  : ENABLE
D: alsa-util.c:   period_step  : 1
D: alsa-util.c:   avail_min    : 441
D: alsa-util.c:   period_event : 0
D: alsa-util.c:   start_threshold  : -1
D: alsa-util.c:   stop_threshold   : 1849688064
D: alsa-util.c:   silence_threshold: 0
D: alsa-util.c:   silence_size : 0
D: alsa-util.c:   boundary     : 1849688064
D: module-alsa-source.c: Thread starting up
D: rtpoll.c: Acquired POSIX realtime signal SIGRTMIN+28
D: module-alsa-source.c: Requested volume: 0:  87% 1:  87%
D: module-alsa-source.c: Got hardware volume: 0:  87% 1:  87%
D: module-alsa-source.c: Calculated software volume: 0: 100% 1: 100%
D: module-suspend-on-idle.c: Source alsa_input.pci_1106_3059_sound_card_0_alsa_capture_0 becomes idle.
I: module.c: Loaded "module-alsa-source" (index: #5; argument: "device_id=0 source_name=alsa_input.pci_1106_3059_sound_card_0_alsa_capture_0 tsched=0").
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_1106_3059_sound_card_0_alsa_control__1
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_1102_6_sound_card_0_alsa_playback_2
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_1102_6_sound_card_0_alsa_playback_1
D: module-hal-detect.c: Loading module-alsa-sink with arguments 'device_id=1 sink_name=alsa_output.pci_1102_6_sound_card_0_alsa_playback_0 tsched=0'
D: alsa-util.c: Trying front:1 with SND_PCM_NO_AUTO_FORMAT ...
W: alsa-util.c: Device front:1 doesn't support 44100 Hz, changed to 48000 Hz.
I: module-alsa-sink.c: Successfully opened device front:1.
I: module-alsa-sink.c: Successfully enabled mmap() mode.
I: (alsa-lib)control.c: Invalid CTL front:1
I: alsa-util.c: Unable to attach to mixer front:1: No such file or directory
I: alsa-util.c: Successfully attached to mixer 'hw:1'
I: alsa-util.c: Using mixer control "Master".
I: module-device-restore.c: Restoring volume for sink alsa_output.pci_1102_6_sound_card_0_alsa_playback_0.
I: module-device-restore.c: Restoring mute state for sink alsa_output.pci_1102_6_sound_card_0_alsa_playback_0.
I: sink.c: Created sink 1 "alsa_output.pci_1102_6_sound_card_0_alsa_playback_0" with sample spec s16le 2ch 48000Hz and channel map front-left,front-right
I: module-device-restore.c: Restoring volume for source alsa_output.pci_1102_6_sound_card_0_alsa_playback_0.monitor.
I: module-device-restore.c: Restoring mute state for source alsa_output.pci_1102_6_sound_card_0_alsa_playback_0.monitor.
I: source.c: Created source 2 "alsa_output.pci_1102_6_sound_card_0_alsa_playback_0.monitor" with sample spec s16le 2ch 48000Hz and channel map front-left,front-right
I: module-alsa-sink.c: Using 8 fragments of size 1920 bytes, buffer time is 80.00ms
D: module-alsa-sink.c: hwbuf_unused=0
D: module-alsa-sink.c: setting avail_min=1
I: module-alsa-sink.c: Volume ranges from 0 to 31.
I: module-alsa-sink.c: Volume ranges from -46.50 dB to 0.00 dB.
I: alsa-util.c: All 2 channels can be mapped to mixer channels.
I: module-alsa-sink.c: Using hardware volume control. Hardware dB scale supported.
D: alsa-util.c: snd_pcm_dump():
D: alsa-util.c: Hardware PCM card 1 'Dell Sound Blaster Live!' device 0 subdevice 0
D: alsa-util.c: Its setup is:
D: alsa-util.c:   stream       : PLAYBACK
D: alsa-util.c:   access       : MMAP_INTERLEAVED
D: alsa-util.c:   format       : S16_LE
D: alsa-util.c:   subformat    : STD
D: alsa-util.c:   channels     : 2
D: alsa-util.c:   rate         : 48000
D: alsa-util.c:   exact rate   : 48000 (48000/1)
D: alsa-util.c:   msbits       : 16
D: alsa-util.c:   buffer_size  : 3840
D: alsa-util.c:   period_size  : 480
D: alsa-util.c:   period_time  : 10000
D: alsa-util.c:   tstamp_mode  : ENABLE
D: alsa-util.c:   period_step  : 1
D: alsa-util.c:   avail_min    : 480
D: alsa-util.c:   period_event : 0
D: alsa-util.c:   start_threshold  : -1
D: alsa-util.c:   stop_threshold   : 2013265920
D: alsa-util.c:   silence_threshold: 0
D: alsa-util.c:   silence_size : 0
D: alsa-util.c:   boundary     : 2013265920
D: module-alsa-sink.c: Thread starting up
D: rtpoll.c: Acquired POSIX realtime signal SIGRTMIN+27
D: module-alsa-sink.c: Requested volume: 0:  87% 1:  87%
D: module-alsa-sink.c: Got hardware volume: 0:  87% 1:  87%
D: module-alsa-sink.c: Calculated software volume: 0: 100% 1: 100%
I: module-alsa-sink.c: Starting playback.
D: module-suspend-on-idle.c: Source alsa_output.pci_1102_6_sound_card_0_alsa_playback_0.monitor becomes idle.
D: module-suspend-on-idle.c: Sink alsa_output.pci_1102_6_sound_card_0_alsa_playback_0 becomes idle.
I: module.c: Loaded "module-alsa-sink" (index: #6; argument: "device_id=1 sink_name=alsa_output.pci_1102_6_sound_card_0_alsa_playback_0 tsched=0").
D: module-hal-detect.c: Loading module-alsa-source with arguments 'device_id=1 source_name=alsa_input.pci_1102_6_sound_card_0_alsa_capture_0 tsched=0'
D: alsa-util.c: Trying front:1 with SND_PCM_NO_AUTO_FORMAT ...
W: alsa-util.c: Device front:1 doesn't support 44100 Hz, changed to 48000 Hz.
I: module-alsa-source.c: Successfully opened device front:1.
I: module-alsa-source.c: Successfully enabled mmap() mode.
I: (alsa-lib)control.c: Invalid CTL front:1
I: alsa-util.c: Unable to attach to mixer front:1: No such file or directory
I: alsa-util.c: Successfully attached to mixer 'hw:1'
I: alsa-util.c: Using mixer control "Capture".
I: module-device-restore.c: Restoring volume for source alsa_input.pci_1102_6_sound_card_0_alsa_capture_0.
I: module-device-restore.c: Restoring mute state for source alsa_input.pci_1102_6_sound_card_0_alsa_capture_0.
I: source.c: Created source 3 "alsa_input.pci_1102_6_sound_card_0_alsa_capture_0" with sample spec s16le 2ch 48000Hz and channel map front-left,front-right
I: module-alsa-source.c: Using 2 fragments of size 7680 bytes, buffer time is 80.00ms
D: module-alsa-source.c: hwbuf_unused=0
D: module-alsa-source.c: setting avail_min=1
I: module-alsa-source.c: Volume ranges from 0 to 15.
I: module-alsa-source.c: Volume ranges from 0.00 dB to 22.50 dB.
I: alsa-util.c: All 2 channels can be mapped to mixer channels.
I: module-alsa-source.c: Using hardware volume control. Hardware dB scale supported.
D: alsa-util.c: snd_pcm_dump():
D: alsa-util.c: Hardware PCM card 1 'Dell Sound Blaster Live!' device 0 subdevice 0
D: alsa-util.c: Its setup is:
D: alsa-util.c:   stream       : CAPTURE
D: alsa-util.c:   access       : MMAP_INTERLEAVED
D: alsa-util.c:   format       : S16_LE
D: alsa-util.c:   subformat    : STD
D: alsa-util.c:   channels     : 2
D: alsa-util.c:   rate         : 48000
D: alsa-util.c:   exact rate   : 48000 (48000/1)
D: alsa-util.c:   msbits       : 16
D: alsa-util.c:   buffer_size  : 3840
D: alsa-util.c:   period_size  : 1920
D: alsa-util.c:   period_time  : 40000
D: alsa-util.c:   tstamp_mode  : ENABLE
D: alsa-util.c:   period_step  : 1
D: alsa-util.c:   avail_min    : 1920
D: alsa-util.c:   period_event : 0
D: alsa-util.c:   start_threshold  : -1
D: alsa-util.c:   stop_threshold   : 2013265920
D: alsa-util.c:   silence_threshold: 0
D: alsa-util.c:   silence_size : 0
D: alsa-util.c:   boundary     : 2013265920
D: module-alsa-source.c: Thread starting up
D: rtpoll.c: Acquired POSIX realtime signal SIGRTMIN+26
D: module-alsa-source.c: Requested volume: 0:  92% 1:  92%
D: module-alsa-source.c: Got hardware volume: 0:  94% 1:  94%
D: module-alsa-source.c: Calculated software volume: 0:  97% 1:  97%
D: module-suspend-on-idle.c: Source alsa_input.pci_1102_6_sound_card_0_alsa_capture_0 becomes idle.
I: module.c: Loaded "module-alsa-source" (index: #7; argument: "device_id=1 source_name=alsa_input.pci_1102_6_sound_card_0_alsa_capture_0 tsched=0").
I: module-alsa-sink.c: Underrun!
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_1102_6_sound_card_0_alsa_midi_0
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_1102_6_sound_card_0_alsa_control__1
I: module-hal-detect.c: Loaded 4 modules.
I: module.c: Loaded "module-hal-detect" (index: #8; argument: "tsched=0").
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9/modules/module-esound-protocol-unix.so': success
I: module.c: Loaded "module-esound-protocol-unix" (index: #9; argument: "").
I: module.c: Loaded "module-native-protocol-unix" (index: #10; argument: "").
I: module-default-device-restore.c: Restored default sink 'alsa_output.pci_1106_3059_sound_card_0_alsa_playback_0'.
D: core-subscribe.c: Dropped redundant event due to change event.
I: module-default-device-restore.c: Restored default source 'alsa_input.pci_1106_3059_sound_card_0_alsa_capture_0'.
I: module.c: Loaded "module-default-device-restore" (index: #11; argument: "").
I: module.c: Loaded "module-rescue-streams" (index: #12; argument: "").
I: module.c: Loaded "module-always-sink" (index: #13; argument: "").
I: client.c: Created 0 "ConsoleKit Session /org/freedesktop/ConsoleKit/Session9"
D: module-console-kit.c: Added new session /org/freedesktop/ConsoleKit/Session9
I: module.c: Loaded "module-console-kit" (index: #14; argument: "").
I: module.c: Loaded "module-position-event-sounds" (index: #15; argument: "").
I: main.c: Daemon startup complete.
D: module-hal-detect.c: dbus: interface=org.freedesktop.DBus, path=/org/freedesktop/DBus, member=NameAcquired
D: module-console-kit.c: dbus: interface=org.freedesktop.DBus, path=/org/freedesktop/DBus, member=NameAcquired
I: module-suspend-on-idle.c: Sink alsa_output.pci_1106_3059_sound_card_0_alsa_playback_0 idle for too long, suspending ...
I: module-alsa-sink.c: Device suspended...
I: module-suspend-on-idle.c: Source alsa_output.pci_1106_3059_sound_card_0_alsa_playback_0.monitor idle for too long, suspending ...
I: module-suspend-on-idle.c: Source alsa_input.pci_1106_3059_sound_card_0_alsa_capture_0 idle for too long, suspending ...
I: module-alsa-source.c: Device suspended...
I: module-suspend-on-idle.c: Source alsa_output.pci_1102_6_sound_card_0_alsa_playback_0.monitor idle for too long, suspending ...
I: module-suspend-on-idle.c: Sink alsa_output.pci_1102_6_sound_card_0_alsa_playback_0 idle for too long, suspending ...
I: module-alsa-sink.c: Device suspended...
I: module-suspend-on-idle.c: Source alsa_input.pci_1102_6_sound_card_0_alsa_capture_0 idle for too long, suspending ...
I: module-alsa-source.c: Device suspended...
^CE: module-gconf.c: Unable to read or parse data from client.
I: module.c: Unloading "module-gconf" (index: #0).
I: module.c: Unloaded "module-gconf" (index: #0).
I: main.c: Got signal SIGINT.
I: main.c: Exiting.
I: main.c: Daemon shutdown initiated.
I: module.c: Unloading "module-suspend-on-idle" (index: #1).
I: module.c: Unloaded "module-suspend-on-idle" (index: #1).
I: module.c: Unloading "module-device-restore" (index: #2).
I: module.c: Unloaded "module-device-restore" (index: #2).
I: module.c: Unloading "module-stream-restore" (index: #3).
I: module.c: Unloaded "module-stream-restore" (index: #3).
I: module.c: Unloading "module-alsa-sink" (index: #4).
D: module-rescue-streams.c: No sink inputs to move away.
D: module-rescue-streams.c: No source outputs to move away.
D: module-alsa-sink.c: Thread shutting down
I: sink.c: Freeing sink 0 "alsa_output.pci_1106_3059_sound_card_0_alsa_playback_0"
I: source.c: Freeing source 0 "alsa_output.pci_1106_3059_sound_card_0_alsa_playback_0.monitor"
I: module.c: Unloaded "module-alsa-sink" (index: #4).
I: module.c: Unloading "module-alsa-source" (index: #5).
D: module-rescue-streams.c: No source outputs to move away.
D: module-alsa-source.c: Thread shutting down
I: source.c: Freeing source 1 "alsa_input.pci_1106_3059_sound_card_0_alsa_capture_0"
I: module.c: Unloaded "module-alsa-source" (index: #5).
I: module.c: Unloading "module-alsa-sink" (index: #6).
D: module-always-sink.c: Autoloading null-sink as no other sinks detected.
I: sink.c: Created sink 2 "auto_null" with sample spec s16le 2ch 44100Hz and channel map front-left,front-right
I: source.c: Created source 4 "auto_null.monitor" with sample spec s16le 2ch 44100Hz and channel map front-left,front-right
D: module-null-sink.c: Thread starting up
D: rtpoll.c: Acquired POSIX realtime signal SIGRTMIN+29
I: module.c: Loaded "module-null-sink" (index: #16; argument: "sink_name=auto_null").
D: module-rescue-streams.c: No sink inputs to move away.
D: module-rescue-streams.c: No source outputs to move away.
D: module-alsa-sink.c: Thread shutting down
I: sink.c: Freeing sink 1 "alsa_output.pci_1102_6_sound_card_0_alsa_playback_0"
I: source.c: Freeing source 2 "alsa_output.pci_1102_6_sound_card_0_alsa_playback_0.monitor"
I: module.c: Unloaded "module-alsa-sink" (index: #6).
I: module.c: Unloading "module-alsa-source" (index: #7).
D: module-rescue-streams.c: No source outputs to move away.
D: module-alsa-source.c: Thread shutting down
I: source.c: Freeing source 3 "alsa_input.pci_1102_6_sound_card_0_alsa_capture_0"
I: module.c: Unloaded "module-alsa-source" (index: #7).
I: module.c: Unloading "module-hal-detect" (index: #8).
I: module.c: Unloaded "module-hal-detect" (index: #8).
I: module.c: Unloading "module-esound-protocol-unix" (index: #9).
I: module.c: Unloaded "module-esound-protocol-unix" (index: #9).
I: module.c: Unloading "module-native-protocol-unix" (index: #10).
I: module.c: Unloaded "module-native-protocol-unix" (index: #10).
I: module.c: Unloading "module-default-device-restore" (index: #11).
I: module.c: Unloaded "module-default-device-restore" (index: #11).
I: module.c: Unloading "module-rescue-streams" (index: #12).
I: module.c: Unloaded "module-rescue-streams" (index: #12).
I: module.c: Unloading "module-always-sink" (index: #13).
I: module.c: Unloaded "module-always-sink" (index: #13).
I: module.c: Unloading "module-console-kit" (index: #14).
D: module-console-kit.c: Removing session /org/freedesktop/ConsoleKit/Session9
I: client.c: Freed 0 "ConsoleKit Session /org/freedesktop/ConsoleKit/Session9"
I: module.c: Unloaded "module-console-kit" (index: #14).
I: module.c: Unloading "module-position-event-sounds" (index: #15).
I: module.c: Unloaded "module-position-event-sounds" (index: #15).
I: module.c: Unloading "module-null-sink" (index: #16).
D: core-subscribe.c: Dropped redundant event due to remove event.
D: core-subscribe.c: Dropped redundant event due to remove event.
D: module-null-sink.c: Thread shutting down
I: sink.c: Freeing sink 2 "auto_null"
I: source.c: Freeing source 4 "auto_null.monitor"
I: module.c: Unloaded "module-null-sink" (index: #16).
D: core-subscribe.c: Dropped redundant event due to remove event.
I: main.c: Daemon terminated.

```

Any help would be greatly appreciated.  Thanks

---

### Post by fballem on 2009-07-21
I found this link to be really helpful: [http://www.ubuntugeek.com/sound-solutions-for-ubuntu-904-jaunty-users.html](http://www.ubuntugeek.com/sound-solutions-for-ubuntu-904-jaunty-users.html)

The only change that I would make to this process is to set the users as members of the pulse, pulse-access, and pulse-rt groups first. The process for doing this is described about 1/2 way down the article.

Hope this helps,

---

### Post by a_posse_ad_esse on 2009-07-21
Thank you for the reply.

My user and root are both members of the pulse groups, as well as me adding them to the 'audio' group.  This is what has me confused.  It really *should* be working.  I'm thinking something is broken somewhere.

---

### Post by psyke83 on 2009-07-22
> **fballem said:**
> I found this link to be really helpful: [http://www.ubuntugeek.com/sound-solutions-for-ubuntu-904-jaunty-users.html](http://www.ubuntugeek.com/sound-solutions-for-ubuntu-904-jaunty-users.html)

The only change that I would make to this process is to set the users as members of the pulse, pulse-access, and pulse-rt groups first. The process for doing this is described about 1/2 way down the article.

Hope this helps,

Please don't link to a site that plagiarizes posts from this forum - the copied posts are often outdated and off-site comments go unnoticed. Always link to the original source.

[http://ubuntuforums.org/showthread.php?t=1130384](http://ubuntuforums.org/showthread.php?t=1130384)

---

### Post by fballem on 2009-07-22
> **psyke83 said:**
> Please don't link to a site that plagiarizes posts from this forum - the copied posts are often outdated and off-site comments go unnoticed. Always link to the original source.

[http://ubuntuforums.org/showthread.php?t=1130384](http://ubuntuforums.org/showthread.php?t=1130384)

I appreciate the reference to the original post. The link that I provided was the link that I actually used, If it solved the original poster's problem, which it appears it did not, then that was the point.

Your suggestion, and the comments about outdated, were useful, and I thank you for them.

Regards,

---

### Post by psyke83 on 2009-07-22
> **fballem said:**
> I appreciate the reference to the original post. The link that I provided was the link that I actually used, If it solved the original poster's problem, which it appears it did not, then that was the point.

Your suggestion, and the comments about outdated, were useful, and I thank you for them.

Regards,

Yes, that's true. You read an older revision of markbuntu's post from that site, which had the potential for incomplete or incorrect information, unfortunately.

---

### Post by psyke83 on 2009-07-22
> **a_posse_ad_esse said:**
> This seems to be a common problem, but none of the solutions (a comprehensive list of what has been done can be found [here]("http://www.ubuntugeek.com/simple-guide-to-sound-solutions-for-hardyintrepid-and-jaunty-jackalope-users.html")) have helped.  

What puzzles me is that the sound worked out-of-the-box before, even while running Jaunty. I combined two of my systems into the current setup by moving the current motherboard into a new case, added peripherals, and reinstalled.  The wiring is correct as everything works except for the sound.  I added a pci soundcard to the setup and made it default with asoundconf, and have been met with the same silence.  The modules are loaded.

I'm sorry for the lengthy output, but this is the only thing that I've found that may be helpful.

Note: asoundconf does not work as expected on a system configured to use PulseAudio. You must set the default sound card through PulseAudio's configuration.

To do this, you can install the pavucontrol application or edit your configuration file manually. If the other links haven't helped, I recommend you look at my PulseAudio guide, and pay attention to Part A, Step 5.

---

### Post by a_posse_ad_esse on 2009-07-22
Thank you for the responses.

I used the link that I gave above as it gave a comprehensive list of the steps that I had taken in the interest of time.  I know that I would much rather look at a single and combined source rather than sifting through user comments when trying to solve a problem.  The author also cited the sources, so I felt comfortable using it as credit was given to those due.  I guess it was more 'this is what I have done' rather than a guide for others to follow as it didn't work...  Hopefully they will find that here!

That is interesting about asoundconf.  I set the default card in the pulseaudio applet, and the settings survived the log out/in, but still no dice.  I may be missing something obvious here as I've always used ALSA.  What prompted the switch?

---

### Post by a_posse_ad_esse on 2009-07-24
Sorry, but *bump.*

---

### Post by markbuntu on 2009-07-25
Try this here. It explains what is going on when using multiple sound cards and what to do about it. It is fairly old but still relevant.


[http://ubuntuforums.org/showthread.php?t=922860](http://ubuntuforums.org/showthread.php?t=922860)

---

### Post by a_posse_ad_esse on 2009-07-25
Thank you all for your help with this problem.  It turns out that the sound was not working for either card because the front audio *must* be hooked up for the sound to work at all.  Never would have guessed...

---

### Post by venkat_coolcat on 2009-08-24
Hi all,

Am new to ubuntu platform.
I was getting sound in my PC (ubuntu 8.04) before like startup sound,mp3 file etc;

But not when watching a movie using 
So i made some change in preferences--->Sound.
But unfortunately am unable to hear any sound now even the startup sound 

As i didn't make note of the initial sound setup am unable to retrieve back.

Can anyone please help me.

Thanks
Venkat

---

### Post by markbuntu on 2009-08-24
Here is a little guide for setting up your sound in Hardy Heron 8.04 and Intrepid 8.10

[http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506)

---

