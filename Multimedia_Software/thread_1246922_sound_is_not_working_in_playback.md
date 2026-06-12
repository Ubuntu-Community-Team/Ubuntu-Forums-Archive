---
title: "sound is not working in playback"
date: 2009-08-22
forum: Multimedia Software
---

### Post by avinashc on 2009-08-22
I installed ubuntu 9.0.14 at the startup my laptop gives very noisy type of sound but whenever i try to play any media file. It doesnt playing any sound though video is working
I run this command pulseaudio -vvv and get following outpu
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
D: main.c: Started as real root: no, suid root: yes
I: main.c: PolicyKit refuses acquire-high-priority privilege.
N: main.c: Called SUID root and real-time and/or high-priority scheduling was requested in the configuration. However, we lack the necessary privileges:
N: main.c: We are not in group 'pulse-rt', PolicyKit refuse to grant us the requested privileges and we have no increase RLIMIT_NICE/RLIMIT_RTPRIO resource limits.
N: main.c: For enabling real-time/high-priority scheduling please acquire the appropriate PolicyKit privileges, or become a member of 'pulse-rt', or increase the RLIMIT_NICE/RLIMIT_RTPRIO resource limits for this user.
I: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
I: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
D: main.c: Can realtime: no, can high-priority: no
D: main.c: Can realtime: no, can high-priority: no
I: main.c: This is PulseAudio 0.9.14
D: main.c: Compilation host: i486-pc-linux-gnu
D: main.c: Compilation CFLAGS: -g -O2 -g -Wall -O3 -Wall -W -Wextra -pedantic -pipe -Wno-long-long -Wvla -Wno-overlength-strings -Wconversion -Wundef -Wformat -Wlogical-op -Wpacked -Wformat-security -Wmissing-include-dirs -Wformat-nonliteral -Wold-style-definition -Wdeclaration-after-statement -Wfloat-equal -Wmissing-declarations -Wmissing-prototypes -Wstrict-prototypes -Wredundant-decls -Wmissing-noreturn -Wshadow -Wendif-labels -Wpointer-arith -Wcast-align -Wwrite-strings -Wno-unused-parameter -ffast-math
D: main.c: Running on host: Linux i686 2.6.28-15-generic #49-Ubuntu SMP Tue Aug 18 18:40:08 UTC 2009
I: main.c: Page size is 4096 bytes
D: main.c: Compiled with Valgrind support: no
D: main.c: Running in valgrind mode: no
D: main.c: Optimized build: yes
I: main.c: Machine ID is d996d9d70663d36313c921564a8fdeb6.
I: main.c: Using runtime directory /home/avinashc/.pulse/d996d9d70663d36313c921564a8fdeb6:runtime.
I: main.c: Using state directory /home/avinashc/.pulse.
I: main.c: Running in system mode: no
I: main.c: Fresh high-resolution timers available! Bon appetit!
D: memblock.c: Using shared memory pool with 1024 slots of size 64.0 KiB each, total size is 64.0 MiB, maximum usable slot size is 65496
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9/modules/module-gconf.so': success
I: module.c: Loaded "module-gconf" (index: #0; argument: "").
I: module.c: Loaded "module-suspend-on-idle" (index: #1; argument: "").
I: module-device-restore.c: Sucessfully opened database file '/home/avinashc/.pulse/d996d9d70663d36313c921564a8fdeb6:device-volumes.i486-pc-linux-gnu.gdbm'.
I: module.c: Loaded "module-device-restore" (index: #2; argument: "").
I: module-stream-restore.c: Sucessfully opened database file '/home/avinashc/.pulse/d996d9d70663d36313c921564a8fdeb6:stream-volumes.i486-pc-linux-gnu.gdbm'.
I: module.c: Loaded "module-stream-restore" (index: #3; argument: "").
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9/modules/module-hal-detect.so': success
I: module-hal-detect.c: Trying capability alsa
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/computer_alsa_timer
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/computer_alsa_sequencer
D: module-hal-detect.c: Loading module-alsa-sink with arguments 'device_id=0 sink_name=alsa_output.pci_8086_293e_sound_card_0_alsa_playback_0 tsched=0'
D: alsa-util.c: Trying front:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC0D0p failed
I: alsa-util.c: Couldn't open PCM device front:0: Device or resource busy
D: alsa-util.c: Trying surround40:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC0D0p failed
I: alsa-util.c: Couldn't open PCM device surround40:0: Device or resource busy
D: alsa-util.c: Trying surround41:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC0D0p failed
I: alsa-util.c: Couldn't open PCM device surround41:0: Device or resource busy
D: alsa-util.c: Trying surround50:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC0D0p failed
I: alsa-util.c: Couldn't open PCM device surround50:0: Device or resource busy
D: alsa-util.c: Trying surround51:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC0D0p failed
I: alsa-util.c: Couldn't open PCM device surround51:0: Device or resource busy
D: alsa-util.c: Trying surround71:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC0D0p failed
I: alsa-util.c: Couldn't open PCM device surround71:0: Device or resource busy
D: alsa-util.c: Trying hw:0 as last resort...
D: alsa-util.c: Trying hw:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm_hw.c: open /dev/snd/pcmC0D0p failed
[COLOR=Red]E: alsa-util.c: Error opening PCM device hw:0: Device or resource busy
E: module.c: Failed to load  module "module-alsa-sink" (argument: "device_id=0 sink_name=alsa_output.pci_8086_293e_sound_card_0_alsa_playback_0 tsched=0"): initialization failed[/COLOR].
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_8086_293e_sound_card_0_alsa_playback_0
D: module-hal-detect.c: Loading module-alsa-source with arguments 'device_id=0 source_name=alsa_input.pci_8086_293e_sound_card_0_alsa_capture_0 tsched=0'
D: alsa-util.c: Trying front:0 with SND_PCM_NO_AUTO_FORMAT ...
I: module-alsa-source.c: Successfully opened device front:0.
I: module-alsa-source.c: Successfully enabled mmap() mode.
I: (alsa-lib)control.c: Invalid CTL front:0
I: alsa-util.c: Unable to attach to mixer front:0: No such file or directory
I: alsa-util.c: Successfully attached to mixer 'hw:0'
I: alsa-util.c: Using mixer control "Capture".
I: module-device-restore.c: Restoring volume for source alsa_input.pci_8086_293e_sound_card_0_alsa_capture_0.
I: module-device-restore.c: Restoring mute state for source alsa_input.pci_8086_293e_sound_card_0_alsa_capture_0.
I: source.c: Created source 0 "alsa_input.pci_8086_293e_sound_card_0_alsa_capture_0" with sample spec s16le 2ch 44100Hz and channel map front-left,front-right
I: module-alsa-source.c: Using 8 fragments of size 1792 bytes, buffer time is 81.27ms
D: module-alsa-source.c: hwbuf_unused=0
D: module-alsa-source.c: setting avail_min=1
I: module-alsa-source.c: Volume ranges from 0 to 15.
I: module-alsa-source.c: Volume ranges from 0.00 dB to 22.50 dB.
I: alsa-util.c: All 2 channels can be mapped to mixer channels.
I: module-alsa-source.c: Using hardware volume control. Hardware dB scale supported.
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
D: alsa-util.c:   buffer_size  : 3584
D: alsa-util.c:   period_size  : 448
D: alsa-util.c:   period_time  : 10158
D: alsa-util.c:   tstamp_mode  : ENABLE
D: alsa-util.c:   period_step  : 1
D: alsa-util.c:   avail_min    : 448
D: alsa-util.c:   period_event : 0
D: alsa-util.c:   start_threshold  : -1
D: alsa-util.c:   stop_threshold   : 1879048192
D: alsa-util.c:   silence_threshold: 0
D: alsa-util.c:   silence_size : 0
D: alsa-util.c:   boundary     : 1879048192
D: alsa-util.c: Slave: Hardware PCM card 0 'HDA Intel' device 0 subdevice 0
D: alsa-util.c: Its setup is:
D: alsa-util.c:   stream       : CAPTURE
D: alsa-util.c:   access       : MMAP_INTERLEAVED
D: alsa-util.c:   format       : S16_LE
D: alsa-util.c:   subformat    : STD
D: alsa-util.c:   channels     : 2
D: alsa-util.c:   rate         : 44100
D: alsa-util.c:   exact rate   : 44100 (44100/1)
D: alsa-util.c:   msbits       : 16
D: alsa-util.c:   buffer_size  : 3584
D: alsa-util.c:   period_size  : 448
D: alsa-util.c:   period_time  : 10158
D: alsa-util.c:   tstamp_mode  : ENABLE
D: alsa-util.c:   period_step  : 1
D: alsa-util.c:   avail_min    : 448
D: alsa-util.c:   period_event : 0
D: alsa-util.c:   start_thresh
D: module-alsa-source.c: Thread starting up
D: rtpoll.c: Acquired POSIX realtime signal SIGRTMIN+29
D: module-alsa-source.c: Requested volume: 0:  62% 1:  62%
D: module-alsa-source.c: Got hardware volume: 0:  62% 1:  62%
D: module-alsa-source.c: Calculated software volume: 0: 100% 1: 100%
D: module-suspend-on-idle.c: Source alsa_input.pci_8086_293e_sound_card_0_alsa_capture_0 becomes idle.
I: module.c: Loaded "module-alsa-source" (index: #4; argument: "device_id=0 source_name=alsa_input.pci_8086_293e_sound_card_0_alsa_capture_0 tsched=0").
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_8086_293e_sound_card_0_alsa_control__1
I: module-hal-detect.c: Loaded 1 modules.
I: module.c: Loaded "module-hal-detect" (index: #5; argument: "tsched=0").
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9/modules/module-esound-protocol-unix.so': success
I: module.c: Loaded "module-esound-protocol-unix" (index: #6; argument: "").
I: module.c: Loaded "module-native-protocol-unix" (index: #7; argument: "").
I: module-default-device-restore.c: Saved default sink 'auto_null' not existant, not restoring default sink setting.
I: module-default-device-restore.c: Restored default source 'alsa_input.pci_8086_293e_sound_card_0_alsa_capture_0'.
I: module.c: Loaded "module-default-device-restore" (index: #8; argument: "").
I: module.c: Loaded "module-rescue-streams" (index: #9; argument: "").
D: module-always-sink.c: Autoloading null-sink as no other sinks detected.
I: module-device-restore.c: Restoring volume for sink auto_null.
I: module-device-restore.c: Restoring mute state for sink auto_null.
I: sink.c: Created sink 0 "auto_null" with sample spec s16le 2ch 44100Hz and channel map front-left,front-right
I: module-device-restore.c: Restoring volume for source auto_null.monitor.
I: module-device-restore.c: Restoring mute state for source auto_null.monitor.
I: source.c: Created source 1 "auto_null.monitor" with sample spec s16le 2ch 44100Hz and channel map front-left,front-right
D: module-null-sink.c: Thread starting up
D: rtpoll.c: Acquired POSIX realtime signal SIGRTMIN+28
D: module-suspend-on-idle.c: Source auto_null.monitor becomes idle.
D: module-suspend-on-idle.c: Sink auto_null becomes idle.
I: module.c: Loaded "module-null-sink" (index: #10; argument: "sink_name=auto_null").
I: module.c: Loaded "module-always-sink" (index: #11; argument: "").
I: client.c: Created 0 "ConsoleKit Session /org/freedesktop/ConsoleKit/Session9"
D: module-console-kit.c: Added new session /org/freedesktop/ConsoleKit/Session9
I: module.c: Loaded "module-console-kit" (index: #12; argument: "").
I: module.c: Loaded "module-position-event-sounds" (index: #13; argument: "").
I: main.c: Daemon startup complete.
D: module-hal-detect.c: dbus: interface=org.freedesktop.DBus, path=/org/freedesktop/DBus, member=NameAcquired
D: module-console-kit.c: dbus: interface=org.freedesktop.DBus, path=/org/freedesktop/DBus, member=NameAcquired
I: module-suspend-on-idle.c: Source alsa_input.pci_8086_293e_sound_card_0_alsa_capture_0 idle for too long, suspending ...
I: module-alsa-source.c: Device suspended...
I: module-suspend-on-idle.c: Source auto_null.monitor idle for too long, suspending ...
I: module-suspend-on-idle.c: Sink auto_null idle for too long, suspending ...
D: module-hal-detect.c: dbus: interface=org.freedesktop.Hal.Device, path=/org/freedesktop/Hal/devices/computer_power_supply_battery_BAT0, member=PropertyModified
D: module-console-kit.c: dbus: interface=org.freedesktop.Hal.Device, path=/org/freedesktop/Hal/devices/computer_power_supply_battery_BAT0, member=PropertyModified

please tell me how to play sound for media files.

---

