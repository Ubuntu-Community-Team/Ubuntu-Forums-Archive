---
title: "Audio Not Working After Boot ubuntu 12.10"
date: 2013-01-23
forum: Multimedia Software
---

### Post by Simeo on 2013-01-23
Ok, I know it's been hashed over and over but.... I did all the searched. Checked google. Ran through a few troubleshooting but still nothing.

I'm not getting any audio now and I was before. I have a dual boot aspire timeline laptop. I usually boot into ubuntu 12.10 but I needed to get into Win7 to run my Maxtor Blackarmor Harddrive.

Now I'm back in Ubuntu and have no sound. I've run several tests, checked alsamixer, etc. Nothing is muted. What outputs do y'all need to help?

Edit: Just logged out of Ubuntu, to Win7 and audio works in Win7, then back to Ubuntu and no audio.

---

### Post by Yellow Pasque on 2013-01-23
Alsa info's often helpful: [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)
Pulseaudio log can help too: [https://wiki.ubuntu.com/PulseAudio/Log](https://wiki.ubuntu.com/PulseAudio/Log)

---

### Post by Simeo on 2013-01-25
> **Temüjin said:**
> Alsa info's often helpful: [https://wiki.ubuntu.com/Audio/AlsaInfo](https://wiki.ubuntu.com/Audio/AlsaInfo)
Pulseaudio log can help too: [https://wiki.ubuntu.com/PulseAudio/Log](https://wiki.ubuntu.com/PulseAudio/Log)

Thank you and sorry for the delay. My audio started working but it's odd... First, after about 3-4 reboots my audio started working fine. Now my audio is working... but the volume control is unavailable... but audio is coming out my headphone jack. If I unplug headphone jack no audio is heard or controllable. 

The output to your comment is below:

--------

~$ /usr/share/alsa-base/alsa-info.sh
ALSA Information Script v 0.4.60
--------------------------------

This script visits the following commands/files to collect diagnostic
information about your ALSA installation and sound related hardware.

  dmesg
  lspci
  lsmod
  aplay
  amixer
  alsactl
  /proc/asound/
  /sys/class/sound/
  ~/.asoundrc (etc.)

See '/usr/share/alsa-base/alsa-info.sh --help' for command line options.

Newer version detected: 0.4.61
To view the ChangeLog, please visit [http://www.alsa-project.org/alsa-info.sh.changelog](http://www.alsa-project.org/alsa-info.sh.changelog)
ALSA-Info script has been downloaded /tmp/alsa-info.1YYGuA7Y7T.
Please, re-run it from new location.

---

Pulseverbose.log

```
(   0.000|   0.000) I: [pulseaudio] main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
(   0.000|   0.000) I: [pulseaudio] main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
(   0.000|   0.000) D: [pulseaudio] core-rtclock.c: Timer slack is set to 50 us.
(   0.003|   0.003) D: [pulseaudio] core-util.c: RealtimeKit worked.
(   0.003|   0.000) I: [pulseaudio] core-util.c: Successfully gained nice level -11.
(   0.003|   0.000) I: [pulseaudio] main.c: This is PulseAudio 2.1
(   0.003|   0.000) D: [pulseaudio] main.c: Compilation host: x86_64-pc-linux-gnu
(   0.004|   0.000) D: [pulseaudio] main.c: Compilation CFLAGS: -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Werror=format-security -Wall -W -Wextra -pipe -Wno-long-long -Wvla -Wno-overlength-strings -Wunsafe-loop-optimizations -Wundef -Wformat=2 -Wlogical-op -Wsign-compare -Wformat-security -Wmissing-include-dirs -Wformat-nonliteral -Wpointer-arith -Winit-self -Wdeclaration-after-statement -Wfloat-equal -Wmissing-prototypes -Wredundant-decls -Wmissing-declarations -Wmissing-noreturn -Wshadow -Wendif-labels -Wcast-align -Wstrict-aliasing -Wwrite-strings -Wno-unused-parameter -ffast-math -Wp,-D_FORTIFY_SOURCE=2 -fno-common -fdiagnostics-show-option
(   0.004|   0.000) D: [pulseaudio] main.c: Running on host: Linux x86_64 3.5.0-22-generic #34-Ubuntu SMP Tue Jan 8 21:47:00 UTC 2013
(   0.004|   0.000) D: [pulseaudio] main.c: Found 4 CPUs.
(   0.004|   0.000) I: [pulseaudio] main.c: Page size is 4096 bytes
(   0.004|   0.000) D: [pulseaudio] main.c: Compiled with Valgrind support: no
(   0.004|   0.000) D: [pulseaudio] main.c: Running in valgrind mode: no
(   0.004|   0.000) D: [pulseaudio] main.c: Running in VM: no
(   0.004|   0.000) D: [pulseaudio] main.c: Optimized build: yes
(   0.004|   0.000) D: [pulseaudio] main.c: FASTPATH defined, only fast path asserts disabled.
(   0.004|   0.000) I: [pulseaudio] main.c: Machine ID is 68208ada37ae139fa75f636350ef60fd.
(   0.004|   0.000) I: [pulseaudio] main.c: Session ID is 68208ada37ae139fa75f636350ef60fd-1359125603.643389-1430610501.
(   0.004|   0.000) I: [pulseaudio] main.c: Using runtime directory /home/joshua/.pulse/68208ada37ae139fa75f636350ef60fd-runtime.
(   0.004|   0.000) I: [pulseaudio] main.c: Using state directory /home/joshua/.pulse.
(   0.004|   0.000) I: [pulseaudio] main.c: Using modules directory /usr/lib/pulse-2.1/modules.
(   0.004|   0.000) I: [pulseaudio] main.c: Running in system mode: no
(   0.004|   0.000) I: [pulseaudio] main.c: Fresh high-resolution timers available! Bon appetit!
(   0.004|   0.000) D: [pulseaudio] memblock.c: Using shared memory pool with 1024 slots of size 64.0 KiB each, total size is 64.0 MiB, maximum usable slot size is 65472
(   0.004|   0.000) I: [pulseaudio] cpu-x86.c: CPU flags: CMOV MMX SSE SSE2 SSE3 SSSE3 SSE4_1 SSE4_2 
(   0.004|   0.000) I: [pulseaudio] svolume_mmx.c: Initialising MMX optimized volume functions.
(   0.004|   0.000) I: [pulseaudio] remap_mmx.c: Initialising MMX optimized remappers.
(   0.004|   0.000) I: [pulseaudio] svolume_sse.c: Initialising SSE2 optimized volume functions.
(   0.004|   0.000) I: [pulseaudio] remap_sse.c: Initialising SSE2 optimized remappers.
(   0.004|   0.000) I: [pulseaudio] sconv_sse.c: Initialising SSE2 optimized conversions.
(   0.004|   0.000) I: [pulseaudio] svolume_orc.c: Initialising ORC optimized volume functions.
(   0.005|   0.000) D: [pulseaudio] database-tdb.c: Opened TDB database '/home/joshua/.pulse/68208ada37ae139fa75f636350ef60fd-device-volumes.tdb'
(   0.005|   0.000) I: [pulseaudio] module-device-restore.c: Successfully opened database file '/home/joshua/.pulse/68208ada37ae139fa75f636350ef60fd-device-volumes'.
(   0.005|   0.000) I: [pulseaudio] module.c: Loaded "module-device-restore" (index: #0; argument: "").
(   0.005|   0.000) D: [pulseaudio] database-tdb.c: Opened TDB database '/home/joshua/.pulse/68208ada37ae139fa75f636350ef60fd-stream-volumes.tdb'
(   0.005|   0.000) I: [pulseaudio] module-stream-restore.c: Successfully opened database file '/home/joshua/.pulse/68208ada37ae139fa75f636350ef60fd-stream-volumes'.
(   0.005|   0.000) D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Ext.StreamRestore1 added for object /org/pulseaudio/stream_restore1
(   0.005|   0.000) D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Ext.StreamRestore1.RestoreEntry added for object /org/pulseaudio/stream_restore1/entry0
(   0.005|   0.000) D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Ext.StreamRestore1.RestoreEntry added for object /org/pulseaudio/stream_restore1/entry1
(   0.005|   0.000) D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Ext.StreamRestore1.RestoreEntry added for object /org/pulseaudio/stream_restore1/entry2
(   0.005|   0.000) D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Ext.StreamRestore1.RestoreEntry added for object /org/pulseaudio/stream_restore1/entry3
(   0.005|   0.000) D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Ext.StreamRestore1.RestoreEntry added for object /org/pulseaudio/stream_restore1/entry4
(   0.005|   0.000) D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Ext.StreamRestore1.RestoreEntry added for object /org/pulseaudio/stream_restore1/entry5
(   0.005|   0.000) D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Ext.StreamRestore1.RestoreEntry added for object /org/pulseaudio/stream_restore1/entry6
(   0.005|   0.000) D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Ext.StreamRestore1.RestoreEntry added for object /org/pulseaudio/stream_restore1/entry7
(   0.005|   0.000) D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Ext.StreamRestore1.RestoreEntry added for object /org/pulseaudio/stream_restore1/entry8
(   0.005|   0.000) D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Ext.StreamRestore1.RestoreEntry added for object /org/pulseaudio/stream_restore1/entry9
(   0.005|   0.000) D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Ext.StreamRestore1.RestoreEntry added for object /org/pulseaudio/stream_restore1/entry10
(   0.005|   0.000) D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Ext.StreamRestore1.RestoreEntry added for object /org/pulseaudio/stream_restore1/entry11
(   0.005|   0.000) D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Ext.StreamRestore1.RestoreEntry added for object /org/pulseaudio/stream_restore1/entry12
(   0.005|   0.000) D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Ext.StreamRestore1.RestoreEntry added for object /org/pulseaudio/stream_restore1/entry13
(   0.005|   0.000) D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Ext.StreamRestore1.RestoreEntry added for object /org/pulseaudio/stream_restore1/entry14
(   0.005|   0.000) D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Ext.StreamRestore1.RestoreEntry added for object /org/pulseaudio/stream_restore1/entry15
(   0.005|   0.000) D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Ext.StreamRestore1.RestoreEntry added for object /org/pulseaudio/stream_restore1/entry16
(   0.005|   0.000) D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Ext.StreamRestore1.RestoreEntry added for object /org/pulseaudio/stream_restore1/entry17
(   0.005|   0.000) I: [pulseaudio] module.c: Loaded "module-stream-restore" (index: #1; argument: "").
(   0.006|   0.000) D: [pulseaudio] database-tdb.c: Opened TDB database '/home/joshua/.pulse/68208ada37ae139fa75f636350ef60fd-card-database.tdb'
(   0.006|   0.000) I: [pulseaudio] module-card-restore.c: Successfully opened database file '/home/joshua/.pulse/68208ada37ae139fa75f636350ef60fd-card-database'.
(   0.006|   0.000) I: [pulseaudio] module.c: Loaded "module-card-restore" (index: #2; argument: "").
(   0.006|   0.000) I: [pulseaudio] module.c: Loaded "module-augment-properties" (index: #3; argument: "").
(   0.006|   0.000) D: [pulseaudio] cli-command.c: Checking for existence of '/usr/lib/pulse-2.1/modules/module-udev-detect.so': success
(   0.007|   0.000) D: [pulseaudio] module-udev-detect.c: /dev/snd/controlC0 is accessible: yes
(   0.007|   0.000) D: [pulseaudio] module-udev-detect.c: /devices/pci0000:00/0000:00:1b.0/sound/card0 is busy: yes
(   0.007|   0.000) I: [pulseaudio] module-udev-detect.c: Found 1 cards.
(   0.007|   0.000) I: [pulseaudio] module.c: Loaded "module-udev-detect" (index: #4; argument: "").
(   0.007|   0.000) D: [pulseaudio] cli-command.c: Checking for existence of '/usr/lib/pulse-2.1/modules/module-jackdbus-detect.so': failure
(   0.007|   0.000) D: [pulseaudio] cli-command.c: Checking for existence of '/usr/lib/pulse-2.1/modules/module-bluetooth-discover.so': success
(   0.008|   0.001) D: [pulseaudio] dbus-util.c: Successfully connected to D-Bus system bus 8942ae8a2e7bae2f1345648f51029c5c as :1.79
(   0.009|   0.000) D: [pulseaudio] bluetooth-util.c: dbus: interface=org.freedesktop.DBus, path=/org/freedesktop/DBus, member=NameAcquired
(   0.009|   0.000) I: [pulseaudio] module.c: Loaded "module-bluetooth-discover" (index: #5; argument: "").
(   0.009|   0.000) D: [pulseaudio] cli-command.c: Checking for existence of '/usr/lib/pulse-2.1/modules/module-esound-protocol-unix.so': failure
(   0.010|   0.000) I: [pulseaudio] module.c: Loaded "module-native-protocol-unix" (index: #6; argument: "").
(   0.010|   0.000) D: [pulseaudio] cli-command.c: Checking for existence of '/usr/lib/pulse-2.1/modules/module-gconf.so': success
(   0.016|   0.006) I: [pulseaudio] module.c: Loaded "module-gconf" (index: #7; argument: "").
(   0.016|   0.000) I: [pulseaudio] module-default-device-restore.c: Saved default sink 'alsa_output.pci-0000_00_1b.0.analog-stereo' not existent, not restoring default sink setting.
(   0.016|   0.000) I: [pulseaudio] module-default-device-restore.c: Saved default source 'alsa_input.pci-0000_00_1b.0.analog-stereo' not existent, not restoring default source setting.
(   0.016|   0.000) I: [pulseaudio] module.c: Loaded "module-default-device-restore" (index: #8; argument: "").
(   0.016|   0.000) I: [pulseaudio] module.c: Loaded "module-rescue-streams" (index: #9; argument: "").
(   0.016|   0.000) D: [pulseaudio] module-always-sink.c: Autoloading null-sink as no other sinks detected.
(   0.017|   0.000) I: [pulseaudio] module-device-restore.c: Restoring volume for sink auto_null.
(   0.017|   0.000) I: [pulseaudio] sink.c: Created sink 0 "auto_null" with sample spec s16le 2ch 44100Hz and channel map front-left,front-right
(   0.017|   0.000) I: [pulseaudio] sink.c:     device.description = "Dummy Output"
(   0.017|   0.000) I: [pulseaudio] sink.c:     device.class = "abstract"
(   0.017|   0.000) I: [pulseaudio] sink.c:     device.icon_name = "audio-card"
(   0.017|   0.000) D: [pulseaudio] core-subscribe.c: Dropped redundant event due to change event.
(   0.017|   0.000) I: [pulseaudio] module-device-restore.c: Restoring volume for source auto_null.monitor.
(   0.017|   0.000) I: [pulseaudio] source.c: Created source 0 "auto_null.monitor" with sample spec s16le 2ch 44100Hz and channel map front-left,front-right
(   0.017|   0.000) I: [pulseaudio] source.c:     device.description = "Monitor of Dummy Output"
(   0.017|   0.000) I: [pulseaudio] source.c:     device.class = "monitor"
(   0.017|   0.000) I: [pulseaudio] source.c:     device.icon_name = "audio-input-microphone"
(   0.017|   0.000) D: [null-sink] module-null-sink.c: Thread starting up
(   0.017|   0.000) D: [pulseaudio] module-device-restore.c: Could not set format on sink auto_null
(   0.017|   0.000) I: [pulseaudio] module.c: Loaded "module-null-sink" (index: #10; argument: "sink_name=auto_null sink_properties='device.description="Dummy Output"'").
(   0.017|   0.000) I: [pulseaudio] module.c: Loaded "module-always-sink" (index: #11; argument: "").
(   0.017|   0.000) I: [pulseaudio] module.c: Loaded "module-intended-roles" (index: #12; argument: "").
(   0.018|   0.000) D: [pulseaudio] module-suspend-on-idle.c: Sink auto_null becomes idle, timeout in 5 seconds.
(   0.018|   0.000) I: [pulseaudio] module.c: Loaded "module-suspend-on-idle" (index: #13; argument: "").
(   0.018|   0.000) D: [pulseaudio] cli-command.c: Checking for existence of '/usr/lib/pulse-2.1/modules/module-console-kit.so': success
(   0.019|   0.001) I: [pulseaudio] client.c: Created 0 "ConsoleKit Session /org/freedesktop/ConsoleKit/Session1"
(   0.019|   0.000) D: [pulseaudio] module-console-kit.c: Added new session /org/freedesktop/ConsoleKit/Session1
(   0.019|   0.000) I: [pulseaudio] module.c: Loaded "module-console-kit" (index: #14; argument: "").
(   0.019|   0.000) D: [pulseaudio] cli-command.c: Checking for existence of '/usr/lib/pulse-2.1/modules/module-systemd-login.so': failure
(   0.019|   0.000) I: [pulseaudio] module.c: Loaded "module-position-event-sounds" (index: #15; argument: "").
(   0.019|   0.000) I: [pulseaudio] module.c: Loaded "module-filter-heuristics" (index: #16; argument: "").
(   0.020|   0.000) I: [pulseaudio] module.c: Loaded "module-filter-apply" (index: #17; argument: "").
(   0.020|   0.000) I: [pulseaudio] module.c: Loaded "module-switch-on-port-available" (index: #18; argument: "").
(   0.022|   0.002) D: [pulseaudio] dbus-util.c: Successfully connected to D-Bus session bus 265a7a09d4a72c2bf621563f51029c64 as :1.125
(   0.023|   0.000) D: [pulseaudio] main.c: Got org.PulseAudio1!
(   0.025|   0.002) D: [pulseaudio] main.c: Got org.pulseaudio.Server!
(   0.025|   0.000) I: [pulseaudio] main.c: Daemon startup complete.
(   0.025|   0.000) I: [pulseaudio] client.c: Created 1 "Native client (UNIX socket client)"
(   0.025|   0.000) D: [pulseaudio] protocol-native.c: Protocol version: remote 26, local 26
(   0.025|   0.000) I: [pulseaudio] protocol-native.c: Got credentials: uid=1000 gid=1000 success=1
(   0.025|   0.000) D: [pulseaudio] protocol-native.c: SHM possible: yes
(   0.025|   0.000) D: [pulseaudio] protocol-native.c: Negotiated SHM: yes
(   0.025|   0.000) I: [pulseaudio] client.c: Created 2 "Native client (UNIX socket client)"
(   0.026|   0.000) D: [pulseaudio] module-augment-properties.c: Looking for .desktop file for indicator-sound-service
(   0.026|   0.000) D: [pulseaudio] protocol-native.c: Protocol version: remote 26, local 26
(   0.026|   0.000) I: [pulseaudio] protocol-native.c: Got credentials: uid=1000 gid=1000 success=1
(   0.026|   0.000) D: [pulseaudio] protocol-native.c: SHM possible: yes
(   0.026|   0.000) D: [pulseaudio] protocol-native.c: Negotiated SHM: yes
(   0.027|   0.001) D: [pulseaudio] module-augment-properties.c: Looking for .desktop file for gnome-settings-daemon
(   5.022|   4.995) I: [pulseaudio] module-suspend-on-idle.c: Sink auto_null idle for too long, suspending ...
(   5.022|   0.000) D: [pulseaudio] sink.c: Suspend cause of sink auto_null is 0x0004, suspending
(   5.022|   0.000) D: [pulseaudio] core.c: Hmm, no streams around, trying to vacuum.
(   6.163|   1.140) D: [pulseaudio] protocol-native.c: Client indicator-sound-service changes volume of sink auto_null.
(   6.163|   0.000) I: [pulseaudio] module-device-restore.c: Storing volume/mute for device+port sink:auto_null:null.
(   6.187|   0.024) D: [pulseaudio] protocol-native.c: Client indicator-sound-service changes volume of sink auto_null.
(   6.187|   0.000) I: [pulseaudio] module-device-restore.c: Storing volume/mute for device+port sink:auto_null:null.
(   6.219|   0.031) D: [pulseaudio] protocol-native.c: Client indicator-sound-service changes volume of sink auto_null.
(   6.219|   0.000) I: [pulseaudio] module-device-restore.c: Storing volume/mute for device+port sink:auto_null:null.
(   6.251|   0.032) D: [pulseaudio] protocol-native.c: Client indicator-sound-service changes volume of sink auto_null.
(   6.251|   0.000) I: [pulseaudio] module-device-restore.c: Storing volume/mute for device+port sink:auto_null:null.
(   6.307|   0.055) D: [pulseaudio] protocol-native.c: Client indicator-sound-service changes volume of sink auto_null.
(   6.307|   0.000) I: [pulseaudio] module-device-restore.c: Storing volume/mute for device+port sink:auto_null:null.
(   6.347|   0.039) D: [pulseaudio] protocol-native.c: Client indicator-sound-service changes volume of sink auto_null.
(   6.347|   0.000) I: [pulseaudio] module-device-restore.c: Storing volume/mute for device+port sink:auto_null:null.
(   6.402|   0.055) D: [pulseaudio] protocol-native.c: Client indicator-sound-service changes volume of sink auto_null.
(   6.403|   0.000) I: [pulseaudio] module-device-restore.c: Storing volume/mute for device+port sink:auto_null:null.
(   6.490|   0.087) D: [pulseaudio] protocol-native.c: Client indicator-sound-service changes volume of sink auto_null.
(   6.490|   0.000) I: [pulseaudio] module-device-restore.c: Storing volume/mute for device+port sink:auto_null:null.
(   6.882|   0.391) D: [pulseaudio] protocol-native.c: Client indicator-sound-service changes volume of sink auto_null.
(   6.883|   0.000) I: [pulseaudio] module-device-restore.c: Storing volume/mute for device+port sink:auto_null:null.
(   6.911|   0.028) D: [pulseaudio] protocol-native.c: Client indicator-sound-service changes volume of sink auto_null.
(   6.911|   0.000) I: [pulseaudio] module-device-restore.c: Storing volume/mute for device+port sink:auto_null:null.
(   6.934|   0.022) D: [pulseaudio] protocol-native.c: Client indicator-sound-service changes volume of sink auto_null.
(   6.935|   0.000) I: [pulseaudio] module-device-restore.c: Storing volume/mute for device+port sink:auto_null:null.
(   6.951|   0.015) D: [pulseaudio] protocol-native.c: Client indicator-sound-service changes volume of sink auto_null.
(   6.951|   0.000) I: [pulseaudio] module-device-restore.c: Storing volume/mute for device+port sink:auto_null:null.
(   6.974|   0.023) D: [pulseaudio] protocol-native.c: Client indicator-sound-service changes volume of sink auto_null.
(   6.975|   0.000) I: [pulseaudio] module-device-restore.c: Storing volume/mute for device+port sink:auto_null:null.
(   6.996|   0.021) D: [pulseaudio] protocol-native.c: Client indicator-sound-service changes volume of sink auto_null.
(   6.996|   0.000) I: [pulseaudio] module-device-restore.c: Storing volume/mute for device+port sink:auto_null:null.
(   7.046|   0.050) D: [pulseaudio] protocol-native.c: Client indicator-sound-service changes volume of sink auto_null.
(   7.047|   0.000) I: [pulseaudio] module-device-restore.c: Storing volume/mute for device+port sink:auto_null:null.
(   7.091|   0.043) D: [pulseaudio] protocol-native.c: Client indicator-sound-service changes volume of sink auto_null.
(   7.091|   0.000) I: [pulseaudio] module-device-restore.c: Storing volume/mute for device+port sink:auto_null:null.
(   7.169|   0.078) D: [pulseaudio] protocol-native.c: Client indicator-sound-service changes volume of sink auto_null.
(   7.281|   0.111) D: [pulseaudio] protocol-native.c: Client indicator-sound-service changes volume of sink auto_null.
(   7.445|   0.163) D: [pulseaudio] protocol-native.c: Client indicator-sound-service changes volume of sink auto_null.
(   9.802|   2.357) D: [pulseaudio] protocol-native.c: Client indicator-sound-service changes volume of sink auto_null.
(   9.802|   0.000) I: [pulseaudio] module-device-restore.c: Storing volume/mute for device+port sink:auto_null:null.
(   9.826|   0.023) D: [pulseaudio] protocol-native.c: Client indicator-sound-service changes volume of sink auto_null.
(   9.826|   0.000) I: [pulseaudio] module-device-restore.c: Storing volume/mute for device+port sink:auto_null:null.
(   9.842|   0.015) D: [pulseaudio] protocol-native.c: Client indicator-sound-service changes volume of sink auto_null.
(   9.842|   0.000) I: [pulseaudio] module-device-restore.c: Storing volume/mute for device+port sink:auto_null:null.
(   9.874|   0.032) D: [pulseaudio] protocol-native.c: Client indicator-sound-service changes volume of sink auto_null.
(   9.874|   0.000) I: [pulseaudio] module-device-restore.c: Storing volume/mute for device+port sink:auto_null:null.
(   9.914|   0.039) D: [pulseaudio] protocol-native.c: Client indicator-sound-service changes volume of sink auto_null.
(   9.914|   0.000) I: [pulseaudio] module-device-restore.c: Storing volume/mute for device+port sink:auto_null:null.
(   9.974|   0.059) D: [pulseaudio] protocol-native.c: Client indicator-sound-service changes volume of sink auto_null.
(   9.975|   0.000) I: [pulseaudio] module-device-restore.c: Storing volume/mute for device+port sink:auto_null:null.
(  10.103|   0.127) D: [pulseaudio] protocol-native.c: Client indicator-sound-service changes volume of sink auto_null.
(  10.103|   0.000) I: [pulseaudio] module-device-restore.c: Storing volume/mute for device+port sink:auto_null:null.
(  10.170|   0.067) D: [pulseaudio] protocol-native.c: Client indicator-sound-service changes volume of sink auto_null.
(  10.171|   0.000) I: [pulseaudio] module-device-restore.c: Storing volume/mute for device+port sink:auto_null:null.
(  10.219|   0.048) D: [pulseaudio] protocol-native.c: Client indicator-sound-service changes volume of sink auto_null.
(  10.219|   0.000) I: [pulseaudio] module-device-restore.c: Storing volume/mute for device+port sink:auto_null:null.
(  10.259|   0.040) D: [pulseaudio] protocol-native.c: Client indicator-sound-service changes volume of sink auto_null.
(  10.260|   0.000) I: [pulseaudio] module-device-restore.c: Storing volume/mute for device+port sink:auto_null:null.
(  10.320|   0.060) D: [pulseaudio] protocol-native.c: Client indicator-sound-service changes volume of sink auto_null.
(  10.320|   0.000) I: [pulseaudio] module-device-restore.c: Storing volume/mute for device+port sink:auto_null:null.
(  11.608|   1.287) D: [pulseaudio] protocol-native.c: Client indicator-sound-service changes volume of sink auto_null.
(  11.608|   0.000) I: [pulseaudio] module-device-restore.c: Storing volume/mute for device+port sink:auto_null:null.
(  11.819|   0.210) D: [pulseaudio] protocol-native.c: Client indicator-sound-service changes volume of sink auto_null.
(  11.819|   0.000) I: [pulseaudio] module-device-restore.c: Storing volume/mute for device+port sink:auto_null:null.
(  16.167|   4.348) I: [pulseaudio] module-device-restore.c: Synced.
(  19.300|   3.132) I: [pulseaudio] main.c: Got signal SIGINT.
(  19.300|   0.000) I: [pulseaudio] main.c: Exiting.
(  19.300|   0.000) I: [pulseaudio] main.c: Daemon shutdown initiated.
(  19.300|   0.000) I: [pulseaudio] module.c: Unloading "module-device-restore" (index: #0).
(  19.300|   0.000) I: [pulseaudio] module.c: Unloaded "module-device-restore" (index: #0).
(  19.300|   0.000) I: [pulseaudio] module.c: Unloading "module-stream-restore" (index: #1).
(  19.300|   0.000) D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Ext.StreamRestore1 removed from object /org/pulseaudio/stream_restore1
(  19.301|   0.000) D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Ext.StreamRestore1.RestoreEntry removed from object /org/pulseaudio/stream_restore1/entry0
(  19.301|   0.000) D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Ext.StreamRestore1.RestoreEntry removed from object /org/pulseaudio/stream_restore1/entry1
(  19.301|   0.000) D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Ext.StreamRestore1.RestoreEntry removed from object /org/pulseaudio/stream_restore1/entry2
(  19.301|   0.000) D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Ext.StreamRestore1.RestoreEntry removed from object /org/pulseaudio/stream_restore1/entry3
(  19.301|   0.000) D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Ext.StreamRestore1.RestoreEntry removed from object /org/pulseaudio/stream_restore1/entry4
(  19.301|   0.000) D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Ext.StreamRestore1.RestoreEntry removed from object /org/pulseaudio/stream_restore1/entry5
(  19.301|   0.000) D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Ext.StreamRestore1.RestoreEntry removed from object /org/pulseaudio/stream_restore1/entry6
(  19.301|   0.000) D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Ext.StreamRestore1.RestoreEntry removed from object /org/pulseaudio/stream_restore1/entry7
(  19.301|   0.000) D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Ext.StreamRestore1.RestoreEntry removed from object /org/pulseaudio/stream_restore1/entry8
(  19.301|   0.000) D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Ext.StreamRestore1.RestoreEntry removed from object /org/pulseaudio/stream_restore1/entry9
(  19.301|   0.000) D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Ext.StreamRestore1.RestoreEntry removed from object /org/pulseaudio/stream_restore1/entry10
(  19.301|   0.000) D: [pulseaudio] flist.c: pulsecore/hashmap.c: entries flist is full (don't worry)
(  19.301|   0.000) D: [pulseaudio] flist.c: pulsecore/hashmap.c: entries flist is full (don't worry)
(  19.301|   0.000) D: [pulseaudio] flist.c: pulsecore/hashmap.c: entries flist is full (don't worry)
(  19.301|   0.000) D: [pulseaudio] flist.c: pulsecore/hashmap.c: entries flist is full (don't worry)
(  19.302|   0.000) D: [pulseaudio] flist.c: pulsecore/hashmap.c: entries flist is full (don't worry)
(  19.302|   0.000) D: [pulseaudio] flist.c: pulsecore/hashmap.c: entries flist is full (don't worry)
(  19.302|   0.000) D: [pulseaudio] flist.c: pulsecore/hashmap.c: entries flist is full (don't worry)
(  19.302|   0.000) D: [pulseaudio] flist.c: pulsecore/hashmap.c: entries flist is full (don't worry)
(  19.302|   0.000) D: [pulseaudio] flist.c: pulsecore/hashmap.c: entries flist is full (don't worry)
(  19.302|   0.000) D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Ext.StreamRestore1.RestoreEntry removed from object /org/pulseaudio/stream_restore1/entry11
(  19.302|   0.000) D: [pulseaudio] flist.c: pulsecore/hashmap.c: entries flist is full (don't worry)
(  19.302|   0.000) D: [pulseaudio] flist.c: pulsecore/hashmap.c: entries flist is full (don't worry)
(  19.302|   0.000) D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Ext.StreamRestore1.RestoreEntry removed from object /org/pulseaudio/stream_restore1/entry12
(  19.302|   0.000) D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Ext.StreamRestore1.RestoreEntry removed from object /org/pulseaudio/stream_restore1/entry13
(  19.302|   0.000) D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Ext.StreamRestore1.RestoreEntry removed from object /org/pulseaudio/stream_restore1/entry14
(  19.302|   0.000) D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Ext.StreamRestore1.RestoreEntry removed from object /org/pulseaudio/stream_restore1/entry15
(  19.302|   0.000) D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Ext.StreamRestore1.RestoreEntry removed from object /org/pulseaudio/stream_restore1/entry16
(  19.302|   0.000) D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Ext.StreamRestore1.RestoreEntry removed from object /org/pulseaudio/stream_restore1/entry17
(  19.302|   0.000) I: [pulseaudio] module.c: Unloaded "module-stream-restore" (index: #1).
(  19.303|   0.000) I: [pulseaudio] module.c: Unloading "module-card-restore" (index: #2).
(  19.303|   0.000) I: [pulseaudio] module.c: Unloaded "module-card-restore" (index: #2).
(  19.303|   0.000) I: [pulseaudio] module.c: Unloading "module-augment-properties" (index: #3).
(  19.303|   0.000) I: [pulseaudio] module.c: Unloaded "module-augment-properties" (index: #3).
(  19.303|   0.000) I: [pulseaudio] module.c: Unloading "module-udev-detect" (index: #4).
(  19.303|   0.000) I: [pulseaudio] module.c: Unloaded "module-udev-detect" (index: #4).
(  19.303|   0.000) I: [pulseaudio] module.c: Unloading "module-bluetooth-discover" (index: #5).
(  19.304|   0.001) I: [pulseaudio] module.c: Unloaded "module-bluetooth-discover" (index: #5).
(  19.305|   0.000) I: [pulseaudio] module.c: Unloading "module-native-protocol-unix" (index: #6).
(  19.305|   0.000) I: [pulseaudio] client.c: Freed 1 "Indicator Sound"
(  19.305|   0.000) I: [pulseaudio] client.c: Freed 2 "GNOME Volume Control Media Keys"
(  19.305|   0.000) I: [pulseaudio] module.c: Unloaded "module-native-protocol-unix" (index: #6).
(  19.305|   0.000) I: [pulseaudio] module.c: Unloading "module-gconf" (index: #7).
(  19.305|   0.000) I: [pulseaudio] module.c: Unloaded "module-gconf" (index: #7).
(  19.305|   0.000) I: [pulseaudio] module.c: Unloading "module-default-device-restore" (index: #8).
(  19.305|   0.000) I: [pulseaudio] module.c: Unloaded "module-default-device-restore" (index: #8).
(  19.305|   0.000) I: [pulseaudio] module.c: Unloading "module-rescue-streams" (index: #9).
(  19.305|   0.000) I: [pulseaudio] module.c: Unloaded "module-rescue-streams" (index: #9).
(  19.305|   0.000) I: [pulseaudio] module.c: Unloading "module-null-sink" (index: #10).
(  19.305|   0.000) D: [pulseaudio] module-always-sink.c: Autoloaded null-sink removed
(  19.306|   0.000) D: [null-sink] module-null-sink.c: Thread shutting down
(  19.306|   0.000) I: [pulseaudio] sink.c: Freeing sink 0 "auto_null"
(  19.306|   0.000) I: [pulseaudio] source.c: Freeing source 0 "auto_null.monitor"
(  19.306|   0.000) I: [pulseaudio] module.c: Unloaded "module-null-sink" (index: #10).
(  19.306|   0.000) I: [pulseaudio] module.c: Unloading "module-always-sink" (index: #11).
(  19.306|   0.000) I: [pulseaudio] module.c: Unloaded "module-always-sink" (index: #11).
(  19.307|   0.000) I: [pulseaudio] module.c: Unloading "module-intended-roles" (index: #12).
(  19.307|   0.000) I: [pulseaudio] module.c: Unloaded "module-intended-roles" (index: #12).
(  19.307|   0.000) I: [pulseaudio] module.c: Unloading "module-suspend-on-idle" (index: #13).
(  19.307|   0.000) I: [pulseaudio] module.c: Unloaded "module-suspend-on-idle" (index: #13).
(  19.307|   0.000) I: [pulseaudio] module.c: Unloading "module-console-kit" (index: #14).
(  19.307|   0.000) D: [pulseaudio] module-console-kit.c: Removing session /org/freedesktop/ConsoleKit/Session1
(  19.307|   0.000) I: [pulseaudio] client.c: Freed 0 "ConsoleKit Session /org/freedesktop/ConsoleKit/Session1"
(  19.307|   0.000) I: [pulseaudio] module.c: Unloaded "module-console-kit" (index: #14).
(  19.307|   0.000) I: [pulseaudio] module.c: Unloading "module-position-event-sounds" (index: #15).
(  19.307|   0.000) I: [pulseaudio] module.c: Unloaded "module-position-event-sounds" (index: #15).
(  19.307|   0.000) I: [pulseaudio] module.c: Unloading "module-filter-heuristics" (index: #16).
(  19.307|   0.000) I: [pulseaudio] module.c: Unloaded "module-filter-heuristics" (index: #16).
(  19.307|   0.000) I: [pulseaudio] module.c: Unloading "module-filter-apply" (index: #17).
(  19.307|   0.000) I: [pulseaudio] module.c: Unloaded "module-filter-apply" (index: #17).
(  19.307|   0.000) I: [pulseaudio] module.c: Unloading "module-switch-on-port-available" (index: #18).
(  19.307|   0.000) I: [pulseaudio] module.c: Unloaded "module-switch-on-port-available" (index: #18).
(  19.307|   0.000) I: [pulseaudio] main.c: Daemon terminated.
```

---

### Post by Yellow Pasque on 2013-01-25
1. You didn't give the link to your alsa info..
2. Please use [ CODE ][ /CODE ] tags for large blocks of text.

---

### Post by Simeo on 2013-01-25
Sorry. Fixed and Alsa Info below:

```
#!/bin/bash

SCRIPT_VERSION=0.4.61
CHANGELOG="http://www.alsa-project.org/alsa-info.sh.changelog"

#################################################################################
#Copyright (C) 2007 Free Software Foundation.

#This program is free software; you can redistribute it and/or modify
#it under the terms of the GNU General Public License as published by
#the Free Software Foundation; either version 2 of the License, or
#(at your option) any later version.

#This program is distributed in the hope that it will be useful,
#but WITHOUT ANY WARRANTY; without even the implied warranty of
#MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
#GNU General Public License for more details.

#You should have received a copy of the GNU General Public License
#along with this program; if not, write to the Free Software
#Foundation, Inc., 51 Franklin Street, Fifth Floor, Boston, MA  02110-1301, USA.

##################################################################################

#The script was written for 2 main reasons:
# 1. Remove the need for the devs/helpers to ask several questions before we can easily help the user.
# 2. Allow newer/inexperienced ALSA users to give us all the info we need to help them.

#Set the locale (this may or may not be a good idea.. let me know)
export LC_ALL=C

#Change the PATH variable, so we can run lspci (needed for some distros)
PATH=$PATH:/bin:/sbin:/usr/bin:/usr/sbin
BGTITLE="ALSA-Info v $SCRIPT_VERSION"
PASTEBINKEY="C9cRIO8m/9y8Cs0nVs0FraRx7U0pHsuc"
#Define some simple functions

pbcheck(){
    [[ $UPLOAD = "no" ]] && return

    if [[ -z $PASTEBIN ]]; then
        [[ $(ping -c1 www.alsa-project.org) ]] || KEEP_FILES="yes" UPLOAD="no" PBERROR="yes"
    else
        [[ $(ping -c1 www.pastebin.ca) ]] || KEEP_FILES="yes" UPLOAD="no" PBERROR="yes"
    fi
}

update() {
    SHFILE=`mktemp -t alsa-info.XXXXXXXXXX` || exit 1
    wget -O $SHFILE "http://www.alsa-project.org/alsa-info.sh" >/dev/null 2>&1
    REMOTE_VERSION=`grep SCRIPT_VERSION $SHFILE |head -n1 |sed 's/.*=//'`
    if [ "$REMOTE_VERSION" != "$SCRIPT_VERSION" ]; then
        if [[ -n $DIALOG ]]
        then
            OVERWRITE=
            if [ -w $0 ]; then
                dialog --yesno "Newer version of ALSA-Info has been found\n\nDo you wish to install it?\nNOTICE: The original file $0 will be overwritten!" 0 0
                DIALOG_EXIT_CODE=$?
                if [[ $DIALOG_EXIT_CODE = 0 ]]; then
                  OVERWRITE=yes
                fi
            fi
            if [ -z "$OVERWRITE" ]; then
                dialog --yesno "Newer version of ALSA-Info has been found\n\nDo you wish to download it?" 0 0
                DIALOG_EXIT_CODE=$?
            fi
            if [[ $DIALOG_EXIT_CODE = 0 ]]
            then
                echo "Newer version detected: $REMOTE_VERSION"
                echo "To view the ChangeLog, please visit $CHANGELOG"
                if [ "$OVERWRITE" = "yes" ]; then
                    cp $SHFILE $0
                    echo "ALSA-Info script has been updated to v $REMOTE_VERSION"
                    echo "Please re-run the script"
                    rm $SHFILE 2>/dev/null
                else
                    echo "ALSA-Info script has been downloaded as $SHFILE."
                    echo "Please re-run the script from new location."
                fi
                exit
            else
                rm $SHFILE 2>/dev/null
            fi
        else
            echo "Newer version detected: $REMOTE_VERSION"
            echo "To view the ChangeLog, please visit $CHANGELOG"
            if [ -w $0 ]; then
                echo "The original file $0 will be overwritten!"
                echo -n "If you do not like to proceed, press Ctrl-C now.." ; read inp
                cp $SHFILE $0
                echo "ALSA-Info script has been updated. Please re-run it."
                rm $SHFILE 2>/dev/null
            else
                echo "ALSA-Info script has been downloaded $SHFILE."
                echo "Please, re-run it from new location."
            fi
            exit
        fi
    else
        rm $SHFILE 2>/dev/null
    fi
}

cleanup() {
    if [ -n "$TEMPDIR" -a "$KEEP_FILES" != "yes" ]; then
        rm -rf "$TEMPDIR" 2>/dev/null
    fi
    test -n "$KEEP_OUTPUT" || rm -f "$NFILE"
}


withaplay() {
        echo "!!Aplay/Arecord output" >> $FILE
        echo "!!--------------------" >> $FILE
        echo "" >> $FILE
           echo "APLAY" >> $FILE
    echo "" >> $FILE 
    aplay -l >> $FILE 2>&1
        echo "" >> $FILE
           echo "ARECORD" >> $FILE
    echo "" >> $FILE
    arecord -l >> $FILE 2>&1
    echo "" >> $FILE
}

withlsmod() {
    echo "!!All Loaded Modules" >> $FILE
    echo "!!------------------" >> $FILE
    echo "" >> $FILE
    lsmod |awk {'print $1'} >> $FILE
    echo "" >> $FILE
    echo "" >> $FILE
}

withamixer() {
        echo "!!Amixer output" >> $FILE
        echo "!!-------------" >> $FILE
        echo "" >> $FILE
    for i in `grep "]: " /proc/asound/cards | awk -F ' ' '{ print $1} '` ; do
    CARD_NAME=`grep "^ *$i " $TEMPDIR/alsacards.tmp|awk {'print $2'}`
    echo "!!-------Mixer controls for card $i $CARD_NAME]" >> $FILE
    echo "" >>$FILE
    amixer -c$i info>> $FILE 2>&1
    amixer -c$i>> $FILE 2>&1
        echo "" >> $FILE
    done
    echo "" >> $FILE
}

withalsactl() {
    echo "!!Alsactl output" >> $FILE
        echo "!!--------------" >> $FILE
        echo "" >> $FILE
        exe=""
        if [ -x /usr/sbin/alsactl ]; then
            exe="/usr/sbin/alsactl"
        fi
        if [ -x /usr/local/sbin/alsactl ]; then
            exe="/usr/local/sbin/alsactl"
        fi
        if [ -z "$exe" ]; then
            exe=`whereis alsactl | cut -d ' ' -f 2`
        fi
    $exe -f $TEMPDIR/alsactl.tmp store
    echo "--startcollapse--" >> $FILE
    cat $TEMPDIR/alsactl.tmp >> $FILE
    echo "--endcollapse--" >> $FILE
    echo "" >> $FILE
    echo "" >> $FILE
}

withdevices() {
        echo "!!ALSA Device nodes" >> $FILE
        echo "!!-----------------" >> $FILE
        echo "" >> $FILE
        ls -la /dev/snd/* >> $FILE
        echo "" >> $FILE
        echo "" >> $FILE
}

withconfigs() {
if [[ -e $HOME/.asoundrc ]] || [[ -e /etc/asound.conf ]] || [[ -e $HOME/.asoundrc.asoundconf ]]
then
        echo "!!ALSA configuration files" >> $FILE
        echo "!!------------------------" >> $FILE
        echo "" >> $FILE

        #Check for ~/.asoundrc
        if [[ -e $HOME/.asoundrc ]]
        then
                echo "!!User specific config file (~/.asoundrc)" >> $FILE
                echo "" >> $FILE
                cat $HOME/.asoundrc >> $FILE
                echo "" >> $FILE
                echo "" >> $FILE
        fi
    #Check for .asoundrc.asoundconf (seems to be Ubuntu specific)
    if [[ -e $HOME/.asoundrc.asoundconf ]]
    then
        echo "!!asoundconf-generated config file" >> $FILE
        echo "" >> $FILE
        cat $HOME/.asoundrc.asoundconf >> $FILE
        echo "" >> $FILE
        echo "" >> $FILE
    fi
        #Check for /etc/asound.conf
        if [[ -e /etc/asound.conf ]]
        then
                echo "!!System wide config file (/etc/asound.conf)" >> $FILE
                echo "" >> $FILE
                cat /etc/asound.conf >> $FILE
                echo "" >> $FILE
                echo "" >> $FILE
        fi
fi
}

withsysfs() {
    local i f
    local printed=""
    for i in /sys/class/sound/*; do
    case "$i" in
        */hwC?D?)
        if [ -f $i/init_pin_configs ]; then
            if [ -z "$printed" ]; then
            echo "!!Sysfs Files" >> $FILE
            echo "!!-----------" >> $FILE
            echo "" >> $FILE
            fi
            for f in init_pin_configs driver_pin_configs user_pin_configs init_verbs; do
            echo "$i/$f:" >> $FILE
            cat $i/$f >> $FILE
            echo >> $FILE
            done
            printed=yes
        fi
        ;;
        esac
    done
    if [ -n "$printed" ]; then
    echo "" >> $FILE
    fi
}

withdmesg() {
    echo "!!ALSA/HDA dmesg" >> $FILE
    echo "!!--------------" >> $FILE
    echo "" >> $FILE
    dmesg | grep -C1 -E 'ALSA|HDA|HDMI|sound|hda.codec|hda.intel' >> $FILE
    echo "" >> $FILE
    echo "" >> $FILE
}

withall() {
    withdevices
    withconfigs
    withaplay
    withamixer
    withalsactl
    withlsmod
    withsysfs
    withdmesg
}

get_alsa_library_version() {
    ALSA_LIB_VERSION=`grep VERSION_STR /usr/include/alsa/version.h 2>/dev/null|awk {'print $3'}|sed 's/"//g'`

    if [ -z "$ALSA_LIB_VERSION" ]; then
        if [ -f /etc/lsb-release ]; then
            . /etc/lsb-release
            case "$DISTRIB_ID" in
                Ubuntu)
                    if which dpkg > /dev/null ; then
                        ALSA_LIB_VERSION=`dpkg -l libasound2 | tail -1 | awk '{print $3}' | cut -f 1 -d -`
                    fi

                    if [ "$ALSA_LIB_VERSION" = "<none>" ]; then
                        ALSA_LIB_VERSION=""
                    fi
                    return
                    ;;
                *)
                    return
                    ;;
            esac
        elif [ -f /etc/debian_version ]; then
            if which dpkg > /dev/null ; then
                ALSA_LIB_VERSION=`dpkg -l libasound2 | tail -1 | awk '{print $3}' | cut -f 1 -d -`
            fi

            if [ "$ALSA_LIB_VERSION" = "<none>" ]; then
                ALSA_LIB_VERSION=""
            fi
            return
        fi
    fi
}


#Run checks to make sure the programs we need are installed.
LSPCI=$(which lspci 2>/dev/null| sed 's|^[^/]*||' 2>/dev/null);
TPUT=$(which tput 2>/dev/null| sed 's|^[^/]*||' 2>/dev/null);
DIALOG=$(which dialog 2>/dev/null | sed 's|^[^/]*||' 2>/dev/null);

#Check to see if sysfs is enabled in the kernel. We'll need this later on
SYSFS=$(mount |grep sysfs|awk {'print $3'});

#Check modprobe config files for sound related options
SNDOPTIONS=$(modprobe -c|sed -n 's/^options \(snd[-_][^ ]*\)/\1:/p')

KEEP_OUTPUT=
NFILE=""

PASTEBIN=""
WWWSERVICE="www.alsa-project.org"
WELCOME="yes"
PROCEED="yes"
UPLOAD="ask"
REPEAT=""
while [ -z "$REPEAT" ]; do
REPEAT="no"
case "$1" in
    --update|--help|--about)
        WELCOME="no"
        PROCEED="no"
        ;;
    --upload)
        UPLOAD="yes"
        WELCOME="no"
        ;;
    --no-upload)
        UPLOAD="no"
        WELCOME="no"
        ;;
    --pastebin)
        PASTEBIN="yes"
        WWWSERVICE="pastebin"
        ;;
    --no-dialog)
        DIALOG=""
        REPEAT=""
        shift
        ;;
    --stdout)
        DIALOG=""
        UPLOAD="no"
        WELCOME="no"
        TOSTDOUT="yes"
        ;;
esac
done


#Script header output.
if [ "$WELCOME" = "yes" ]; then
greeting_message="\

This script visits the following commands/files to collect diagnostic
information about your ALSA installation and sound related hardware.

  dmesg
  lspci
  lsmod
  aplay
  amixer
  alsactl
  /proc/asound/
  /sys/class/sound/
  ~/.asoundrc (etc.)

See '$0 --help' for command line options.
"
if [[ -n "$DIALOG" ]]; then
    dialog  --backtitle "$BGTITLE" \
        --title "ALSA-Info script v $SCRIPT_VERSION" \
        --msgbox "$greeting_message" 20 80
else
    echo "ALSA Information Script v $SCRIPT_VERSION"
    echo "--------------------------------"
    echo "$greeting_message"
fi # dialog
fi # WELCOME

#Set the output file
TEMPDIR=`mktemp -t -d alsa-info.XXXXXXXXXX` || exit 1
FILE="$TEMPDIR/alsa-info.txt"
if [ -z "$NFILE" ]; then
    NFILE=`mktemp -t alsa-info.txt.XXXXXXXXXX` || exit 1
fi

trap cleanup 0

if [ "$PROCEED" = "yes" ]; then

if [[ -z "$LSPCI" ]] 
then
    echo "This script requires lspci. Please install it, and re-run this script."
    exit 0
fi

#Fetch the info and store in temp files/variables
DISTRO=`grep -ihs "buntu\|SUSE\|Fedora\|PCLinuxOS\|MEPIS\|Mandriva\|Debian\|Damn\|Sabayon\|Slackware\|KNOPPIX\|Gentoo\|Zenwalk\|Mint\|Kubuntu\|FreeBSD\|Puppy\|Freespire\|Vector\|Dreamlinux\|CentOS\|Arch\|Xandros\|Elive\|SLAX\|Red\|BSD\|KANOTIX\|Nexenta\|Foresight\|GeeXboX\|Frugalware\|64\|SystemRescue\|Novell\|Solaris\|BackTrack\|KateOS\|Pardus" /etc/{issue,*release,*version}`
KERNEL_VERSION=`uname -r`
KERNEL_PROCESSOR=`uname -p`
KERNEL_MACHINE=`uname -m`
KERNEL_OS=`uname -o`
[[ `uname -v |grep SMP`  ]] && KERNEL_SMP="Yes" || KERNEL_SMP="No" 
ALSA_DRIVER_VERSION=`cat /proc/asound/version |head -n1|awk {'print $7'} |sed 's/\.$//'`
get_alsa_library_version
ALSA_UTILS_VERSION=`amixer -v |awk {'print $3'}`
VENDOR_ID=`lspci -vn |grep 040[1-3] | awk -F':' '{print $3}'|awk {'print substr($0, 2);}' >$TEMPDIR/vendor_id.tmp`
DEVICE_ID=`lspci -vn |grep 040[1-3] | awk -F':' '{print $4}'|awk {'print $1'} >$TEMPDIR/device_id.tmp`
LAST_CARD=$((`grep "]: " /proc/asound/cards | wc -l` - 1 ))

ESDINST=$(which esd 2>/dev/null| sed 's|^[^/]*||' 2>/dev/null)
PAINST=$(which pulseaudio 2>/dev/null| sed 's|^[^/]*||' 2>/dev/null)
ARTSINST=$(which artsd 2>/dev/null| sed 's|^[^/]*||' 2>/dev/null)
JACKINST=$(which jackd 2>/dev/null| sed 's|^[^/]*||' 2>/dev/null)
ROARINST=$(which roard 2>/dev/null| sed 's|^[^/]*||' 2>/dev/null)
DMIDECODE=$(which dmidecode 2>/dev/null| sed 's|^[^/]*||' 2>/dev/null)

#Check for DMI data
if [ -d /sys/class/dmi/id ]; then
    # No root privileges are required when using sysfs method
    DMI_SYSTEM_MANUFACTURER=$(cat /sys/class/dmi/id/sys_vendor 2>/dev/null)
    DMI_SYSTEM_PRODUCT_NAME=$(cat /sys/class/dmi/id/product_name 2>/dev/null)
    DMI_SYSTEM_PRODUCT_VERSION=$(cat /sys/class/dmi/id/product_version 2>/dev/null)
    DMI_SYSTEM_FIRMWARE_VERSION=$(cat /sys/class/dmi/id/bios_version 2>/dev/null)
elif [ -x $DMIDECODE ]; then
    DMI_SYSTEM_MANUFACTURER=$($DMIDECODE -s system-manufacturer 2>/dev/null)
    DMI_SYSTEM_PRODUCT_NAME=$($DMIDECODE -s system-product-name 2>/dev/null)
    DMI_SYSTEM_PRODUCT_VERSION=$($DMIDECODE -s system-version 2>/dev/null)
    DMI_SYSTEM_FIRMWARE_VERSION=$($DMIDECODE -s bios-version 2>/dev/null)
fi

cat /proc/asound/modules 2>/dev/null|awk {'print $2'}>$TEMPDIR/alsamodules.tmp
cat /proc/asound/cards >$TEMPDIR/alsacards.tmp
lspci |grep -i "multi\|audio">$TEMPDIR/lspci.tmp

#Check for HDA-Intel cards codec#*
cat /proc/asound/card*/codec\#* > $TEMPDIR/alsa-hda-intel.tmp 2> /dev/null

#Check for AC97 cards codec
cat /proc/asound/card*/codec97\#0/ac97\#0-0 > $TEMPDIR/alsa-ac97.tmp 2> /dev/null
cat /proc/asound/card*/codec97\#0/ac97\#0-0+regs > $TEMPDIR/alsa-ac97-regs.tmp 2> /dev/null

#Check for USB mixer setup
cat /proc/asound/card*/usbmixer > $TEMPDIR/alsa-usbmixer.tmp 2> /dev/null

#Fetch the info, and put it in $FILE in a nice readable format.
if [[ -z $PASTEBIN ]]; then
echo "upload=true&script=true&cardinfo=" > $FILE
else
echo "name=$USER&type=33&description=/tmp/alsa-info.txt&expiry=&s=Submit+Post&content=" > $FILE
fi
echo "!!################################" >> $FILE
echo "!!ALSA Information Script v $SCRIPT_VERSION" >> $FILE
echo "!!################################" >> $FILE
echo "" >> $FILE
echo "!!Script ran on: `LANG=C TZ=UTC date`" >> $FILE
echo "" >> $FILE
echo "" >> $FILE
echo "!!Linux Distribution" >> $FILE
echo "!!------------------" >> $FILE
echo "" >> $FILE
echo $DISTRO >> $FILE
echo "" >> $FILE
echo "" >> $FILE
echo "!!DMI Information" >> $FILE
echo "!!---------------" >> $FILE
echo "" >> $FILE
echo "Manufacturer:      $DMI_SYSTEM_MANUFACTURER" >> $FILE
echo "Product Name:      $DMI_SYSTEM_PRODUCT_NAME" >> $FILE
echo "Product Version:   $DMI_SYSTEM_PRODUCT_VERSION" >> $FILE
echo "Firmware Version:  $DMI_SYSTEM_FIRMWARE_VERSION" >> $FILE
echo "" >> $FILE
echo "" >> $FILE
echo "!!Kernel Information" >> $FILE
echo "!!------------------" >> $FILE
echo "" >> $FILE
echo "Kernel release:    $KERNEL_VERSION" >> $FILE
echo "Operating System:  $KERNEL_OS" >> $FILE
echo "Architecture:      $KERNEL_MACHINE" >> $FILE
echo "Processor:         $KERNEL_PROCESSOR" >> $FILE
echo "SMP Enabled:       $KERNEL_SMP" >> $FILE
echo "" >> $FILE
echo "" >> $FILE
echo "!!ALSA Version" >> $FILE
echo "!!------------" >> $FILE
echo "" >> $FILE
echo "Driver version:     $ALSA_DRIVER_VERSION" >> $FILE
echo "Library version:    $ALSA_LIB_VERSION" >> $FILE
echo "Utilities version:  $ALSA_UTILS_VERSION" >> $FILE
echo "" >> $FILE
echo "" >> $FILE
echo "!!Loaded ALSA modules" >> $FILE
echo "!!-------------------" >> $FILE
echo "" >> $FILE
cat $TEMPDIR/alsamodules.tmp >> $FILE
echo "" >> $FILE
echo "" >> $FILE
echo "!!Sound Servers on this system" >> $FILE
echo "!!----------------------------" >> $FILE
echo "" >> $FILE
if [[ -n $PAINST ]];then
[[ `pgrep '^(.*/)?pulseaudio$'` ]] && PARUNNING="Yes" || PARUNNING="No"
echo "Pulseaudio:" >> $FILE
echo "      Installed - Yes ($PAINST)" >> $FILE
echo "      Running - $PARUNNING" >> $FILE
echo "" >> $FILE
fi
if [[ -n $ESDINST ]];then
[[ `pgrep '^(.*/)?esd$'` ]] && ESDRUNNING="Yes" || ESDRUNNING="No"
echo "ESound Daemon:" >> $FILE
echo "      Installed - Yes ($ESDINST)" >> $FILE
echo "      Running - $ESDRUNNING" >> $FILE
echo "" >> $FILE
fi
if [[ -n $ARTSINST ]];then
[[ `pgrep '^(.*/)?artsd$'` ]] && ARTSRUNNING="Yes" || ARTSRUNNING="No"
echo "aRts:" >> $FILE
echo "      Installed - Yes ($ARTSINST)" >> $FILE
echo "      Running - $ARTSRUNNING" >> $FILE
echo "" >> $FILE
fi
if [[ -n $JACKINST ]];then
[[ `pgrep '^(.*/)?jackd$'` ]] && JACKRUNNING="Yes" || JACKRUNNING="No"
echo "Jack:" >> $FILE
echo "      Installed - Yes ($JACKINST)" >> $FILE
echo "      Running - $JACKRUNNING" >> $FILE
echo "" >> $FILE
fi
if [[ -n $ROARINST ]];then
[[ `pgrep '^(.*/)?roard$'` ]] && ROARRUNNING="Yes" || ROARRUNNING="No"
echo "RoarAudio:" >> $FILE
echo "      Installed - Yes ($ROARINST)" >> $FILE
echo "      Running - $ROARRUNNING" >> $FILE
echo "" >> $FILE
fi
if [[ -z "$PAINST" && -z "$ESDINST" && -z "$ARTSINST" && -z "$JACKINST" && -z "$ROARINST" ]];then
echo "No sound servers found." >> $FILE
echo "" >> $FILE
fi
echo "" >> $FILE
echo "!!Soundcards recognised by ALSA" >> $FILE
echo "!!-----------------------------" >> $FILE
echo "" >> $FILE
cat $TEMPDIR/alsacards.tmp >> $FILE
echo "" >> $FILE
echo "" >> $FILE
echo "!!PCI Soundcards installed in the system" >> $FILE
echo "!!--------------------------------------" >> $FILE
echo "" >> $FILE
cat $TEMPDIR/lspci.tmp >> $FILE
echo "" >> $FILE
echo "" >> $FILE
echo "!!Advanced information - PCI Vendor/Device/Subsystem ID's" >> $FILE
echo "!!-------------------------------------------------------" >> $FILE
echo "" >> $FILE
lspci -vvn |grep -A1 040[1-3] >> $FILE
echo "" >> $FILE
echo "" >> $FILE

if [ "$SNDOPTIONS" ]
then
echo "!!Modprobe options (Sound related)" >> $FILE
echo "!!--------------------------------" >> $FILE
echo "" >> $FILE
modprobe -c|sed -n 's/^options \(snd[-_][^ ]*\)/\1:/p' >> $FILE
echo "" >> $FILE
echo "" >> $FILE
fi

if [ -d "$SYSFS" ]
then
echo "!!Loaded sound module options" >> $FILE
echo "!!---------------------------" >> $FILE
echo "" >> $FILE
for mod in `cat /proc/asound/modules|awk {'print $2'}`;do
echo "!!Module: $mod" >> $FILE
for params in `echo $SYSFS/module/$mod/parameters/*`; do
    echo -ne "\t";
    echo "$params : `cat $params`" | sed 's:.*/::';
done >> $FILE
echo "" >> $FILE
done
echo "" >> $FILE
fi

if [ -s "$TEMPDIR/alsa-hda-intel.tmp" ] 
then
    echo "!!HDA-Intel Codec information" >> $FILE
    echo "!!---------------------------" >> $FILE
    echo "--startcollapse--" >> $FILE
    echo "" >> $FILE
    cat $TEMPDIR/alsa-hda-intel.tmp >> $FILE
    echo "--endcollapse--" >> $FILE
    echo "" >> $FILE
    echo "" >> $FILE
fi

if [ -s "$TEMPDIR/alsa-ac97.tmp" ]
then
        echo "!!AC97 Codec information" >> $FILE
        echo "!!----------------------" >> $FILE
        echo "--startcollapse--" >> $FILE
        echo "" >> $FILE
        cat $TEMPDIR/alsa-ac97.tmp >> $FILE
        echo "" >> $FILE
        cat $TEMPDIR/alsa-ac97-regs.tmp >> $FILE
        echo "--endcollapse--" >> $FILE
    echo "" >> $FILE
    echo "" >> $FILE
fi

if [ -s "$TEMPDIR/alsa-usbmixer.tmp" ]
then
        echo "!!USB Mixer information" >> $FILE
        echo "!!---------------------" >> $FILE
        echo "--startcollapse--" >> $FILE
        echo "" >> $FILE
        cat $TEMPDIR/alsa-usbmixer.tmp >> $FILE
        echo "--endcollapse--" >> $FILE
    echo "" >> $FILE
    echo "" >> $FILE
fi

#If no command line options are specified, then run as though --with-all was specified
if [[ -z "$1" ]]
then
    update
    withall
    pbcheck    
fi

fi # proceed

#loop through command line arguments, until none are left.
if [[ -n "$1" ]]
then
    until [ -z "$1" ]
    do
    case "$1" in
        --pastebin)
                update
            withall
                pbcheck
            ;;
        --update)
            update
            exit
            ;;
        --upload)
            UPLOAD="yes"
            withall
            ;;
        --no-upload)
            UPLOAD="no"
            withall
            ;;
        --output)
            shift
            NFILE="$1"
            KEEP_OUTPUT="yes"
            ;;
        --debug)
            echo "Debugging enabled. $FILE and $TEMPDIR will not be deleted"
            KEEP_FILES="yes"
            echo ""
            withall
            ;;
        --with-all)
            withall
            ;;
        --with-aplay)
            withaplay
            ;;
        --with-amixer)
            withamixer
            ;;
        --with-alsactl)
            withalsactl
            ;;
        --with-devices)
            withdevices
            ;;
        --with-dmesg)
            withdmesg
            ;;
        --with-configs)
            if [[ -e $HOME/.asoundrc ]] || [[ -e /etc/asound.conf ]]
            then
                echo "!!ALSA configuration files" >> $FILE
                echo "!!------------------------" >> $FILE
                echo "" >> $FILE

                #Check for ~/.asoundrc
                if [[ -e $HOME/.asoundrc ]]
                then
                    echo "!!User specific config file ($HOME/.asoundrc)" >> $FILE
                    echo "" >> $FILE
                    cat $HOME/.asoundrc >> $FILE
                    echo "" >> $FILE
                    echo "" >> $FILE
                fi

                #Check for /etc/asound.conf
                if [[ -e /etc/asound.conf ]]
                then
                    echo "!!System wide config file (/etc/asound.conf)" >> $FILE
                    echo "" >> $FILE
                    cat /etc/asound.conf >> $FILE
                    echo "" >> $FILE
                    echo "" >> $FILE
                fi
            fi
            ;;
        --stdout)
            UPLOAD="no"
            withall
            cat $FILE
            rm $FILE
            ;;
        --about)
            echo "Written/Tested by the following users of #alsa on irc.freenode.net:"
            echo ""
            echo "    wishie - Script author and developer / Testing"
            echo "    crimsun - Various script ideas / Testing"
            echo "    gnubien - Various script ideas / Testing"
            echo "    GrueMaster - HDA Intel specific items / Testing"
            echo "    olegfink - Script update function"
            echo "  TheMuso - display to stdout functionality"
            exit 0
            ;;
        *)
            echo "alsa-info.sh version $SCRIPT_VERSION"
            echo ""
            echo "Available options:"
            echo "    --with-aplay (includes the output of aplay -l)"
            echo "    --with-amixer (includes the output of amixer)"
            echo "    --with-alsactl (includes the output of alsactl)"
            echo "    --with-configs (includes the output of ~/.asoundrc and"
            echo "        /etc/asound.conf if they exist)" 
            echo "    --with-devices (shows the device nodes in /dev/snd/)"
            echo "    --with-dmesg (shows the ALSA/HDA kernel messages)"
            echo ""
            echo "    --output FILE (specify the file to output for no-upload mode)"
            echo "    --update (check server for script updates)"
            echo "    --upload (upload contents to remote server)"
            echo "    --no-upload (do not upload contents to remote server)"
            echo "    --pastebin (use http://pastebin.ca) as remote server"
            echo "        instead www.alsa-project.org"
            echo "    --stdout (print alsa information to standard output"
            echo "        instead of a file)"
            echo "    --about (show some information about the script)"
            echo "    --debug (will run the script as normal, but will not"
            echo "         delete $FILE)"
            exit 0
            ;;
    esac
    shift 1
    done
fi

if [ "$PROCEED" = "no" ]; then
    exit 1
fi

if [ "$UPLOAD" = "ask" ]; then
    if [[ -n "$DIALOG" ]]; then
        dialog --backtitle "$BGTITLE" --title "Information collected" --yes-label " UPLOAD / SHARE " --no-label " SAVE LOCALLY " --defaultno --yesno "\n\nAutomatically upload ALSA information to $WWWSERVICE?" 10 80
        DIALOG_EXIT_CODE=$?
        if [ $DIALOG_EXIT_CODE != 0 ]; then
            UPLOAD="no"
        else
            UPLOAD="yes"
        fi
    else
        echo -n "Automatically upload ALSA information to $WWWSERVICE? [y/N] : "
        read -e CONFIRM
        if [ "$CONFIRM" != "y" ]; then
            UPLOAD="no"
        else
            UPLOAD="yes"
        fi
    fi

fi

if [ "$UPLOAD" = "no" ]; then

    if [ -z "$TOSTDOUT" ]; then
        mv -f $FILE $NFILE || exit 1
        KEEP_OUTPUT="yes"
    fi

    if [[ -n $DIALOG ]]
    then
        if [[ -n $PBERROR ]]; then
            dialog --backtitle "$BGTITLE" --title "Information collected" --msgbox "An error occurred while contacting the $WWWSERVICE.\n Your information was NOT automatically uploaded.\n\nYour ALSA information is in $NFILE" 10 100
        else
            dialog --backtitle "$BGTITLE" --title "Information collected" --msgbox "\n\nYour ALSA information is in $NFILE" 10 60
        fi
    else
        echo

        if [[ -n $PBERROR ]]; then
            echo "An error occurred while contacting the $WWWSERVICE."
            echo "Your information was NOT automatically uploaded."
            echo ""
            echo "Your ALSA information is in $NFILE"
            echo ""
        else
            if [ -z "$TOSTDOUT" ]; then
                echo ""
                echo "Your ALSA information is in $NFILE"
                echo ""
            fi
        fi
    fi

    exit

fi # UPLOAD

#Test that wget is installed, and supports --post-file. Upload $FILE if it does, and prompt user to upload file if it doesnt. 
if
WGET=$(which wget 2>/dev/null| sed 's|^[^/]*||' 2>/dev/null); [[ -n "${WGET}" ]] && [[ -x "${WGET}" ]] && [[ `wget --help |grep post-file` ]]
then

if [[ -n $DIALOG ]]
then

if [[ -z $PASTEBIN ]]; then
    wget -O - --tries=5 --timeout=60 --post-file=$FILE "http://www.alsa-project.org/cardinfo-db/" &>$TEMPDIR/wget.tmp || echo "Upload failed; exit"
    { for i in 10 20 30 40 50 60 70 80 90; do
        echo $i
        sleep 0.2
    done
    echo; } |dialog --backtitle "$BGTITLE" --guage "Uploading information to www.alsa-project.org ..." 6 70 0
else
    wget -O - --tries=5 --timeout=60 --post-file=$FILE "http://pastebin.ca/quiet-paste.php?api=$PASTEBINKEY&encrypt=t&encryptpw=blahblah" &>$TEMPDIR/wget.tmp || echo "Upload failed; exit"
    { for i in 10 20 30 40 50 60 70 80 90; do
        echo $i
        sleep 0.2
    done
    echo; } |dialog --backtitle "$BGTITLE" --guage "Uploading information to www.pastebin.ca ..." 6 70 0
fi

dialog --backtitle "$BGTITLE" --title "Information uploaded" --yesno "Would you like to see the uploaded information?" 5 100 
DIALOG_EXIT_CODE=$?
if [ $DIALOG_EXIT_CODE = 0 ]; then
    grep -v "alsa-info.txt" $FILE >$TEMPDIR/uploaded.txt
    dialog --backtitle "$BGTITLE" --textbox $TEMPDIR/uploaded.txt 0 0
fi

clear

# no dialog
else

if [[ -z $PASTEBIN ]]; then
    echo -n "Uploading information to www.alsa-project.org ... " 
    wget -O - --tries=5 --timeout=60 --post-file=$FILE http://www.alsa-project.org/cardinfo-db/ &>$TEMPDIR/wget.tmp &
else
    echo -n "Uploading information to www.pastebin.ca ... " 
    wget -O - --tries=5 --timeout=60 --post-file=$FILE http://pastebin.ca/quiet-paste.php?api=$PASTEBINKEY &>$TEMPDIR/wget.tmp &
fi

#Progess spinner for wget transfer.
i=1
sp="/-\|"
echo -n ' '
while pgrep wget &>/dev/null
do
    echo -en "\b${sp:i++%${#sp}:1}"
done

echo -e "\b Done!"
echo ""

fi #dialog

#See if tput is available, and use it if it is.    
if [[ -n "$TPUT" ]]
then
    if [[ -z $PASTEBIN ]]; then
        FINAL_URL=`tput setaf 1; grep "SUCCESS:" $TEMPDIR/wget.tmp | cut -d ' ' -f 2 ; tput sgr0`
    else
        FINAL_URL=`tput setaf 1; grep "SUCCESS:" $TEMPDIR/wget.tmp |sed -n 's/.*\:\([0-9]\+\).*/http:\/\/pastebin.ca\/\1/p';tput sgr0`
    fi
else
    if [[ -z $PASTEBIN ]]; then
        FINAL_URL=`grep "SUCCESS:" $TEMPDIR/wget.tmp | cut -d ' ' -f 2`
    else
        FINAL_URL=`grep "SUCCESS:" $TEMPDIR/wget.tmp |sed -n 's/.*\:\([0-9]\+\).*/http:\/\/pastebin.ca\/\1/p'`
    fi
fi

#Output the URL of the uploaded file.    
echo "Your ALSA information is located at $FINAL_URL"
echo "Please inform the person helping you."
echo ""

#We couldnt find a suitable wget, so tell the user to upload manually.
else
    mv -f $FILE $NFILE || exit 1
    KEEP_OUTPUT="yes"
    if [[ -z $DIALOG ]]
    then
        if [[ -z $PASTEBIN ]]; then
        echo ""
        echo "Could not automatically upload output to http://www.alsa-project.org"
        echo "Possible reasons are:"
        echo "    1. Couldnt find 'wget' in your PATH"
        echo "    2. Your version of wget is less than 1.8.2"
        echo ""
        echo "Please manually upload $NFILE to http://www.alsa-project.org/cardinfo-db/ and submit your post."
        echo ""
        else
        echo ""
        echo "Could not automatically upload output to http://www.pastebin.ca"
        echo "Possible reasons are:"
        echo "    1. Couldnt find 'wget' in your PATH"
        echo "    2. Your version of wget is less than 1.8.2"
        echo ""
        echo "Please manually upload $NFILE to http://www.pastebin.ca/upload.php and submit your post."
        echo ""
        fi
    else
        if [[ -z $PASTEBIN ]]; then
            dialog --backtitle "$BGTITLE" --msgbox "Could not automatically upload output to http://www.alsa-project.org.\nPossible reasons are:\n\n    1. Couldn't find 'wget' in your PATH\n    2. Your version of wget is less than 1.8.2\n\nPlease manually upload $NFILE to http://www.alsa-project,org/cardinfo-db/ and submit your post." 25 100
        else
            dialog --backtitle "$BGTITLE" --msgbox "Could not automatically upload output to http://www.pastebin.ca.\nPossible reasons are:\n\n    1. Couldn't find 'wget' in your PATH\n    2. Your version of wget is less than 1.8.2\n\nPlease manually upload $NFILE to http://www.pastebin.ca/upload.php and submit your post." 25 100
        fi
    fi
fi


```

---

### Post by Yellow Pasque on 2013-01-25
No, that's not the ALSA info. All you need to do is copy/paste the link the script gives you after running it (you copied/pasted the script itself).
Example of the link you should be given upon running the script: [http://www.alsa-project.org/db/?f=a36b80c9fb99340b1369246aa31c1e7d2fd2f91e](http://www.alsa-project.org/db/?f=a36b80c9fb99340b1369246aa31c1e7d2fd2f91e)

---

### Post by Simeo on 2013-01-25
> **Temüjin said:**
> No, that's not the ALSA info. All you need to do is copy/paste the link the script gives you after running it (you copied/pasted the script itself).
Example of the link you should be given upon running the script: [http://www.alsa-project.org/db/?f=a36b80c9fb99340b1369246aa31c1e7d2fd2f91e](http://www.alsa-project.org/db/?f=a36b80c9fb99340b1369246aa31c1e7d2fd2f91e)

When I ran the command "/usr/share/alsa-base/alsa-info.sh" as prompted in the link you provided all I received is a file with the code pasted above. No link was provided in the output of the terminal (unless I'm doing something wrong). Again, I'll input the command in terminal again and paste the output below so you'll see what I mean:

```
:~$ /usr/share/alsa-base/alsa-info.sh
ALSA Information Script v 0.4.60
--------------------------------

This script visits the following commands/files to collect diagnostic
information about your ALSA installation and sound related hardware.

  dmesg
  lspci
  lsmod
  aplay
  amixer
  alsactl
  /proc/asound/
  /sys/class/sound/
  ~/.asoundrc (etc.)

See '/usr/share/alsa-base/alsa-info.sh --help' for command line options.

Newer version detected: 0.4.61
To view the ChangeLog, please visit http://www.alsa-project.org/alsa-info.sh.changelog
ALSA-Info script has been downloaded /tmp/alsa-info.ZPQHyXfPNg.
Please, re-run it from new location.

```

The ALSA-Info script it says was downloaded pasted below (Ubuntu forums won't let me upload as attachment)

Filename: alsa-info.ZPQHyXfPNg
```
#!/bin/bash

SCRIPT_VERSION=0.4.61
CHANGELOG="http://www.alsa-project.org/alsa-info.sh.changelog"

#################################################################################
#Copyright (C) 2007 Free Software Foundation.

#This program is free software; you can redistribute it and/or modify
#it under the terms of the GNU General Public License as published by
#the Free Software Foundation; either version 2 of the License, or
#(at your option) any later version.

#This program is distributed in the hope that it will be useful,
#but WITHOUT ANY WARRANTY; without even the implied warranty of
#MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
#GNU General Public License for more details.

#You should have received a copy of the GNU General Public License
#along with this program; if not, write to the Free Software
#Foundation, Inc., 51 Franklin Street, Fifth Floor, Boston, MA  02110-1301, USA.

##################################################################################

#The script was written for 2 main reasons:
# 1. Remove the need for the devs/helpers to ask several questions before we can easily help the user.
# 2. Allow newer/inexperienced ALSA users to give us all the info we need to help them.

#Set the locale (this may or may not be a good idea.. let me know)
export LC_ALL=C

#Change the PATH variable, so we can run lspci (needed for some distros)
PATH=$PATH:/bin:/sbin:/usr/bin:/usr/sbin
BGTITLE="ALSA-Info v $SCRIPT_VERSION"
PASTEBINKEY="C9cRIO8m/9y8Cs0nVs0FraRx7U0pHsuc"
#Define some simple functions

pbcheck(){
    [[ $UPLOAD = "no" ]] && return

    if [[ -z $PASTEBIN ]]; then
        [[ $(ping -c1 www.alsa-project.org) ]] || KEEP_FILES="yes" UPLOAD="no" PBERROR="yes"
    else
        [[ $(ping -c1 www.pastebin.ca) ]] || KEEP_FILES="yes" UPLOAD="no" PBERROR="yes"
    fi
}

update() {
    SHFILE=`mktemp -t alsa-info.XXXXXXXXXX` || exit 1
    wget -O $SHFILE "http://www.alsa-project.org/alsa-info.sh" >/dev/null 2>&1
    REMOTE_VERSION=`grep SCRIPT_VERSION $SHFILE |head -n1 |sed 's/.*=//'`
    if [ "$REMOTE_VERSION" != "$SCRIPT_VERSION" ]; then
        if [[ -n $DIALOG ]]
        then
            OVERWRITE=
            if [ -w $0 ]; then
                dialog --yesno "Newer version of ALSA-Info has been found\n\nDo you wish to install it?\nNOTICE: The original file $0 will be overwritten!" 0 0
                DIALOG_EXIT_CODE=$?
                if [[ $DIALOG_EXIT_CODE = 0 ]]; then
                  OVERWRITE=yes
                fi
            fi
            if [ -z "$OVERWRITE" ]; then
                dialog --yesno "Newer version of ALSA-Info has been found\n\nDo you wish to download it?" 0 0
                DIALOG_EXIT_CODE=$?
            fi
            if [[ $DIALOG_EXIT_CODE = 0 ]]
            then
                echo "Newer version detected: $REMOTE_VERSION"
                echo "To view the ChangeLog, please visit $CHANGELOG"
                if [ "$OVERWRITE" = "yes" ]; then
                    cp $SHFILE $0
                    echo "ALSA-Info script has been updated to v $REMOTE_VERSION"
                    echo "Please re-run the script"
                    rm $SHFILE 2>/dev/null
                else
                    echo "ALSA-Info script has been downloaded as $SHFILE."
                    echo "Please re-run the script from new location."
                fi
                exit
            else
                rm $SHFILE 2>/dev/null
            fi
        else
            echo "Newer version detected: $REMOTE_VERSION"
            echo "To view the ChangeLog, please visit $CHANGELOG"
            if [ -w $0 ]; then
                echo "The original file $0 will be overwritten!"
                echo -n "If you do not like to proceed, press Ctrl-C now.." ; read inp
                cp $SHFILE $0
                echo "ALSA-Info script has been updated. Please re-run it."
                rm $SHFILE 2>/dev/null
            else
                echo "ALSA-Info script has been downloaded $SHFILE."
                echo "Please, re-run it from new location."
            fi
            exit
        fi
    else
        rm $SHFILE 2>/dev/null
    fi
}

cleanup() {
    if [ -n "$TEMPDIR" -a "$KEEP_FILES" != "yes" ]; then
        rm -rf "$TEMPDIR" 2>/dev/null
    fi
    test -n "$KEEP_OUTPUT" || rm -f "$NFILE"
}


withaplay() {
        echo "!!Aplay/Arecord output" >> $FILE
        echo "!!--------------------" >> $FILE
        echo "" >> $FILE
           echo "APLAY" >> $FILE
    echo "" >> $FILE 
    aplay -l >> $FILE 2>&1
        echo "" >> $FILE
           echo "ARECORD" >> $FILE
    echo "" >> $FILE
    arecord -l >> $FILE 2>&1
    echo "" >> $FILE
}

withlsmod() {
    echo "!!All Loaded Modules" >> $FILE
    echo "!!------------------" >> $FILE
    echo "" >> $FILE
    lsmod |awk {'print $1'} >> $FILE
    echo "" >> $FILE
    echo "" >> $FILE
}

withamixer() {
        echo "!!Amixer output" >> $FILE
        echo "!!-------------" >> $FILE
        echo "" >> $FILE
    for i in `grep "]: " /proc/asound/cards | awk -F ' ' '{ print $1} '` ; do
    CARD_NAME=`grep "^ *$i " $TEMPDIR/alsacards.tmp|awk {'print $2'}`
    echo "!!-------Mixer controls for card $i $CARD_NAME]" >> $FILE
    echo "" >>$FILE
    amixer -c$i info>> $FILE 2>&1
    amixer -c$i>> $FILE 2>&1
        echo "" >> $FILE
    done
    echo "" >> $FILE
}

withalsactl() {
    echo "!!Alsactl output" >> $FILE
        echo "!!--------------" >> $FILE
        echo "" >> $FILE
        exe=""
        if [ -x /usr/sbin/alsactl ]; then
            exe="/usr/sbin/alsactl"
        fi
        if [ -x /usr/local/sbin/alsactl ]; then
            exe="/usr/local/sbin/alsactl"
        fi
        if [ -z "$exe" ]; then
            exe=`whereis alsactl | cut -d ' ' -f 2`
        fi
    $exe -f $TEMPDIR/alsactl.tmp store
    echo "--startcollapse--" >> $FILE
    cat $TEMPDIR/alsactl.tmp >> $FILE
    echo "--endcollapse--" >> $FILE
    echo "" >> $FILE
    echo "" >> $FILE
}

withdevices() {
        echo "!!ALSA Device nodes" >> $FILE
        echo "!!-----------------" >> $FILE
        echo "" >> $FILE
        ls -la /dev/snd/* >> $FILE
        echo "" >> $FILE
        echo "" >> $FILE
}

withconfigs() {
if [[ -e $HOME/.asoundrc ]] || [[ -e /etc/asound.conf ]] || [[ -e $HOME/.asoundrc.asoundconf ]]
then
        echo "!!ALSA configuration files" >> $FILE
        echo "!!------------------------" >> $FILE
        echo "" >> $FILE

        #Check for ~/.asoundrc
        if [[ -e $HOME/.asoundrc ]]
        then
                echo "!!User specific config file (~/.asoundrc)" >> $FILE
                echo "" >> $FILE
                cat $HOME/.asoundrc >> $FILE
                echo "" >> $FILE
                echo "" >> $FILE
        fi
    #Check for .asoundrc.asoundconf (seems to be Ubuntu specific)
    if [[ -e $HOME/.asoundrc.asoundconf ]]
    then
        echo "!!asoundconf-generated config file" >> $FILE
        echo "" >> $FILE
        cat $HOME/.asoundrc.asoundconf >> $FILE
        echo "" >> $FILE
        echo "" >> $FILE
    fi
        #Check for /etc/asound.conf
        if [[ -e /etc/asound.conf ]]
        then
                echo "!!System wide config file (/etc/asound.conf)" >> $FILE
                echo "" >> $FILE
                cat /etc/asound.conf >> $FILE
                echo "" >> $FILE
                echo "" >> $FILE
        fi
fi
}

withsysfs() {
    local i f
    local printed=""
    for i in /sys/class/sound/*; do
    case "$i" in
        */hwC?D?)
        if [ -f $i/init_pin_configs ]; then
            if [ -z "$printed" ]; then
            echo "!!Sysfs Files" >> $FILE
            echo "!!-----------" >> $FILE
            echo "" >> $FILE
            fi
            for f in init_pin_configs driver_pin_configs user_pin_configs init_verbs; do
            echo "$i/$f:" >> $FILE
            cat $i/$f >> $FILE
            echo >> $FILE
            done
            printed=yes
        fi
        ;;
        esac
    done
    if [ -n "$printed" ]; then
    echo "" >> $FILE
    fi
}

withdmesg() {
    echo "!!ALSA/HDA dmesg" >> $FILE
    echo "!!--------------" >> $FILE
    echo "" >> $FILE
    dmesg | grep -C1 -E 'ALSA|HDA|HDMI|sound|hda.codec|hda.intel' >> $FILE
    echo "" >> $FILE
    echo "" >> $FILE
}

withall() {
    withdevices
    withconfigs
    withaplay
    withamixer
    withalsactl
    withlsmod
    withsysfs
    withdmesg
}

get_alsa_library_version() {
    ALSA_LIB_VERSION=`grep VERSION_STR /usr/include/alsa/version.h 2>/dev/null|awk {'print $3'}|sed 's/"//g'`

    if [ -z "$ALSA_LIB_VERSION" ]; then
        if [ -f /etc/lsb-release ]; then
            . /etc/lsb-release
            case "$DISTRIB_ID" in
                Ubuntu)
                    if which dpkg > /dev/null ; then
                        ALSA_LIB_VERSION=`dpkg -l libasound2 | tail -1 | awk '{print $3}' | cut -f 1 -d -`
                    fi

                    if [ "$ALSA_LIB_VERSION" = "<none>" ]; then
                        ALSA_LIB_VERSION=""
                    fi
                    return
                    ;;
                *)
                    return
                    ;;
            esac
        elif [ -f /etc/debian_version ]; then
            if which dpkg > /dev/null ; then
                ALSA_LIB_VERSION=`dpkg -l libasound2 | tail -1 | awk '{print $3}' | cut -f 1 -d -`
            fi

            if [ "$ALSA_LIB_VERSION" = "<none>" ]; then
                ALSA_LIB_VERSION=""
            fi
            return
        fi
    fi
}


#Run checks to make sure the programs we need are installed.
LSPCI=$(which lspci 2>/dev/null| sed 's|^[^/]*||' 2>/dev/null);
TPUT=$(which tput 2>/dev/null| sed 's|^[^/]*||' 2>/dev/null);
DIALOG=$(which dialog 2>/dev/null | sed 's|^[^/]*||' 2>/dev/null);

#Check to see if sysfs is enabled in the kernel. We'll need this later on
SYSFS=$(mount |grep sysfs|awk {'print $3'});

#Check modprobe config files for sound related options
SNDOPTIONS=$(modprobe -c|sed -n 's/^options \(snd[-_][^ ]*\)/\1:/p')

KEEP_OUTPUT=
NFILE=""

PASTEBIN=""
WWWSERVICE="www.alsa-project.org"
WELCOME="yes"
PROCEED="yes"
UPLOAD="ask"
REPEAT=""
while [ -z "$REPEAT" ]; do
REPEAT="no"
case "$1" in
    --update|--help|--about)
        WELCOME="no"
        PROCEED="no"
        ;;
    --upload)
        UPLOAD="yes"
        WELCOME="no"
        ;;
    --no-upload)
        UPLOAD="no"
        WELCOME="no"
        ;;
    --pastebin)
        PASTEBIN="yes"
        WWWSERVICE="pastebin"
        ;;
    --no-dialog)
        DIALOG=""
        REPEAT=""
        shift
        ;;
    --stdout)
        DIALOG=""
        UPLOAD="no"
        WELCOME="no"
        TOSTDOUT="yes"
        ;;
esac
done


#Script header output.
if [ "$WELCOME" = "yes" ]; then
greeting_message="\

This script visits the following commands/files to collect diagnostic
information about your ALSA installation and sound related hardware.

  dmesg
  lspci
  lsmod
  aplay
  amixer
  alsactl
  /proc/asound/
  /sys/class/sound/
  ~/.asoundrc (etc.)

See '$0 --help' for command line options.
"
if [[ -n "$DIALOG" ]]; then
    dialog  --backtitle "$BGTITLE" \
        --title "ALSA-Info script v $SCRIPT_VERSION" \
        --msgbox "$greeting_message" 20 80
else
    echo "ALSA Information Script v $SCRIPT_VERSION"
    echo "--------------------------------"
    echo "$greeting_message"
fi # dialog
fi # WELCOME

#Set the output file
TEMPDIR=`mktemp -t -d alsa-info.XXXXXXXXXX` || exit 1
FILE="$TEMPDIR/alsa-info.txt"
if [ -z "$NFILE" ]; then
    NFILE=`mktemp -t alsa-info.txt.XXXXXXXXXX` || exit 1
fi

trap cleanup 0

if [ "$PROCEED" = "yes" ]; then

if [[ -z "$LSPCI" ]] 
then
    echo "This script requires lspci. Please install it, and re-run this script."
    exit 0
fi

#Fetch the info and store in temp files/variables
DISTRO=`grep -ihs "buntu\|SUSE\|Fedora\|PCLinuxOS\|MEPIS\|Mandriva\|Debian\|Damn\|Sabayon\|Slackware\|KNOPPIX\|Gentoo\|Zenwalk\|Mint\|Kubuntu\|FreeBSD\|Puppy\|Freespire\|Vector\|Dreamlinux\|CentOS\|Arch\|Xandros\|Elive\|SLAX\|Red\|BSD\|KANOTIX\|Nexenta\|Foresight\|GeeXboX\|Frugalware\|64\|SystemRescue\|Novell\|Solaris\|BackTrack\|KateOS\|Pardus" /etc/{issue,*release,*version}`
KERNEL_VERSION=`uname -r`
KERNEL_PROCESSOR=`uname -p`
KERNEL_MACHINE=`uname -m`
KERNEL_OS=`uname -o`
[[ `uname -v |grep SMP`  ]] && KERNEL_SMP="Yes" || KERNEL_SMP="No" 
ALSA_DRIVER_VERSION=`cat /proc/asound/version |head -n1|awk {'print $7'} |sed 's/\.$//'`
get_alsa_library_version
ALSA_UTILS_VERSION=`amixer -v |awk {'print $3'}`
VENDOR_ID=`lspci -vn |grep 040[1-3] | awk -F':' '{print $3}'|awk {'print substr($0, 2);}' >$TEMPDIR/vendor_id.tmp`
DEVICE_ID=`lspci -vn |grep 040[1-3] | awk -F':' '{print $4}'|awk {'print $1'} >$TEMPDIR/device_id.tmp`
LAST_CARD=$((`grep "]: " /proc/asound/cards | wc -l` - 1 ))

ESDINST=$(which esd 2>/dev/null| sed 's|^[^/]*||' 2>/dev/null)
PAINST=$(which pulseaudio 2>/dev/null| sed 's|^[^/]*||' 2>/dev/null)
ARTSINST=$(which artsd 2>/dev/null| sed 's|^[^/]*||' 2>/dev/null)
JACKINST=$(which jackd 2>/dev/null| sed 's|^[^/]*||' 2>/dev/null)
ROARINST=$(which roard 2>/dev/null| sed 's|^[^/]*||' 2>/dev/null)
DMIDECODE=$(which dmidecode 2>/dev/null| sed 's|^[^/]*||' 2>/dev/null)

#Check for DMI data
if [ -d /sys/class/dmi/id ]; then
    # No root privileges are required when using sysfs method
    DMI_SYSTEM_MANUFACTURER=$(cat /sys/class/dmi/id/sys_vendor 2>/dev/null)
    DMI_SYSTEM_PRODUCT_NAME=$(cat /sys/class/dmi/id/product_name 2>/dev/null)
    DMI_SYSTEM_PRODUCT_VERSION=$(cat /sys/class/dmi/id/product_version 2>/dev/null)
    DMI_SYSTEM_FIRMWARE_VERSION=$(cat /sys/class/dmi/id/bios_version 2>/dev/null)
elif [ -x $DMIDECODE ]; then
    DMI_SYSTEM_MANUFACTURER=$($DMIDECODE -s system-manufacturer 2>/dev/null)
    DMI_SYSTEM_PRODUCT_NAME=$($DMIDECODE -s system-product-name 2>/dev/null)
    DMI_SYSTEM_PRODUCT_VERSION=$($DMIDECODE -s system-version 2>/dev/null)
    DMI_SYSTEM_FIRMWARE_VERSION=$($DMIDECODE -s bios-version 2>/dev/null)
fi

cat /proc/asound/modules 2>/dev/null|awk {'print $2'}>$TEMPDIR/alsamodules.tmp
cat /proc/asound/cards >$TEMPDIR/alsacards.tmp
lspci |grep -i "multi\|audio">$TEMPDIR/lspci.tmp

#Check for HDA-Intel cards codec#*
cat /proc/asound/card*/codec\#* > $TEMPDIR/alsa-hda-intel.tmp 2> /dev/null

#Check for AC97 cards codec
cat /proc/asound/card*/codec97\#0/ac97\#0-0 > $TEMPDIR/alsa-ac97.tmp 2> /dev/null
cat /proc/asound/card*/codec97\#0/ac97\#0-0+regs > $TEMPDIR/alsa-ac97-regs.tmp 2> /dev/null

#Check for USB mixer setup
cat /proc/asound/card*/usbmixer > $TEMPDIR/alsa-usbmixer.tmp 2> /dev/null

#Fetch the info, and put it in $FILE in a nice readable format.
if [[ -z $PASTEBIN ]]; then
echo "upload=true&script=true&cardinfo=" > $FILE
else
echo "name=$USER&type=33&description=/tmp/alsa-info.txt&expiry=&s=Submit+Post&content=" > $FILE
fi
echo "!!################################" >> $FILE
echo "!!ALSA Information Script v $SCRIPT_VERSION" >> $FILE
echo "!!################################" >> $FILE
echo "" >> $FILE
echo "!!Script ran on: `LANG=C TZ=UTC date`" >> $FILE
echo "" >> $FILE
echo "" >> $FILE
echo "!!Linux Distribution" >> $FILE
echo "!!------------------" >> $FILE
echo "" >> $FILE
echo $DISTRO >> $FILE
echo "" >> $FILE
echo "" >> $FILE
echo "!!DMI Information" >> $FILE
echo "!!---------------" >> $FILE
echo "" >> $FILE
echo "Manufacturer:      $DMI_SYSTEM_MANUFACTURER" >> $FILE
echo "Product Name:      $DMI_SYSTEM_PRODUCT_NAME" >> $FILE
echo "Product Version:   $DMI_SYSTEM_PRODUCT_VERSION" >> $FILE
echo "Firmware Version:  $DMI_SYSTEM_FIRMWARE_VERSION" >> $FILE
echo "" >> $FILE
echo "" >> $FILE
echo "!!Kernel Information" >> $FILE
echo "!!------------------" >> $FILE
echo "" >> $FILE
echo "Kernel release:    $KERNEL_VERSION" >> $FILE
echo "Operating System:  $KERNEL_OS" >> $FILE
echo "Architecture:      $KERNEL_MACHINE" >> $FILE
echo "Processor:         $KERNEL_PROCESSOR" >> $FILE
echo "SMP Enabled:       $KERNEL_SMP" >> $FILE
echo "" >> $FILE
echo "" >> $FILE
echo "!!ALSA Version" >> $FILE
echo "!!------------" >> $FILE
echo "" >> $FILE
echo "Driver version:     $ALSA_DRIVER_VERSION" >> $FILE
echo "Library version:    $ALSA_LIB_VERSION" >> $FILE
echo "Utilities version:  $ALSA_UTILS_VERSION" >> $FILE
echo "" >> $FILE
echo "" >> $FILE
echo "!!Loaded ALSA modules" >> $FILE
echo "!!-------------------" >> $FILE
echo "" >> $FILE
cat $TEMPDIR/alsamodules.tmp >> $FILE
echo "" >> $FILE
echo "" >> $FILE
echo "!!Sound Servers on this system" >> $FILE
echo "!!----------------------------" >> $FILE
echo "" >> $FILE
if [[ -n $PAINST ]];then
[[ `pgrep '^(.*/)?pulseaudio$'` ]] && PARUNNING="Yes" || PARUNNING="No"
echo "Pulseaudio:" >> $FILE
echo "      Installed - Yes ($PAINST)" >> $FILE
echo "      Running - $PARUNNING" >> $FILE
echo "" >> $FILE
fi
if [[ -n $ESDINST ]];then
[[ `pgrep '^(.*/)?esd$'` ]] && ESDRUNNING="Yes" || ESDRUNNING="No"
echo "ESound Daemon:" >> $FILE
echo "      Installed - Yes ($ESDINST)" >> $FILE
echo "      Running - $ESDRUNNING" >> $FILE
echo "" >> $FILE
fi
if [[ -n $ARTSINST ]];then
[[ `pgrep '^(.*/)?artsd$'` ]] && ARTSRUNNING="Yes" || ARTSRUNNING="No"
echo "aRts:" >> $FILE
echo "      Installed - Yes ($ARTSINST)" >> $FILE
echo "      Running - $ARTSRUNNING" >> $FILE
echo "" >> $FILE
fi
if [[ -n $JACKINST ]];then
[[ `pgrep '^(.*/)?jackd$'` ]] && JACKRUNNING="Yes" || JACKRUNNING="No"
echo "Jack:" >> $FILE
echo "      Installed - Yes ($JACKINST)" >> $FILE
echo "      Running - $JACKRUNNING" >> $FILE
echo "" >> $FILE
fi
if [[ -n $ROARINST ]];then
[[ `pgrep '^(.*/)?roard$'` ]] && ROARRUNNING="Yes" || ROARRUNNING="No"
echo "RoarAudio:" >> $FILE
echo "      Installed - Yes ($ROARINST)" >> $FILE
echo "      Running - $ROARRUNNING" >> $FILE
echo "" >> $FILE
fi
if [[ -z "$PAINST" && -z "$ESDINST" && -z "$ARTSINST" && -z "$JACKINST" && -z "$ROARINST" ]];then
echo "No sound servers found." >> $FILE
echo "" >> $FILE
fi
echo "" >> $FILE
echo "!!Soundcards recognised by ALSA" >> $FILE
echo "!!-----------------------------" >> $FILE
echo "" >> $FILE
cat $TEMPDIR/alsacards.tmp >> $FILE
echo "" >> $FILE
echo "" >> $FILE
echo "!!PCI Soundcards installed in the system" >> $FILE
echo "!!--------------------------------------" >> $FILE
echo "" >> $FILE
cat $TEMPDIR/lspci.tmp >> $FILE
echo "" >> $FILE
echo "" >> $FILE
echo "!!Advanced information - PCI Vendor/Device/Subsystem ID's" >> $FILE
echo "!!-------------------------------------------------------" >> $FILE
echo "" >> $FILE
lspci -vvn |grep -A1 040[1-3] >> $FILE
echo "" >> $FILE
echo "" >> $FILE

if [ "$SNDOPTIONS" ]
then
echo "!!Modprobe options (Sound related)" >> $FILE
echo "!!--------------------------------" >> $FILE
echo "" >> $FILE
modprobe -c|sed -n 's/^options \(snd[-_][^ ]*\)/\1:/p' >> $FILE
echo "" >> $FILE
echo "" >> $FILE
fi

if [ -d "$SYSFS" ]
then
echo "!!Loaded sound module options" >> $FILE
echo "!!---------------------------" >> $FILE
echo "" >> $FILE
for mod in `cat /proc/asound/modules|awk {'print $2'}`;do
echo "!!Module: $mod" >> $FILE
for params in `echo $SYSFS/module/$mod/parameters/*`; do
    echo -ne "\t";
    echo "$params : `cat $params`" | sed 's:.*/::';
done >> $FILE
echo "" >> $FILE
done
echo "" >> $FILE
fi

if [ -s "$TEMPDIR/alsa-hda-intel.tmp" ] 
then
    echo "!!HDA-Intel Codec information" >> $FILE
    echo "!!---------------------------" >> $FILE
    echo "--startcollapse--" >> $FILE
    echo "" >> $FILE
    cat $TEMPDIR/alsa-hda-intel.tmp >> $FILE
    echo "--endcollapse--" >> $FILE
    echo "" >> $FILE
    echo "" >> $FILE
fi

if [ -s "$TEMPDIR/alsa-ac97.tmp" ]
then
        echo "!!AC97 Codec information" >> $FILE
        echo "!!----------------------" >> $FILE
        echo "--startcollapse--" >> $FILE
        echo "" >> $FILE
        cat $TEMPDIR/alsa-ac97.tmp >> $FILE
        echo "" >> $FILE
        cat $TEMPDIR/alsa-ac97-regs.tmp >> $FILE
        echo "--endcollapse--" >> $FILE
    echo "" >> $FILE
    echo "" >> $FILE
fi

if [ -s "$TEMPDIR/alsa-usbmixer.tmp" ]
then
        echo "!!USB Mixer information" >> $FILE
        echo "!!---------------------" >> $FILE
        echo "--startcollapse--" >> $FILE
        echo "" >> $FILE
        cat $TEMPDIR/alsa-usbmixer.tmp >> $FILE
        echo "--endcollapse--" >> $FILE
    echo "" >> $FILE
    echo "" >> $FILE
fi

#If no command line options are specified, then run as though --with-all was specified
if [[ -z "$1" ]]
then
    update
    withall
    pbcheck    
fi

fi # proceed

#loop through command line arguments, until none are left.
if [[ -n "$1" ]]
then
    until [ -z "$1" ]
    do
    case "$1" in
        --pastebin)
                update
            withall
                pbcheck
            ;;
        --update)
            update
            exit
            ;;
        --upload)
            UPLOAD="yes"
            withall
            ;;
        --no-upload)
            UPLOAD="no"
            withall
            ;;
        --output)
            shift
            NFILE="$1"
            KEEP_OUTPUT="yes"
            ;;
        --debug)
            echo "Debugging enabled. $FILE and $TEMPDIR will not be deleted"
            KEEP_FILES="yes"
            echo ""
            withall
            ;;
        --with-all)
            withall
            ;;
        --with-aplay)
            withaplay
            ;;
        --with-amixer)
            withamixer
            ;;
        --with-alsactl)
            withalsactl
            ;;
        --with-devices)
            withdevices
            ;;
        --with-dmesg)
            withdmesg
            ;;
        --with-configs)
            if [[ -e $HOME/.asoundrc ]] || [[ -e /etc/asound.conf ]]
            then
                echo "!!ALSA configuration files" >> $FILE
                echo "!!------------------------" >> $FILE
                echo "" >> $FILE

                #Check for ~/.asoundrc
                if [[ -e $HOME/.asoundrc ]]
                then
                    echo "!!User specific config file ($HOME/.asoundrc)" >> $FILE
                    echo "" >> $FILE
                    cat $HOME/.asoundrc >> $FILE
                    echo "" >> $FILE
                    echo "" >> $FILE
                fi

                #Check for /etc/asound.conf
                if [[ -e /etc/asound.conf ]]
                then
                    echo "!!System wide config file (/etc/asound.conf)" >> $FILE
                    echo "" >> $FILE
                    cat /etc/asound.conf >> $FILE
                    echo "" >> $FILE
                    echo "" >> $FILE
                fi
            fi
            ;;
        --stdout)
            UPLOAD="no"
            withall
            cat $FILE
            rm $FILE
            ;;
        --about)
            echo "Written/Tested by the following users of #alsa on irc.freenode.net:"
            echo ""
            echo "    wishie - Script author and developer / Testing"
            echo "    crimsun - Various script ideas / Testing"
            echo "    gnubien - Various script ideas / Testing"
            echo "    GrueMaster - HDA Intel specific items / Testing"
            echo "    olegfink - Script update function"
            echo "  TheMuso - display to stdout functionality"
            exit 0
            ;;
        *)
            echo "alsa-info.sh version $SCRIPT_VERSION"
            echo ""
            echo "Available options:"
            echo "    --with-aplay (includes the output of aplay -l)"
            echo "    --with-amixer (includes the output of amixer)"
            echo "    --with-alsactl (includes the output of alsactl)"
            echo "    --with-configs (includes the output of ~/.asoundrc and"
            echo "        /etc/asound.conf if they exist)" 
            echo "    --with-devices (shows the device nodes in /dev/snd/)"
            echo "    --with-dmesg (shows the ALSA/HDA kernel messages)"
            echo ""
            echo "    --output FILE (specify the file to output for no-upload mode)"
            echo "    --update (check server for script updates)"
            echo "    --upload (upload contents to remote server)"
            echo "    --no-upload (do not upload contents to remote server)"
            echo "    --pastebin (use http://pastebin.ca) as remote server"
            echo "        instead www.alsa-project.org"
            echo "    --stdout (print alsa information to standard output"
            echo "        instead of a file)"
            echo "    --about (show some information about the script)"
            echo "    --debug (will run the script as normal, but will not"
            echo "         delete $FILE)"
            exit 0
            ;;
    esac
    shift 1
    done
fi

if [ "$PROCEED" = "no" ]; then
    exit 1
fi

if [ "$UPLOAD" = "ask" ]; then
    if [[ -n "$DIALOG" ]]; then
        dialog --backtitle "$BGTITLE" --title "Information collected" --yes-label " UPLOAD / SHARE " --no-label " SAVE LOCALLY " --defaultno --yesno "\n\nAutomatically upload ALSA information to $WWWSERVICE?" 10 80
        DIALOG_EXIT_CODE=$?
        if [ $DIALOG_EXIT_CODE != 0 ]; then
            UPLOAD="no"
        else
            UPLOAD="yes"
        fi
    else
        echo -n "Automatically upload ALSA information to $WWWSERVICE? [y/N] : "
        read -e CONFIRM
        if [ "$CONFIRM" != "y" ]; then
            UPLOAD="no"
        else
            UPLOAD="yes"
        fi
    fi

fi

if [ "$UPLOAD" = "no" ]; then

    if [ -z "$TOSTDOUT" ]; then
        mv -f $FILE $NFILE || exit 1
        KEEP_OUTPUT="yes"
    fi

    if [[ -n $DIALOG ]]
    then
        if [[ -n $PBERROR ]]; then
            dialog --backtitle "$BGTITLE" --title "Information collected" --msgbox "An error occurred while contacting the $WWWSERVICE.\n Your information was NOT automatically uploaded.\n\nYour ALSA information is in $NFILE" 10 100
        else
            dialog --backtitle "$BGTITLE" --title "Information collected" --msgbox "\n\nYour ALSA information is in $NFILE" 10 60
        fi
    else
        echo

        if [[ -n $PBERROR ]]; then
            echo "An error occurred while contacting the $WWWSERVICE."
            echo "Your information was NOT automatically uploaded."
            echo ""
            echo "Your ALSA information is in $NFILE"
            echo ""
        else
            if [ -z "$TOSTDOUT" ]; then
                echo ""
                echo "Your ALSA information is in $NFILE"
                echo ""
            fi
        fi
    fi

    exit

fi # UPLOAD

#Test that wget is installed, and supports --post-file. Upload $FILE if it does, and prompt user to upload file if it doesnt. 
if
WGET=$(which wget 2>/dev/null| sed 's|^[^/]*||' 2>/dev/null); [[ -n "${WGET}" ]] && [[ -x "${WGET}" ]] && [[ `wget --help |grep post-file` ]]
then

if [[ -n $DIALOG ]]
then

if [[ -z $PASTEBIN ]]; then
    wget -O - --tries=5 --timeout=60 --post-file=$FILE "http://www.alsa-project.org/cardinfo-db/" &>$TEMPDIR/wget.tmp || echo "Upload failed; exit"
    { for i in 10 20 30 40 50 60 70 80 90; do
        echo $i
        sleep 0.2
    done
    echo; } |dialog --backtitle "$BGTITLE" --guage "Uploading information to www.alsa-project.org ..." 6 70 0
else
    wget -O - --tries=5 --timeout=60 --post-file=$FILE "http://pastebin.ca/quiet-paste.php?api=$PASTEBINKEY&encrypt=t&encryptpw=blahblah" &>$TEMPDIR/wget.tmp || echo "Upload failed; exit"
    { for i in 10 20 30 40 50 60 70 80 90; do
        echo $i
        sleep 0.2
    done
    echo; } |dialog --backtitle "$BGTITLE" --guage "Uploading information to www.pastebin.ca ..." 6 70 0
fi

dialog --backtitle "$BGTITLE" --title "Information uploaded" --yesno "Would you like to see the uploaded information?" 5 100 
DIALOG_EXIT_CODE=$?
if [ $DIALOG_EXIT_CODE = 0 ]; then
    grep -v "alsa-info.txt" $FILE >$TEMPDIR/uploaded.txt
    dialog --backtitle "$BGTITLE" --textbox $TEMPDIR/uploaded.txt 0 0
fi

clear

# no dialog
else

if [[ -z $PASTEBIN ]]; then
    echo -n "Uploading information to www.alsa-project.org ... " 
    wget -O - --tries=5 --timeout=60 --post-file=$FILE http://www.alsa-project.org/cardinfo-db/ &>$TEMPDIR/wget.tmp &
else
    echo -n "Uploading information to www.pastebin.ca ... " 
    wget -O - --tries=5 --timeout=60 --post-file=$FILE http://pastebin.ca/quiet-paste.php?api=$PASTEBINKEY &>$TEMPDIR/wget.tmp &
fi

#Progess spinner for wget transfer.
i=1
sp="/-\|"
echo -n ' '
while pgrep wget &>/dev/null
do
    echo -en "\b${sp:i++%${#sp}:1}"
done

echo -e "\b Done!"
echo ""

fi #dialog

#See if tput is available, and use it if it is.    
if [[ -n "$TPUT" ]]
then
    if [[ -z $PASTEBIN ]]; then
        FINAL_URL=`tput setaf 1; grep "SUCCESS:" $TEMPDIR/wget.tmp | cut -d ' ' -f 2 ; tput sgr0`
    else
        FINAL_URL=`tput setaf 1; grep "SUCCESS:" $TEMPDIR/wget.tmp |sed -n 's/.*\:\([0-9]\+\).*/http:\/\/pastebin.ca\/\1/p';tput sgr0`
    fi
else
    if [[ -z $PASTEBIN ]]; then
        FINAL_URL=`grep "SUCCESS:" $TEMPDIR/wget.tmp | cut -d ' ' -f 2`
    else
        FINAL_URL=`grep "SUCCESS:" $TEMPDIR/wget.tmp |sed -n 's/.*\:\([0-9]\+\).*/http:\/\/pastebin.ca\/\1/p'`
    fi
fi

#Output the URL of the uploaded file.    
echo "Your ALSA information is located at $FINAL_URL"
echo "Please inform the person helping you."
echo ""

#We couldnt find a suitable wget, so tell the user to upload manually.
else
    mv -f $FILE $NFILE || exit 1
    KEEP_OUTPUT="yes"
    if [[ -z $DIALOG ]]
    then
        if [[ -z $PASTEBIN ]]; then
        echo ""
        echo "Could not automatically upload output to http://www.alsa-project.org"
        echo "Possible reasons are:"
        echo "    1. Couldnt find 'wget' in your PATH"
        echo "    2. Your version of wget is less than 1.8.2"
        echo ""
        echo "Please manually upload $NFILE to http://www.alsa-project.org/cardinfo-db/ and submit your post."
        echo ""
        else
        echo ""
        echo "Could not automatically upload output to http://www.pastebin.ca"
        echo "Possible reasons are:"
        echo "    1. Couldnt find 'wget' in your PATH"
        echo "    2. Your version of wget is less than 1.8.2"
        echo ""
        echo "Please manually upload $NFILE to http://www.pastebin.ca/upload.php and submit your post."
        echo ""
        fi
    else
        if [[ -z $PASTEBIN ]]; then
            dialog --backtitle "$BGTITLE" --msgbox "Could not automatically upload output to http://www.alsa-project.org.\nPossible reasons are:\n\n    1. Couldn't find 'wget' in your PATH\n    2. Your version of wget is less than 1.8.2\n\nPlease manually upload $NFILE to http://www.alsa-project,org/cardinfo-db/ and submit your post." 25 100
        else
            dialog --backtitle "$BGTITLE" --msgbox "Could not automatically upload output to http://www.pastebin.ca.\nPossible reasons are:\n\n    1. Couldn't find 'wget' in your PATH\n    2. Your version of wget is less than 1.8.2\n\nPlease manually upload $NFILE to http://www.pastebin.ca/upload.php and submit your post." 25 100
        fi
    fi
fi


```

---

### Post by Yellow Pasque on 2013-01-25
Hmm. It looks like Ubuntu 12.10 contains an outdated version of the script and it's prompting you to run the newer version. Use the alternate method (for Ubuntu 12.04 and earlier).
```
cd ~/
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh
```

---

### Post by Simeo on 2013-01-25
> **Temüjin said:**
> Hmm. It looks like Ubuntu 12.10 contains an outdated version of the script and it's prompting you to run the newer version. Use the alternate method (for Ubuntu 12.04 and earlier).
```
cd ~/
wget http://www.alsa-project.org/alsa-info.sh -O alsa-info.sh && bash alsa-info.sh
```

Yep, that's what was happening. Here's the link: [http://www.alsa-project.org/db/?f=fe411a6f37a2b769918cf0e90c555fb4c79878ee](http://www.alsa-project.org/db/?f=fe411a6f37a2b769918cf0e90c555fb4c79878ee)

---

### Post by AgentZ86 on 2013-01-25
Can you please check this

-Right click little speaker in upper right corner of ubuntu
-Select sound settings
-make sure the correct output device is selected
Test

I have a wireless headset and sometimes when I boot to ubuntu after booting to windows 7 it defaults to the incorrect output

I don't know if that will help but the list shows your output devices and you want to make sure the correct one is selected

If your not plugging your headset into the actual headset connection then you need to select analgue audio built in audio or something like that

Because even though you may be using the headset connection it may not actually be a headset connection but just an extended jack for the non-powered speaker connection like line out or something

Anyhow check that and be sure.
Hope this helps

---

### Post by Yellow Pasque on 2013-01-25
I don't see anything glaringly wrong with the info. This is always worth a shot (deleting pulseaudio configuration files so fresh ones get generated):
```
cd ~/; rm -r .pulse*; pulseaudio -k
```

---

### Post by Simeo on 2013-01-25
> **AgentZ86 said:**
> Can you please check this

-Right click little speaker in upper right corner of ubuntu
-Select sound settings
-make sure the correct output device is selected
Test

In this particular boot there is no output available to select. In other boots I've tried doing what you suggested to no avail. I don't know why no outputs are available but of course, in this boot I'm now showing no audio and the only audio which is working is through my headphone jack (hooked to speakers). Thank you.

---

### Post by Simeo on 2013-01-25
> **Temüjin said:**
> I don't see anything glaringly wrong with the info. This is always worth a shot (deleting pulseaudio configuration files so fresh ones get generated):
```
cd ~/; rm -r .pulse*; pulseaudio -k
```

Received this output: ```
E: [pulseaudio] main.c: Failed to kill daemon: No such process
```

---

### Post by Yellow Pasque on 2013-01-25
Oh, so pulseaudio's not running and that's what's screwing it up. I wish I was better at reading those pulseaudio logs..

---

### Post by Simeo on 2013-01-25
> **Temüjin said:**
> Oh, so pulseaudio's not running and that's what's screwing it up. I wish I was better at reading those pulseaudio logs..

I don't know if this means anything but when I type in pulseaudio I receive the following output:
```

~$ pulseaudio
E: [pulseaudio] pid.c: Daemon already running.
E: [pulseaudio] main.c: pa_pid_file_create() failed.

```

Also now, I have audio working like normal again.... Is it just not starting at boot? I don't understand what's happening or why. Thank you for your help.

---

### Post by Yellow Pasque on 2013-01-25
Unfortunately, I'm not that familiar with pulseaudio (I use Debian/xfce and plain old ALSA). If you can't figure it out or no one can help with a couple days, maybe you should file a bug?
At least you know what's causing it and have your audio back...

---

### Post by Simeo on 2013-01-25
> **Temüjin said:**
> At least you know what's causing it and have your audio back...

No worries. Thank you so much for your help. If I have another issue on reboot I'll just try typing pulseaudio in terminal. If I continue to have an issue I'll file a bug report. 

Should I upgrade my alsa?

---

### Post by Yellow Pasque on 2013-01-25
> **Simeo said:**
> Should I upgrade my alsa?

I don't see any reason to..

---

### Post by AgentZ86 on 2013-01-26
One more thing to check is to make sure that in your bios or your FN shortcut keys did do not have the external audio connection muted

This is not a software setting but only a hardware setting either in bios or from a shortcut on your keyboard only.

Worth a second look anyhow

If it the external connections are disabled or muted then you wouldn't see anything in the output settings because they would not show up in this case, however this would also be persistant when bootting back to windows as well

---

### Post by Simeo on 2013-02-15
Alright it's happening again. I did a boot into Win7, played a game, used firefox, then restart into Ubuntu and no audio. -_-

Alsa Info: [http://www.alsa-project.org/db/?f=4143b08ebe82b26153e20a7e528a49c5ade75841](http://www.alsa-project.org/db/?f=4143b08ebe82b26153e20a7e528a49c5ade75841)

Pulse Audio Info: 
```
(   0.000|   0.000) I: [pulseaudio] main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
(   0.000|   0.000) I: [pulseaudio] main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
(   0.000|   0.000) D: [pulseaudio] core-rtclock.c: Timer slack is set to 50 us.
(   0.003|   0.003) D: [pulseaudio] core-util.c: RealtimeKit worked.
(   0.003|   0.000) I: [pulseaudio] core-util.c: Successfully gained nice level -11.
(   0.003|   0.000) I: [pulseaudio] main.c: This is PulseAudio 2.1
(   0.003|   0.000) D: [pulseaudio] main.c: Compilation host: x86_64-pc-linux-gnu
(   0.003|   0.000) D: [pulseaudio] main.c: Compilation CFLAGS: -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Werror=format-security -Wall -W -Wextra -pipe -Wno-long-long -Wvla -Wno-overlength-strings -Wunsafe-loop-optimizations -Wundef -Wformat=2 -Wlogical-op -Wsign-compare -Wformat-security -Wmissing-include-dirs -Wformat-nonliteral -Wpointer-arith -Winit-self -Wdeclaration-after-statement -Wfloat-equal -Wmissing-prototypes -Wredundant-decls -Wmissing-declarations -Wmissing-noreturn -Wshadow -Wendif-labels -Wcast-align -Wstrict-aliasing -Wwrite-strings -Wno-unused-parameter -ffast-math -Wp,-D_FORTIFY_SOURCE=2 -fno-common -fdiagnostics-show-option
(   0.003|   0.000) D: [pulseaudio] main.c: Running on host: Linux x86_64 3.5.0-23-generic #35-Ubuntu SMP Thu Jan 24 13:15:40 UTC 2013
(   0.004|   0.000) D: [pulseaudio] main.c: Found 4 CPUs.
(   0.004|   0.000) I: [pulseaudio] main.c: Page size is 4096 bytes
(   0.004|   0.000) D: [pulseaudio] main.c: Compiled with Valgrind support: no
(   0.004|   0.000) D: [pulseaudio] main.c: Running in valgrind mode: no
(   0.004|   0.000) D: [pulseaudio] main.c: Running in VM: no
(   0.004|   0.000) D: [pulseaudio] main.c: Optimized build: yes
(   0.004|   0.000) D: [pulseaudio] main.c: FASTPATH defined, only fast path asserts disabled.
(   0.004|   0.000) I: [pulseaudio] main.c: Machine ID is 68208ada37ae139fa75f636350ef60fd.
(   0.004|   0.000) I: [pulseaudio] main.c: Session ID is 68208ada37ae139fa75f636350ef60fd-1360959397.541844-576099878.
(   0.004|   0.000) I: [pulseaudio] main.c: Using runtime directory /home/joshua/.pulse/68208ada37ae139fa75f636350ef60fd-runtime.
(   0.004|   0.000) I: [pulseaudio] main.c: Using state directory /home/joshua/.pulse.
(   0.004|   0.000) I: [pulseaudio] main.c: Using modules directory /usr/lib/pulse-2.1/modules.
(   0.004|   0.000) I: [pulseaudio] main.c: Running in system mode: no
(   0.004|   0.000) I: [pulseaudio] main.c: Fresh high-resolution timers available! Bon appetit!
(   0.004|   0.000) D: [pulseaudio] memblock.c: Using shared memory pool with 1024 slots of size 64.0 KiB each, total size is 64.0 MiB, maximum usable slot size is 65472
(   0.004|   0.000) I: [pulseaudio] cpu-x86.c: CPU flags: CMOV MMX SSE SSE2 SSE3 SSSE3 SSE4_1 SSE4_2 
(   0.004|   0.000) I: [pulseaudio] svolume_mmx.c: Initialising MMX optimized volume functions.
(   0.004|   0.000) I: [pulseaudio] remap_mmx.c: Initialising MMX optimized remappers.
(   0.004|   0.000) I: [pulseaudio] svolume_sse.c: Initialising SSE2 optimized volume functions.
(   0.004|   0.000) I: [pulseaudio] remap_sse.c: Initialising SSE2 optimized remappers.
(   0.004|   0.000) I: [pulseaudio] sconv_sse.c: Initialising SSE2 optimized conversions.
(   0.004|   0.000) I: [pulseaudio] svolume_orc.c: Initialising ORC optimized volume functions.
(   0.005|   0.000) D: [pulseaudio] database-tdb.c: Opened TDB database '/home/joshua/.pulse/68208ada37ae139fa75f636350ef60fd-device-volumes.tdb'
(   0.005|   0.000) I: [pulseaudio] module-device-restore.c: Successfully opened database file '/home/joshua/.pulse/68208ada37ae139fa75f636350ef60fd-device-volumes'.
(   0.005|   0.000) I: [pulseaudio] module.c: Loaded "module-device-restore" (index: #0; argument: "").
(   0.005|   0.000) D: [pulseaudio] database-tdb.c: Opened TDB database '/home/joshua/.pulse/68208ada37ae139fa75f636350ef60fd-stream-volumes.tdb'
(   0.005|   0.000) I: [pulseaudio] module-stream-restore.c: Successfully opened database file '/home/joshua/.pulse/68208ada37ae139fa75f636350ef60fd-stream-volumes'.
(   0.005|   0.000) D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Ext.StreamRestore1 added for object /org/pulseaudio/stream_restore1
(   0.005|   0.000) D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Ext.StreamRestore1.RestoreEntry added for object /org/pulseaudio/stream_restore1/entry0
(   0.005|   0.000) D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Ext.StreamRestore1.RestoreEntry added for object /org/pulseaudio/stream_restore1/entry1
(   0.006|   0.000) D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Ext.StreamRestore1.RestoreEntry added for object /org/pulseaudio/stream_restore1/entry2
(   0.006|   0.000) D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Ext.StreamRestore1.RestoreEntry added for object /org/pulseaudio/stream_restore1/entry3
(   0.006|   0.000) D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Ext.StreamRestore1.RestoreEntry added for object /org/pulseaudio/stream_restore1/entry4
(   0.006|   0.000) D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Ext.StreamRestore1.RestoreEntry added for object /org/pulseaudio/stream_restore1/entry5
(   0.006|   0.000) D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Ext.StreamRestore1.RestoreEntry added for object /org/pulseaudio/stream_restore1/entry6
(   0.006|   0.000) D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Ext.StreamRestore1.RestoreEntry added for object /org/pulseaudio/stream_restore1/entry7
(   0.006|   0.000) D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Ext.StreamRestore1.RestoreEntry added for object /org/pulseaudio/stream_restore1/entry8
(   0.006|   0.000) I: [pulseaudio] module.c: Loaded "module-stream-restore" (index: #1; argument: "").
(   0.006|   0.000) D: [pulseaudio] database-tdb.c: Opened TDB database '/home/joshua/.pulse/68208ada37ae139fa75f636350ef60fd-card-database.tdb'
(   0.006|   0.000) I: [pulseaudio] module-card-restore.c: Successfully opened database file '/home/joshua/.pulse/68208ada37ae139fa75f636350ef60fd-card-database'.
(   0.006|   0.000) I: [pulseaudio] module.c: Loaded "module-card-restore" (index: #2; argument: "").
(   0.006|   0.000) I: [pulseaudio] module.c: Loaded "module-augment-properties" (index: #3; argument: "").
(   0.006|   0.000) D: [pulseaudio] cli-command.c: Checking for existence of '/usr/lib/pulse-2.1/modules/module-udev-detect.so': success
(   0.007|   0.000) D: [pulseaudio] module-udev-detect.c: /dev/snd/controlC0 is accessible: yes
(   0.007|   0.000) D: [pulseaudio] module-udev-detect.c: /devices/pci0000:00/0000:00:1b.0/sound/card0 is busy: yes
(   0.007|   0.000) I: [pulseaudio] module-udev-detect.c: Found 1 cards.
(   0.007|   0.000) I: [pulseaudio] module.c: Loaded "module-udev-detect" (index: #4; argument: "").
(   0.007|   0.000) D: [pulseaudio] cli-command.c: Checking for existence of '/usr/lib/pulse-2.1/modules/module-jackdbus-detect.so': failure
(   0.007|   0.000) D: [pulseaudio] cli-command.c: Checking for existence of '/usr/lib/pulse-2.1/modules/module-bluetooth-discover.so': success
(   0.008|   0.001) D: [pulseaudio] dbus-util.c: Successfully connected to D-Bus system bus c261a123bbbe1fe99409e105511e97a3 as :1.69
(   0.009|   0.001) D: [pulseaudio] bluetooth-util.c: dbus: interface=org.freedesktop.DBus, path=/org/freedesktop/DBus, member=NameAcquired
(   0.010|   0.000) I: [pulseaudio] module.c: Loaded "module-bluetooth-discover" (index: #5; argument: "").
(   0.010|   0.000) D: [pulseaudio] cli-command.c: Checking for existence of '/usr/lib/pulse-2.1/modules/module-esound-protocol-unix.so': failure
(   0.010|   0.000) I: [pulseaudio] module.c: Loaded "module-native-protocol-unix" (index: #6; argument: "").
(   0.010|   0.000) D: [pulseaudio] cli-command.c: Checking for existence of '/usr/lib/pulse-2.1/modules/module-gconf.so': success
(   0.015|   0.004) I: [pulseaudio] module.c: Loaded "module-gconf" (index: #7; argument: "").
(   0.015|   0.000) I: [pulseaudio] module-default-device-restore.c: Saved default sink 'alsa_output.pci-0000_00_1b.0.iec958-stereo' not existent, not restoring default sink setting.
(   0.015|   0.000) I: [pulseaudio] module-default-device-restore.c: Saved default source 'alsa_input.pci-0000_00_1b.0.analog-stereo' not existent, not restoring default source setting.
(   0.015|   0.000) I: [pulseaudio] module.c: Loaded "module-default-device-restore" (index: #8; argument: "").
(   0.016|   0.000) I: [pulseaudio] module.c: Loaded "module-rescue-streams" (index: #9; argument: "").
(   0.016|   0.000) D: [pulseaudio] module-always-sink.c: Autoloading null-sink as no other sinks detected.
(   0.016|   0.000) I: [pulseaudio] sink.c: Created sink 0 "auto_null" with sample spec s16le 2ch 44100Hz and channel map front-left,front-right
(   0.016|   0.000) I: [pulseaudio] sink.c:     device.description = "Dummy Output"
(   0.016|   0.000) I: [pulseaudio] sink.c:     device.class = "abstract"
(   0.016|   0.000) I: [pulseaudio] sink.c:     device.icon_name = "audio-card"
(   0.016|   0.000) D: [pulseaudio] core-subscribe.c: Dropped redundant event due to change event.
(   0.016|   0.000) I: [pulseaudio] source.c: Created source 0 "auto_null.monitor" with sample spec s16le 2ch 44100Hz and channel map front-left,front-right
(   0.016|   0.000) I: [pulseaudio] source.c:     device.description = "Monitor of Dummy Output"
(   0.016|   0.000) I: [pulseaudio] source.c:     device.class = "monitor"
(   0.016|   0.000) I: [pulseaudio] source.c:     device.icon_name = "audio-input-microphone"
(   0.016|   0.000) D: [null-sink] module-null-sink.c: Thread starting up
(   0.016|   0.000) D: [pulseaudio] module-device-restore.c: Could not set format on sink auto_null
(   0.016|   0.000) I: [pulseaudio] module.c: Loaded "module-null-sink" (index: #10; argument: "sink_name=auto_null sink_properties='device.description="Dummy Output"'").
(   0.016|   0.000) I: [pulseaudio] module.c: Loaded "module-always-sink" (index: #11; argument: "").
(   0.016|   0.000) I: [pulseaudio] module.c: Loaded "module-intended-roles" (index: #12; argument: "").
(   0.016|   0.000) D: [pulseaudio] module-suspend-on-idle.c: Sink auto_null becomes idle, timeout in 5 seconds.
(   0.016|   0.000) I: [pulseaudio] module.c: Loaded "module-suspend-on-idle" (index: #13; argument: "").
(   0.016|   0.000) D: [pulseaudio] cli-command.c: Checking for existence of '/usr/lib/pulse-2.1/modules/module-console-kit.so': success
(   0.017|   0.000) I: [pulseaudio] client.c: Created 0 "ConsoleKit Session /org/freedesktop/ConsoleKit/Session1"
(   0.017|   0.000) D: [pulseaudio] module-console-kit.c: Added new session /org/freedesktop/ConsoleKit/Session1
(   0.017|   0.000) I: [pulseaudio] module.c: Loaded "module-console-kit" (index: #14; argument: "").
(   0.017|   0.000) D: [pulseaudio] cli-command.c: Checking for existence of '/usr/lib/pulse-2.1/modules/module-systemd-login.so': failure
(   0.017|   0.000) I: [pulseaudio] module.c: Loaded "module-position-event-sounds" (index: #15; argument: "").
(   0.017|   0.000) I: [pulseaudio] module.c: Loaded "module-filter-heuristics" (index: #16; argument: "").
(   0.018|   0.000) I: [pulseaudio] module.c: Loaded "module-filter-apply" (index: #17; argument: "").
(   0.018|   0.000) I: [pulseaudio] module.c: Loaded "module-switch-on-port-available" (index: #18; argument: "").
(   0.019|   0.000) D: [pulseaudio] dbus-util.c: Successfully connected to D-Bus session bus aaf0ff2fb39a3255c32db3ba511e97a6 as :1.120
(   0.020|   0.000) D: [pulseaudio] main.c: Got org.PulseAudio1!
(   0.021|   0.001) D: [pulseaudio] main.c: Got org.pulseaudio.Server!
(   0.021|   0.000) I: [pulseaudio] main.c: Daemon startup complete.
(   0.021|   0.000) I: [pulseaudio] client.c: Created 1 "Native client (UNIX socket client)"
(   0.021|   0.000) D: [pulseaudio] protocol-native.c: Protocol version: remote 26, local 26
(   0.021|   0.000) I: [pulseaudio] protocol-native.c: Got credentials: uid=1000 gid=1000 success=1
(   0.021|   0.000) D: [pulseaudio] protocol-native.c: SHM possible: yes
(   0.021|   0.000) D: [pulseaudio] protocol-native.c: Negotiated SHM: yes
(   0.022|   0.000) D: [pulseaudio] module-augment-properties.c: Looking for .desktop file for indicator-sound-service
(   0.024|   0.002) I: [pulseaudio] client.c: Created 2 "Native client (UNIX socket client)"
(   0.024|   0.000) D: [pulseaudio] protocol-native.c: Protocol version: remote 26, local 26
(   0.024|   0.000) I: [pulseaudio] protocol-native.c: Got credentials: uid=1000 gid=1000 success=1
(   0.024|   0.000) D: [pulseaudio] protocol-native.c: SHM possible: yes
(   0.024|   0.000) D: [pulseaudio] protocol-native.c: Negotiated SHM: yes
(   0.024|   0.000) D: [pulseaudio] module-augment-properties.c: Looking for .desktop file for gnome-settings-daemon
(   0.026|   0.001) D: [pulseaudio] protocol-native.c: Client indicator-sound-service changes volume of source auto_null.monitor.
(   5.021|   4.994) I: [pulseaudio] module-suspend-on-idle.c: Sink auto_null idle for too long, suspending ...
(   5.021|   0.000) D: [pulseaudio] sink.c: Suspend cause of sink auto_null is 0x0004, suspending
(   5.021|   0.000) D: [pulseaudio] core.c: Hmm, no streams around, trying to vacuum.
(   5.021|   0.000) I: [pulseaudio] module-device-restore.c: Storing volume/mute for device+port source:auto_null.monitor:null.
(  15.031|  10.009) I: [pulseaudio] module-device-restore.c: Synced.
(  26.206|  11.175) I: [pulseaudio] client.c: Created 3 "Native client (UNIX socket client)"
(  26.410|   0.203) D: [pulseaudio] protocol-native.c: Protocol version: remote 26, local 26
(  26.410|   0.000) I: [pulseaudio] protocol-native.c: Got credentials: uid=1000 gid=1000 success=1
(  26.410|   0.000) D: [pulseaudio] protocol-native.c: SHM possible: yes
(  26.410|   0.000) D: [pulseaudio] protocol-native.c: Negotiated SHM: yes
(  26.410|   0.000) D: [pulseaudio] module-augment-properties.c: Looking for .desktop file for gnome-control-center
(  26.410|   0.000) D: [pulseaudio] module-augment-properties.c: Found /usr/share/applications/gnome-control-center.desktop.
(  31.305|   4.894) I: [pulseaudio] client.c: Freed 3 "GNOME Volume Control Dialog"
(  31.305|   0.000) I: [pulseaudio] protocol-native.c: Connection died.
(  36.010|   4.705) I: [pulseaudio] main.c: Got signal SIGINT.
(  36.010|   0.000) I: [pulseaudio] main.c: Exiting.
(  36.010|   0.000) I: [pulseaudio] main.c: Daemon shutdown initiated.
(  36.010|   0.000) I: [pulseaudio] module.c: Unloading "module-device-restore" (index: #0).
(  36.010|   0.000) I: [pulseaudio] module.c: Unloaded "module-device-restore" (index: #0).
(  36.010|   0.000) I: [pulseaudio] module.c: Unloading "module-stream-restore" (index: #1).
(  36.010|   0.000) D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Ext.StreamRestore1 removed from object /org/pulseaudio/stream_restore1
(  36.010|   0.000) D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Ext.StreamRestore1.RestoreEntry removed from object /org/pulseaudio/stream_restore1/entry0
(  36.010|   0.000) D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Ext.StreamRestore1.RestoreEntry removed from object /org/pulseaudio/stream_restore1/entry1
(  36.010|   0.000) D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Ext.StreamRestore1.RestoreEntry removed from object /org/pulseaudio/stream_restore1/entry2
(  36.010|   0.000) D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Ext.StreamRestore1.RestoreEntry removed from object /org/pulseaudio/stream_restore1/entry3
(  36.010|   0.000) D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Ext.StreamRestore1.RestoreEntry removed from object /org/pulseaudio/stream_restore1/entry4
(  36.010|   0.000) D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Ext.StreamRestore1.RestoreEntry removed from object /org/pulseaudio/stream_restore1/entry5
(  36.010|   0.000) D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Ext.StreamRestore1.RestoreEntry removed from object /org/pulseaudio/stream_restore1/entry6
(  36.010|   0.000) D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Ext.StreamRestore1.RestoreEntry removed from object /org/pulseaudio/stream_restore1/entry7
(  36.010|   0.000) D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Ext.StreamRestore1.RestoreEntry removed from object /org/pulseaudio/stream_restore1/entry8
(  36.010|   0.000) D: [pulseaudio] flist.c: pulsecore/hashmap.c: entries flist is full (don't worry)
(  36.010|   0.000) D: [pulseaudio] flist.c: pulsecore/hashmap.c: entries flist is full (don't worry)
(  36.010|   0.000) D: [pulseaudio] flist.c: pulsecore/hashmap.c: entries flist is full (don't worry)
(  36.010|   0.000) D: [pulseaudio] flist.c: pulsecore/hashmap.c: entries flist is full (don't worry)
(  36.010|   0.000) D: [pulseaudio] flist.c: pulsecore/hashmap.c: entries flist is full (don't worry)
(  36.010|   0.000) D: [pulseaudio] flist.c: pulsecore/hashmap.c: entries flist is full (don't worry)
(  36.010|   0.000) I: [pulseaudio] module.c: Unloaded "module-stream-restore" (index: #1).
(  36.010|   0.000) I: [pulseaudio] module.c: Unloading "module-card-restore" (index: #2).
(  36.010|   0.000) D: [pulseaudio] flist.c: pulsecore/hashmap.c: entries flist is full (don't worry)
(  36.010|   0.000) D: [pulseaudio] flist.c: pulsecore/hashmap.c: entries flist is full (don't worry)
(  36.010|   0.000) D: [pulseaudio] flist.c: pulsecore/hashmap.c: entries flist is full (don't worry)
(  36.010|   0.000) I: [pulseaudio] module.c: Unloaded "module-card-restore" (index: #2).
(  36.010|   0.000) I: [pulseaudio] module.c: Unloading "module-augment-properties" (index: #3).
(  36.010|   0.000) D: [pulseaudio] flist.c: pulsecore/hashmap.c: entries flist is full (don't worry)
(  36.010|   0.000) D: [pulseaudio] flist.c: pulsecore/hashmap.c: entries flist is full (don't worry)
(  36.010|   0.000) I: [pulseaudio] module.c: Unloaded "module-augment-properties" (index: #3).
(  36.010|   0.000) I: [pulseaudio] module.c: Unloading "module-udev-detect" (index: #4).
(  36.011|   0.000) I: [pulseaudio] module.c: Unloaded "module-udev-detect" (index: #4).
(  36.011|   0.000) I: [pulseaudio] module.c: Unloading "module-bluetooth-discover" (index: #5).
(  36.011|   0.000) I: [pulseaudio] module.c: Unloaded "module-bluetooth-discover" (index: #5).
(  36.011|   0.000) I: [pulseaudio] module.c: Unloading "module-native-protocol-unix" (index: #6).
(  36.011|   0.000) I: [pulseaudio] client.c: Freed 1 "Indicator Sound"
(  36.011|   0.000) I: [pulseaudio] client.c: Freed 2 "GNOME Volume Control Media Keys"
(  36.011|   0.000) I: [pulseaudio] module.c: Unloaded "module-native-protocol-unix" (index: #6).
(  36.011|   0.000) I: [pulseaudio] module.c: Unloading "module-gconf" (index: #7).
(  36.011|   0.000) I: [pulseaudio] module.c: Unloaded "module-gconf" (index: #7).
(  36.011|   0.000) I: [pulseaudio] module.c: Unloading "module-default-device-restore" (index: #8).
(  36.011|   0.000) I: [pulseaudio] module.c: Unloaded "module-default-device-restore" (index: #8).
(  36.011|   0.000) I: [pulseaudio] module.c: Unloading "module-rescue-streams" (index: #9).
(  36.011|   0.000) I: [pulseaudio] module.c: Unloaded "module-rescue-streams" (index: #9).
(  36.011|   0.000) I: [pulseaudio] module.c: Unloading "module-null-sink" (index: #10).
(  36.011|   0.000) D: [pulseaudio] module-always-sink.c: Autoloaded null-sink removed
(  36.011|   0.000) D: [null-sink] module-null-sink.c: Thread shutting down
(  36.012|   0.000) I: [pulseaudio] sink.c: Freeing sink 0 "auto_null"
(  36.012|   0.000) I: [pulseaudio] source.c: Freeing source 0 "auto_null.monitor"
(  36.012|   0.000) I: [pulseaudio] module.c: Unloaded "module-null-sink" (index: #10).
(  36.012|   0.000) I: [pulseaudio] module.c: Unloading "module-always-sink" (index: #11).
(  36.012|   0.000) I: [pulseaudio] module.c: Unloaded "module-always-sink" (index: #11).
(  36.012|   0.000) I: [pulseaudio] module.c: Unloading "module-intended-roles" (index: #12).
(  36.012|   0.000) I: [pulseaudio] module.c: Unloaded "module-intended-roles" (index: #12).
(  36.012|   0.000) I: [pulseaudio] module.c: Unloading "module-suspend-on-idle" (index: #13).
(  36.012|   0.000) I: [pulseaudio] module.c: Unloaded "module-suspend-on-idle" (index: #13).
(  36.012|   0.000) I: [pulseaudio] module.c: Unloading "module-console-kit" (index: #14).
(  36.012|   0.000) D: [pulseaudio] module-console-kit.c: Removing session /org/freedesktop/ConsoleKit/Session1
(  36.012|   0.000) I: [pulseaudio] client.c: Freed 0 "ConsoleKit Session /org/freedesktop/ConsoleKit/Session1"
(  36.012|   0.000) I: [pulseaudio] module.c: Unloaded "module-console-kit" (index: #14).
(  36.012|   0.000) I: [pulseaudio] module.c: Unloading "module-position-event-sounds" (index: #15).
(  36.012|   0.000) I: [pulseaudio] module.c: Unloaded "module-position-event-sounds" (index: #15).
(  36.012|   0.000) I: [pulseaudio] module.c: Unloading "module-filter-heuristics" (index: #16).
(  36.012|   0.000) I: [pulseaudio] module.c: Unloaded "module-filter-heuristics" (index: #16).
(  36.012|   0.000) I: [pulseaudio] module.c: Unloading "module-filter-apply" (index: #17).
(  36.012|   0.000) I: [pulseaudio] module.c: Unloaded "module-filter-apply" (index: #17).
(  36.012|   0.000) I: [pulseaudio] module.c: Unloading "module-switch-on-port-available" (index: #18).
(  36.012|   0.000) I: [pulseaudio] module.c: Unloaded "module-switch-on-port-available" (index: #18).
(  36.012|   0.000) I: [pulseaudio] main.c: Daemon terminated.
```

---

### Post by Simeo on 2013-02-15
Another Note. Upon typing 'killall pulsaudio' into the terminal to get the pulseaudio info above my audio started working again.... but out of BOTH headphones and laptop speakers.

Edit: Now nothing is working.

---

