---
title: "Compaq C300 - No sound under Jaunty"
date: 2009-08-03
forum: Multimedia Software
---

### Post by dawynn on 2009-08-03
Hoping someone can help.

I followed this guide:
[http://ubuntuforums.org/showthread.php?t=789578&referrerid=703](http://ubuntuforums.org/showthread.php?t=789578&referrerid=703)
(Why is the PulseAudio guide hidden under "Other discussions", while an older Alsa-only guide is sticky'ed under multimedia?)

I still have no sound.  This is on a Compaq C300 laptop.  I'm running a cross between Linux Mint and Edubuntu -- primarily focused on the Xfce desktop from Xfce mint, although I also can log into a gnome session.  System was migrated from Hardy through Intrepid up to Jaunty.

Output from "aplay -l":
```
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: CONEXANT Analog [CONEXANT Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: Conexant Digital [Conexant Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

Output of "pkill pulseaudio; sleep 2; pulseaudio -vv":
```
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
D: main.c: Running on host: Linux i686 2.6.28-14-generic #47-Ubuntu SMP Sat Jul 25 00:28:35 UTC 2009
I: main.c: Page size is 4096 bytes
D: main.c: Compiled with Valgrind support: no
D: main.c: Running in valgrind mode: no
D: main.c: Optimized build: yes
I: main.c: Machine ID is 26488061d7a163866298020046345cbd.
I: main.c: Using runtime directory /home/dawynn/.pulse/26488061d7a163866298020046345cbd:runtime.
I: main.c: Using state directory /home/dawynn/.pulse.
I: main.c: Running in system mode: no
I: main.c: Fresh high-resolution timers available! Bon appetit!
D: memblock.c: Using shared memory pool with 1024 slots of size 64.0 KiB each, total size is 64.0 MiB, maximum usable slot size is 65496
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9/modules/module-gconf.so': success
I: module.c: Loaded "module-gconf" (index: #0; argument: "").
I: module.c: Loaded "module-suspend-on-idle" (index: #1; argument: "").
I: module-device-restore.c: Sucessfully opened database file '/home/dawynn/.pulse/26488061d7a163866298020046345cbd:device-volumes.i486-pc-linux-gnu.gdbm'.
I: module.c: Loaded "module-device-restore" (index: #2; argument: "").
I: module-stream-restore.c: Sucessfully opened database file '/home/dawynn/.pulse/26488061d7a163866298020046345cbd:stream-volumes.i486-pc-linux-gnu.gdbm'.
I: module.c: Loaded "module-stream-restore" (index: #3; argument: "").
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9/modules/module-hal-detect.so': success
I: module-hal-detect.c: Trying capability alsa
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/computer_alsa_timer
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/computer_alsa_sequencer
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_8086_27d8_sound_card_0_alsa_playback_1
D: module-hal-detect.c: Loading module-alsa-sink with arguments 'device_id=0 sink_name=alsa_output.pci_8086_27d8_sound_card_0_alsa_playback_0 tsched=0'
D: alsa-util.c: Trying front:0 with SND_PCM_NO_AUTO_FORMAT ...
W: alsa-util.c: Device front:0 doesn't support 44100 Hz, changed to 48000 Hz.
I: module-alsa-sink.c: Successfully opened device front:0.
I: module-alsa-sink.c: Successfully enabled mmap() mode.
I: (alsa-lib)control.c: Invalid CTL front:0
I: alsa-util.c: Unable to attach to mixer front:0: No such file or directory
I: alsa-util.c: Successfully attached to mixer 'hw:0'
I: alsa-util.c: Using mixer control "Master".
I: sink.c: Created sink 0 "alsa_output.pci_8086_27d8_sound_card_0_alsa_playback_0" with sample spec s16le 2ch 48000Hz and channel map front-left,front-right
I: source.c: Created source 0 "alsa_output.pci_8086_27d8_sound_card_0_alsa_playback_0.monitor" with sample spec s16le 2ch 48000Hz and channel map front-left,front-right
I: module-alsa-sink.c: Using 8 fragments of size 1920 bytes, buffer time is 80.00ms
D: module-alsa-sink.c: hwbuf_unused=0
D: module-alsa-sink.c: setting avail_min=1
I: module-alsa-sink.c: Volume ranges from 0 to 30.
I: module-alsa-sink.c: Volume ranges from -46.50 dB to -1.50 dB.
I: alsa-util.c: All 2 channels can be mapped to mixer channels.
I: module-alsa-sink.c: Using hardware volume control. Hardware dB scale supported.
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
D: alsa-util.c: Slave: Hardware PCM card 0 'HDA Intel' device 0 subdevice 0
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
D: alsa-util.c:   start_thre
D: module-alsa-sink.c: Thread starting up
D: rtpoll.c: Acquired POSIX realtime signal SIGRTMIN+29
D: module-alsa-sink.c: Read hardware volume: 0: 100% 1: 100%
I: module-alsa-sink.c: Starting playback.
D: module-suspend-on-idle.c: Source alsa_output.pci_8086_27d8_sound_card_0_alsa_playback_0.monitor becomes idle.
D: module-suspend-on-idle.c: Sink alsa_output.pci_8086_27d8_sound_card_0_alsa_playback_0 becomes idle.
I: module.c: Loaded "module-alsa-sink" (index: #4; argument: "device_id=0 sink_name=alsa_output.pci_8086_27d8_sound_card_0_alsa_playback_0 tsched=0").
D: module-hal-detect.c: Loading module-alsa-source with arguments 'device_id=0 source_name=alsa_input.pci_8086_27d8_sound_card_0_alsa_capture_0 tsched=0'
D: alsa-util.c: Trying front:0 with SND_PCM_NO_AUTO_FORMAT ...
W: alsa-util.c: Device front:0 doesn't support 44100 Hz, changed to 48000 Hz.
I: module-alsa-source.c: Successfully opened device front:0.
I: module-alsa-source.c: Successfully enabled mmap() mode.
I: (alsa-lib)control.c: Invalid CTL front:0
I: alsa-util.c: Unable to attach to mixer front:0: No such file or directory
I: alsa-util.c: Successfully attached to mixer 'hw:0'
I: alsa-util.c: Using mixer control "Capture".
I: source.c: Created source 1 "alsa_input.pci_8086_27d8_sound_card_0_alsa_capture_0" with sample spec s16le 2ch 48000Hz and channel map front-left,front-right
I: module-alsa-source.c: Using 8 fragments of size 1920 bytes, buffer time is 80.00ms
D: module-alsa-source.c: hwbuf_unused=0
D: module-alsa-source.c: setting avail_min=1
I: module-alsa-source.c: Volume ranges from 0 to 14.
I: module-alsa-source.c: Volume ranges from 0.00 dB to 21.00 dB.
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
D: alsa-util.c: Slave: Hardware PCM card 0 'HDA Intel' device 0 subdevice 0
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
D: alsa-util.c:   period_size  : 480
D: alsa-util.c:   period_time  : 10000
D: alsa-util.c:   tstamp_mode  : ENABLE
D: alsa-util.c:   period_step  : 1
D: alsa-util.c:   avail_min    : 480
D: alsa-util.c:   period_event : 0
D: alsa-util.c:   start_thresh
D: module-alsa-source.c: Thread starting up
D: rtpoll.c: Acquired POSIX realtime signal SIGRTMIN+28
D: module-alsa-source.c: Read hardware volume: 0:  64% 1:  64%
D: module-suspend-on-idle.c: Source alsa_input.pci_8086_27d8_sound_card_0_alsa_capture_0 becomes idle.
I: module.c: Loaded "module-alsa-source" (index: #5; argument: "device_id=0 source_name=alsa_input.pci_8086_27d8_sound_card_0_alsa_capture_0 tsched=0").
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_8086_27d8_sound_card_0_alsa_control__1
I: module-hal-detect.c: Loaded 2 modules.
I: module.c: Loaded "module-hal-detect" (index: #6; argument: "tsched=0").
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9/modules/module-esound-protocol-unix.so': success
I: module.c: Loaded "module-esound-protocol-unix" (index: #7; argument: "").
I: module.c: Loaded "module-native-protocol-unix" (index: #8; argument: "").
I: module.c: Loaded "module-default-device-restore" (index: #9; argument: "").
I: module.c: Loaded "module-rescue-streams" (index: #10; argument: "").
I: module.c: Loaded "module-always-sink" (index: #11; argument: "").
I: client.c: Created 0 "ConsoleKit Session /org/freedesktop/ConsoleKit/Session3"
D: module-console-kit.c: Added new session /org/freedesktop/ConsoleKit/Session3
I: module.c: Loaded "module-console-kit" (index: #12; argument: "").
I: module.c: Loaded "module-position-event-sounds" (index: #13; argument: "").
I: main.c: Daemon startup complete.
D: module-hal-detect.c: dbus: interface=org.freedesktop.DBus, path=/org/freedesktop/DBus, member=NameAcquired
D: module-console-kit.c: dbus: interface=org.freedesktop.DBus, path=/org/freedesktop/DBus, member=NameAcquired
I: module-device-restore.c: Storing volume/mute for device source:alsa_output.pci_8086_27d8_sound_card_0_alsa_playback_0.monitor.
I: module-device-restore.c: Storing volume/mute for device sink:alsa_output.pci_8086_27d8_sound_card_0_alsa_playback_0.
I: module-device-restore.c: Storing volume/mute for device source:alsa_input.pci_8086_27d8_sound_card_0_alsa_capture_0.
I: module-suspend-on-idle.c: Sink alsa_output.pci_8086_27d8_sound_card_0_alsa_playback_0 idle for too long, suspending ...
I: module-alsa-sink.c: Device suspended...
I: module-suspend-on-idle.c: Source alsa_output.pci_8086_27d8_sound_card_0_alsa_playback_0.monitor idle for too long, suspending ...
I: module-suspend-on-idle.c: Source alsa_input.pci_8086_27d8_sound_card_0_alsa_capture_0 idle for too long, suspending ...
I: module-alsa-source.c: Device suspended...
I: module-device-restore.c: Synced.
D: module-hal-detect.c: dbus: interface=org.freedesktop.ConsoleKit.Seat, path=/org/freedesktop/ConsoleKit/Seat1, member=SessionAdded
D: module-console-kit.c: dbus: interface=org.freedesktop.ConsoleKit.Seat, path=/org/freedesktop/ConsoleKit/Seat1, member=SessionAdded
D: module-hal-detect.c: dbus: interface=org.freedesktop.ConsoleKit.Seat, path=/org/freedesktop/ConsoleKit/Seat1, member=SessionAdded
D: module-console-kit.c: dbus: interface=org.freedesktop.ConsoleKit.Seat, path=/org/freedesktop/ConsoleKit/Seat1, member=SessionAdded
D: module-hal-detect.c: dbus: interface=org.freedesktop.ConsoleKit.Seat, path=/org/freedesktop/ConsoleKit/Seat1, member=SessionRemoved
D: module-console-kit.c: dbus: interface=org.freedesktop.ConsoleKit.Seat, path=/org/freedesktop/ConsoleKit/Seat1, member=SessionRemoved
D: module-hal-detect.c: dbus: interface=org.freedesktop.ConsoleKit.Seat, path=/org/freedesktop/ConsoleKit/Seat1, member=SessionRemoved
D: module-console-kit.c: dbus: interface=org.freedesktop.ConsoleKit.Seat, path=/org/freedesktop/ConsoleKit/Seat1, member=SessionRemoved
D: module-hal-detect.c: dbus: interface=org.freedesktop.ConsoleKit.Seat, path=/org/freedesktop/ConsoleKit/Seat1, member=SessionAdded
D: module-console-kit.c: dbus: interface=org.freedesktop.ConsoleKit.Seat, path=/org/freedesktop/ConsoleKit/Seat1, member=SessionAdded
D: module-hal-detect.c: dbus: interface=org.freedesktop.ConsoleKit.Seat, path=/org/freedesktop/ConsoleKit/Seat1, member=SessionRemoved
D: module-console-kit.c: dbus: interface=org.freedesktop.ConsoleKit.Seat, path=/org/freedesktop/ConsoleKit/Seat1, member=SessionRemoved
^CI: main.c: Got signal SIGINT.
I: main.c: Exiting.
I: main.c: Daemon shutdown initiated.
I: module.c: Unloading "module-gconf" (index: #0).
I: module.c: Unloaded "module-gconf" (index: #0).
I: module.c: Unloading "module-suspend-on-idle" (index: #1).
I: module.c: Unloaded "module-suspend-on-idle" (index: #1).
I: module.c: Unloading "module-device-restore" (index: #2).
I: module.c: Unloaded "module-device-restore" (index: #2).
I: module.c: Unloading "module-stream-restore" (index: #3).
I: module.c: Unloaded "module-stream-restore" (index: #3).
I: module.c: Unloading "module-alsa-sink" (index: #4).
D: module-always-sink.c: Autoloading null-sink as no other sinks detected.
I: sink.c: Created sink 1 "auto_null" with sample spec s16le 2ch 44100Hz and channel map front-left,front-right
I: source.c: Created source 2 "auto_null.monitor" with sample spec s16le 2ch 44100Hz and channel map front-left,front-right
D: module-null-sink.c: Thread starting up
D: rtpoll.c: Acquired POSIX realtime signal SIGRTMIN+27
I: module.c: Loaded "module-null-sink" (index: #14; argument: "sink_name=auto_null").
D: module-rescue-streams.c: No sink inputs to move away.
D: module-rescue-streams.c: No source outputs to move away.
D: module-alsa-sink.c: Thread shutting down
I: sink.c: Freeing sink 0 "alsa_output.pci_8086_27d8_sound_card_0_alsa_playback_0"
I: source.c: Freeing source 0 "alsa_output.pci_8086_27d8_sound_card_0_alsa_playback_0.monitor"
I: module.c: Unloaded "module-alsa-sink" (index: #4).
I: module.c: Unloading "module-alsa-source" (index: #5).
D: module-rescue-streams.c: No source outputs to move away.
D: module-alsa-source.c: Thread shutting down
I: source.c: Freeing source 1 "alsa_input.pci_8086_27d8_sound_card_0_alsa_capture_0"
I: module.c: Unloaded "module-alsa-source" (index: #5).
I: module.c: Unloading "module-hal-detect" (index: #6).
I: module.c: Unloaded "module-hal-detect" (index: #6).
I: module.c: Unloading "module-esound-protocol-unix" (index: #7).
I: module.c: Unloaded "module-esound-protocol-unix" (index: #7).
I: module.c: Unloading "module-native-protocol-unix" (index: #8).
I: module.c: Unloaded "module-native-protocol-unix" (index: #8).
I: module.c: Unloading "module-default-device-restore" (index: #9).
I: module.c: Unloaded "module-default-device-restore" (index: #9).
I: module.c: Unloading "module-rescue-streams" (index: #10).
I: module.c: Unloaded "module-rescue-streams" (index: #10).
I: module.c: Unloading "module-always-sink" (index: #11).
I: module.c: Unloaded "module-always-sink" (index: #11).
I: module.c: Unloading "module-console-kit" (index: #12).
D: module-console-kit.c: Removing session /org/freedesktop/ConsoleKit/Session3
I: client.c: Freed 0 "ConsoleKit Session /org/freedesktop/ConsoleKit/Session3"
I: module.c: Unloaded "module-console-kit" (index: #12).
I: module.c: Unloading "module-position-event-sounds" (index: #13).
I: module.c: Unloaded "module-position-event-sounds" (index: #13).
I: module.c: Unloading "module-null-sink" (index: #14).
D: core-subscribe.c: Dropped redundant event due to remove event.
D: core-subscribe.c: Dropped redundant event due to remove event.
D: module-null-sink.c: Thread shutting down
I: sink.c: Freeing sink 1 "auto_null"
I: source.c: Freeing source 2 "auto_null.monitor"
I: module.c: Unloaded "module-null-sink" (index: #14).
D: core-subscribe.c: Dropped redundant event due to remove event.
I: main.c: Daemon terminated.

```

I would greatly appreciate help from anyone that can decipher this information.

---

### Post by dawynn on 2009-08-04
Problem solved.  I had a card much like the one diagnosed here.
[http://ubuntuforums.org/showthread.php?t=806620](http://ubuntuforums.org/showthread.php?t=806620)

---

