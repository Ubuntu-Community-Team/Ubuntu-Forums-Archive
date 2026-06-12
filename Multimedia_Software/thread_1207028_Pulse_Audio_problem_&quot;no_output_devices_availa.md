---
title: "Pulse Audio problem: &quot;no output devices available&quot;"
date: 2009-07-07
forum: Multimedia Software
---

### Post by zob on 2009-07-07
Hi.

I'm on ubuntu 9.04 with a RME HDSP 9632 sound card.

Pulseaudio doesn't seem to work for me. I can get sound from vlc for example, but only because I can tweak it to direct the sound directly to my sound card.

However, anything that goes through pulse, doesn't make a sound. For example rhythmbox. I can see the rhythmbox sound streaming in my playback tab i the pulseaudio volume control. The problem is that pulseaudio doesn't detect my output device (in my case the HDSP-card), so under the output-tab I can't get any hardware devices, I only get a virtual "Null output" and that doesn't make a sound.

There are no errors in all the standard troubleshooting commands like lspci, aplay -l, lshw -C multimedia, cat /proc/asound/cards and the like.

I do however get errors when starting op pulseaudio. So I will start by only listing that and a pulseaudio-log which follows:

```
lars@ubuntu:~$ pulseaudio -v --log-target=stderr
I: main.c: We're in the group 'pulse-rt', allowing high-priority scheduling.
I: main.c: RLIMIT_RTPRIO is set to 99, allowing real-time scheduling.
I: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
I: core-util.c: Successfully gained nice level -11.
I: main.c: Giving up CAP_NICE
I: main.c: This is PulseAudio 0.9.15
I: main.c: Page size is 4096 bytes
I: main.c: Machine ID is b901b9c288a08f1c0f8aa01c4a0369b2.
I: main.c: Session ID is b901b9c288a08f1c0f8aa01c4a0369b2-1247005694.122951-828548076.
I: main.c: Using runtime directory /home/lars/.pulse/b901b9c288a08f1c0f8aa01c4a0369b2:runtime.
I: main.c: Using state directory /home/lars/.pulse.
I: main.c: Running in system mode: no
E: pid.c: Daemon already running.
E: main.c: pa_pid_file_create() failed.

```

First:
```
killall pulseaudio
```

And then restart in terminal verbose mode (here come the errors):
```
D: main.c: Started as real root: no, suid root: yes
I: main.c: We're in the group 'pulse-rt', allowing high-priority scheduling.
I: main.c: RLIMIT_RTPRIO is set to 99, allowing real-time scheduling.
I: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
I: core-util.c: Successfully gained nice level -11.
D: main.c: Can realtime: yes, can high-priority: yes
I: main.c: Giving up CAP_NICE
D: main.c: Can realtime: yes, can high-priority: no
I: main.c: This is PulseAudio 0.9.15
D: main.c: Compilation host: i486-pc-linux-gnu
D: main.c: Compilation CFLAGS: -g -O2 -g -Wall -O3 -Wall -W -Wextra -pipe -Wno-long-long -Winline -Wvla -Wno-overlength-strings -Wunsafe-loop-optimizations -Wundef -Wformat=2 -Wlogical-op -Wsign-compare -Wformat-security -Wmissing-include-dirs -Wformat-nonliteral -Wold-style-definition -Wpointer-arith -Winit-self -Wdeclaration-after-statement -Wfloat-equal -Wmissing-prototypes -Wstrict-prototypes -Wredundant-decls -Wmissing-declarations -Wmissing-noreturn -Wshadow -Wendif-labels -Wcast-align -Wstrict-aliasing=2 -Wwrite-strings -Wno-unused-parameter -ffast-math -Wp,-D_FORTIFY_SOURCE=2 -fno-common -fdiagnostics-show-option
D: main.c: Running on host: Linux i686 2.6.28-3-rt #12-Ubuntu SMP PREEMPT RT Fri Apr 17 10:09:11 UTC 2009
D: main.c: Found 1 CPUs.
I: main.c: Page size is 4096 bytes
D: main.c: Compiled with Valgrind support: no
D: main.c: Running in valgrind mode: no
D: main.c: Optimized build: yes
D: main.c: All asserts enabled.
I: main.c: Machine ID is b901b9c288a08f1c0f8aa01c4a0369b2.
I: main.c: Session ID is b901b9c288a08f1c0f8aa01c4a0369b2-1247005694.122951-828548076.
I: main.c: Using runtime directory /home/lars/.pulse/b901b9c288a08f1c0f8aa01c4a0369b2:runtime.
I: main.c: Using state directory /home/lars/.pulse.
I: main.c: Running in system mode: no
I: main.c: Fresh high-resolution timers available! Bon appetit!
D: rtclock.c: Timer slack is set to 50 us.
D: memblock.c: Using shared memory pool with 1024 slots of size 64,0 KiB each, total size is 64,0 MiB, maximum usable slot size is 65496
I: module.c: Loaded "module-suspend-on-idle" (index: #0; argument: "").
I: module-device-restore.c: Sucessfully opened database file '/home/lars/.pulse/b901b9c288a08f1c0f8aa01c4a0369b2:device-volumes.i486-pc-linux-gnu.gdbm'.
I: module.c: Loaded "module-device-restore" (index: #1; argument: "").
I: module-stream-restore.c: Sucessfully opened database file '/home/lars/.pulse/b901b9c288a08f1c0f8aa01c4a0369b2:stream-volumes.i486-pc-linux-gnu.gdbm'.
I: module.c: Loaded "module-stream-restore" (index: #2; argument: "").
I: module-card-restore.c: Sucessfully opened database file '/home/lars/.pulse/b901b9c288a08f1c0f8aa01c4a0369b2:card-database.i486-pc-linux-gnu.gdbm'.
I: module.c: Loaded "module-card-restore" (index: #3; argument: "").
I: module.c: Loaded "module-augment-properties" (index: #4; argument: "").
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9.15/modules/module-hal-detect.so': success
D: dbus-util.c: Successfully connected to D-Bus system bus 8736ffe233278aad456f8beb4a53cbe1 as :1.63
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/computer_alsa_timer
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/computer_alsa_sequencer
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_10ee_3fc5_sound_card_0_alsa_playback_0
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_10ee_3fc5_sound_card_0_alsa_capture_0
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_10ee_3fc5_sound_card_0_alsa_midi_0
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_10ee_3fc5_sound_card_0_alsa_hw_specific_0
D: module-hal-detect.c: Loading module-alsa-card with arguments 'device_id=0 name=pci_10ee_3fc5_sound_card_0 card_name=alsa_card.pci_10ee_3fc5_sound_card_0 tsched=0'
D: dbus-util.c: Successfully connected to D-Bus session bus 3962a9db3bcdc8c43061909d4a53cbff as :1.83
D: reserve-wrap.c: Successfully acquired reservation lock on device 'Audio0'
D: alsa-util.c: Checking for playback on analog-mono (hw)
D: alsa-util.c: Trying hw:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open hw:0
D: alsa-util.c: snd_pcm_hw_params_set_access() failed: Invalid argument
D: alsa-util.c: Trying hw:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open hw:0
D: alsa-util.c: snd_pcm_hw_params_set_access() failed: Invalid argument
D: alsa-util.c: Trying plug:hw:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:hw:0
D: alsa-util.c: snd_pcm_hw_params_set_format(Signed 16 bit Little Endian) failed: Invalid argument
D: alsa-util.c: snd_pcm_hw_params_set_format(Signed 16 bit Big Endian) failed: Invalid argument
D: alsa-util.c: snd_pcm_hw_params_set_format(Float 32 bit Little Endian) failed: Invalid argument
D: alsa-util.c: snd_pcm_hw_params_set_format(Float 32 bit Big Endian) failed: Invalid argument
D: alsa-util.c: snd_pcm_hw_params_set_channels() failed: Invalid argument
D: alsa-util.c: Trying plug:hw:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:hw:0
D: alsa-util.c: snd_pcm_hw_params_set_channels() failed: Invalid argument
I: alsa-util.c: Failed to set hardware parameters on plug:hw:0: Invalid argument
D: alsa-util.c: Checking for playback on analog-stereo (front)
D: alsa-util.c: Trying front:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)conf.c: Unknown parameters 0
I: (alsa-lib)pcm.c: Unknown PCM front:0
I: alsa-util.c: Error opening PCM device front:0: Invalid argument
D: alsa-util.c: Trying hw:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open hw:0
D: alsa-util.c: snd_pcm_hw_params_set_access() failed: Invalid argument
D: alsa-util.c: Trying hw:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open hw:0
D: alsa-util.c: snd_pcm_hw_params_set_access() failed: Invalid argument
D: alsa-util.c: Trying plug:hw:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:hw:0
D: alsa-util.c: snd_pcm_hw_params_set_format(Signed 16 bit Little Endian) failed: Invalid argument
D: alsa-util.c: snd_pcm_hw_params_set_format(Signed 16 bit Big Endian) failed: Invalid argument
D: alsa-util.c: snd_pcm_hw_params_set_format(Float 32 bit Little Endian) failed: Invalid argument
D: alsa-util.c: snd_pcm_hw_params_set_format(Float 32 bit Big Endian) failed: Invalid argument
D: alsa-util.c: snd_pcm_hw_params_set_channels() failed: Invalid argument
D: alsa-util.c: Trying plug:hw:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:hw:0
D: alsa-util.c: snd_pcm_hw_params_set_channels() failed: Invalid argument
I: alsa-util.c: Failed to set hardware parameters on plug:hw:0: Invalid argument
D: alsa-util.c: Checking for playback on iec958-stereo (iec958)
D: alsa-util.c: Trying iec958:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)conf.c: Unknown parameters 0
I: (alsa-lib)pcm.c: Unknown PCM iec958:0
I: alsa-util.c: Error opening PCM device iec958:0: Invalid argument
D: alsa-util.c: Checking for playback on hdmi-stereo (hdmi)
D: alsa-util.c: Trying hdmi:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)conf.c: Unknown parameters 0
I: (alsa-lib)pcm.c: Unknown PCM hdmi:0
I: alsa-util.c: Error opening PCM device hdmi:0: Invalid argument
D: alsa-util.c: Checking for playback on analog-surround-40 (surround40)
D: alsa-util.c: Trying surround40:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)conf.c: Unknown parameters 0
I: (alsa-lib)pcm.c: Unknown PCM surround40:0
I: alsa-util.c: Error opening PCM device surround40:0: Invalid argument
D: alsa-util.c: Checking for playback on iec958-ac3-surround-40 (a52)
D: alsa-util.c: Trying a52:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm.c: Unknown PCM a52:0
I: alsa-util.c: Error opening PCM device a52:0: No such file or directory
D: alsa-util.c: Checking for playback on analog-surround-41 (surround41)
D: alsa-util.c: Trying surround41:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)conf.c: Unknown parameters 0
I: (alsa-lib)pcm.c: Unknown PCM surround41:0
I: alsa-util.c: Error opening PCM device surround41:0: Invalid argument
D: alsa-util.c: Checking for playback on analog-surround-50 (surround50)
D: alsa-util.c: Trying surround50:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)conf.c: Unknown parameters 0
I: (alsa-lib)pcm.c: Unknown PCM surround50:0
I: alsa-util.c: Error opening PCM device surround50:0: Invalid argument
D: alsa-util.c: Checking for playback on analog-surround-51 (surround51)
D: alsa-util.c: Trying surround51:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)conf.c: Unknown parameters 0
I: (alsa-lib)pcm.c: Unknown PCM surround51:0
I: alsa-util.c: Error opening PCM device surround51:0: Invalid argument
D: alsa-util.c: Checking for playback on iec958-ac3-surround-51 (a52)
D: alsa-util.c: Trying a52:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm.c: Unknown PCM a52:0
I: alsa-util.c: Error opening PCM device a52:0: No such file or directory
D: alsa-util.c: Checking for playback on analog-surround-71 (surround71)
D: alsa-util.c: Trying surround71:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)conf.c: Unknown parameters 0
I: (alsa-lib)pcm.c: Unknown PCM surround71:0
I: alsa-util.c: Error opening PCM device surround71:0: Invalid argument
D: alsa-util.c: Checking for capture on analog-mono (hw)
D: alsa-util.c: Trying hw:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open hw:0
D: alsa-util.c: snd_pcm_hw_params_set_access() failed: Invalid argument
D: alsa-util.c: Trying hw:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open hw:0
D: alsa-util.c: snd_pcm_hw_params_set_access() failed: Invalid argument
D: alsa-util.c: Trying plug:hw:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:hw:0
D: alsa-util.c: snd_pcm_hw_params_set_format(Signed 16 bit Little Endian) failed: Invalid argument
D: alsa-util.c: snd_pcm_hw_params_set_format(Signed 16 bit Big Endian) failed: Invalid argument
D: alsa-util.c: snd_pcm_hw_params_set_format(Float 32 bit Little Endian) failed: Invalid argument
D: alsa-util.c: snd_pcm_hw_params_set_format(Float 32 bit Big Endian) failed: Invalid argument
D: alsa-util.c: snd_pcm_hw_params_set_channels() failed: Invalid argument
D: alsa-util.c: Trying plug:hw:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:hw:0
D: alsa-util.c: snd_pcm_hw_params_set_channels() failed: Invalid argument
I: alsa-util.c: Failed to set hardware parameters on plug:hw:0: Invalid argument
D: alsa-util.c: Checking for capture on analog-stereo (front)
D: alsa-util.c: Trying front:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)conf.c: Unknown parameters 0
I: (alsa-lib)pcm.c: Unknown PCM front:0
I: alsa-util.c: Error opening PCM device front:0: Invalid argument
D: alsa-util.c: Trying hw:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open hw:0
D: alsa-util.c: snd_pcm_hw_params_set_access() failed: Invalid argument
D: alsa-util.c: Trying hw:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open hw:0
D: alsa-util.c: snd_pcm_hw_params_set_access() failed: Invalid argument
D: alsa-util.c: Trying plug:hw:0 with SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:hw:0
D: alsa-util.c: snd_pcm_hw_params_set_format(Signed 16 bit Little Endian) failed: Invalid argument
D: alsa-util.c: snd_pcm_hw_params_set_format(Signed 16 bit Big Endian) failed: Invalid argument
D: alsa-util.c: snd_pcm_hw_params_set_format(Float 32 bit Little Endian) failed: Invalid argument
D: alsa-util.c: snd_pcm_hw_params_set_format(Float 32 bit Big Endian) failed: Invalid argument
D: alsa-util.c: snd_pcm_hw_params_set_channels() failed: Invalid argument
D: alsa-util.c: Trying plug:hw:0 without SND_PCM_NO_AUTO_FORMAT ...
D: alsa-util.c: Managed to open plug:hw:0
D: alsa-util.c: snd_pcm_hw_params_set_channels() failed: Invalid argument
I: alsa-util.c: Failed to set hardware parameters on plug:hw:0: Invalid argument
D: alsa-util.c: Checking for capture on iec958-stereo (iec958)
D: alsa-util.c: Trying iec958:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)conf.c: Unknown parameters 0
I: (alsa-lib)pcm.c: Unknown PCM iec958:0
I: alsa-util.c: Error opening PCM device iec958:0: Invalid argument
D: alsa-util.c: Checking for capture on hdmi-stereo (hdmi)
D: alsa-util.c: Trying hdmi:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)conf.c: Unknown parameters 0
I: (alsa-lib)pcm.c: Unknown PCM hdmi:0
I: alsa-util.c: Error opening PCM device hdmi:0: Invalid argument
D: alsa-util.c: Checking for capture on analog-surround-40 (surround40)
D: alsa-util.c: Trying surround40:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)conf.c: Unknown parameters 0
I: (alsa-lib)pcm.c: Unknown PCM surround40:0
I: alsa-util.c: Error opening PCM device surround40:0: Invalid argument
D: alsa-util.c: Checking for capture on iec958-ac3-surround-40 (a52)
D: alsa-util.c: Trying a52:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm.c: Unknown PCM a52:0
I: alsa-util.c: Error opening PCM device a52:0: No such file or directory
D: alsa-util.c: Checking for capture on analog-surround-41 (surround41)
D: alsa-util.c: Trying surround41:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)conf.c: Unknown parameters 0
I: (alsa-lib)pcm.c: Unknown PCM surround41:0
I: alsa-util.c: Error opening PCM device surround41:0: Invalid argument
D: alsa-util.c: Checking for capture on analog-surround-50 (surround50)
D: alsa-util.c: Trying surround50:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)conf.c: Unknown parameters 0
I: (alsa-lib)pcm.c: Unknown PCM surround50:0
I: alsa-util.c: Error opening PCM device surround50:0: Invalid argument
D: alsa-util.c: Checking for capture on analog-surround-51 (surround51)
D: alsa-util.c: Trying surround51:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)conf.c: Unknown parameters 0
I: (alsa-lib)pcm.c: Unknown PCM surround51:0
I: alsa-util.c: Error opening PCM device surround51:0: Invalid argument
D: alsa-util.c: Checking for capture on iec958-ac3-surround-51 (a52)
D: alsa-util.c: Trying a52:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)pcm.c: Unknown PCM a52:0
I: alsa-util.c: Error opening PCM device a52:0: No such file or directory
D: alsa-util.c: Checking for capture on analog-surround-71 (surround71)
D: alsa-util.c: Trying surround71:0 with SND_PCM_NO_AUTO_FORMAT ...
I: (alsa-lib)conf.c: Unknown parameters 0
I: (alsa-lib)pcm.c: Unknown PCM surround71:0
I: alsa-util.c: Error opening PCM device surround71:0: Invalid argument
E: module-alsa-card.c: Failed to find a working profile.
E: module.c: Failed to load  module "module-alsa-card" (argument: "device_id=0 name=pci_10ee_3fc5_sound_card_0 card_name=alsa_card.pci_10ee_3fc5_sound_card_0 tsched=0"): initialization failed.
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_10ee_3fc5_sound_card_0_alsa_control__1
I: module-hal-detect.c: Loaded 0 modules.
I: module.c: Loaded "module-hal-detect" (index: #5; argument: "tsched=0").
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9.15/modules/module-bluetooth-discover.so': failure
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9.15/modules/module-esound-protocol-unix.so': success
I: module.c: Loaded "module-esound-protocol-unix" (index: #6; argument: "").
I: module.c: Loaded "module-native-protocol-unix" (index: #7; argument: "").
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9.15/modules/module-gconf.so': success
I: module.c: Loaded "module-gconf" (index: #8; argument: "").
I: module-default-device-restore.c: Saved default sink 'auto_null' not existant, not restoring default sink setting.
I: module-default-device-restore.c: Saved default source 'auto_null.monitor' not existant, not restoring default source setting.
I: module.c: Loaded "module-default-device-restore" (index: #9; argument: "").
I: module.c: Loaded "module-rescue-streams" (index: #10; argument: "").
D: module-always-sink.c: Autoloading null-sink as no other sinks detected.
I: module-device-restore.c: Restoring volume for sink auto_null.
I: module-device-restore.c: Restoring mute state for sink auto_null.
I: sink.c: Created sink 0 "auto_null" with sample spec s16le 2ch 44100Hz and channel map front-left,front-right
I: sink.c:     device.description = "Null Output"
I: sink.c:     device.class = "abstract"
I: sink.c:     device.icon_name = "audio-card"
I: module-device-restore.c: Restoring volume for source auto_null.monitor.
I: module-device-restore.c: Restoring mute state for source auto_null.monitor.
I: source.c: Created source 0 "auto_null.monitor" with sample spec s16le 2ch 44100Hz and channel map front-left,front-right
I: source.c:     device.description = "Monitor of Null Output"
I: source.c:     device.class = "monitor"
I: source.c:     device.icon_name = "audio-input-microphone"
D: module-null-sink.c: Thread starting up
D: rtpoll.c: Acquired POSIX realtime signal SIGRTMIN+29
D: module-suspend-on-idle.c: Sink auto_null becomes idle.
I: module.c: Loaded "module-null-sink" (index: #11; argument: "sink_name=auto_null").
I: module.c: Loaded "module-always-sink" (index: #12; argument: "").
I: client.c: Created 0 "ConsoleKit Session /org/freedesktop/ConsoleKit/Session1"
D: module-console-kit.c: Added new session /org/freedesktop/ConsoleKit/Session1
I: module.c: Loaded "module-console-kit" (index: #13; argument: "").
I: module.c: Loaded "module-position-event-sounds" (index: #14; argument: "").
I: module.c: Loaded "module-cork-music-on-phone" (index: #15; argument: "").
D: dbus-util.c: Successfully connected to D-Bus session bus 3962a9db3bcdc8c43061909d4a53cbff as :1.85
D: main.c: Got org.pulseaudio.Server!
I: main.c: Daemon startup complete.
D: module-hal-detect.c: dbus: interface=org.freedesktop.DBus, path=/org/freedesktop/DBus, member=NameAcquired
D: module-console-kit.c: dbus: interface=org.freedesktop.DBus, path=/org/freedesktop/DBus, member=NameAcquired
I: module-suspend-on-idle.c: Sink auto_null idle for too long, suspending ...
D: module-hal-detect.c: dbus: interface=org.freedesktop.ConsoleKit.Seat, path=/org/freedesktop/ConsoleKit/Seat1, member=SessionAdded
D: module-console-kit.c: dbus: interface=org.freedesktop.ConsoleKit.Seat, path=/org/freedesktop/ConsoleKit/Seat1, member=SessionAdded
D: module-hal-detect.c: dbus: interface=org.freedesktop.ConsoleKit.Seat, path=/org/freedesktop/ConsoleKit/Seat1, member=SessionAdded
D: module-console-kit.c: dbus: interface=org.freedesktop.ConsoleKit.Seat, path=/org/freedesktop/ConsoleKit/Seat1, member=SessionAdded
D: module-hal-detect.c: dbus: interface=org.freedesktop.ConsoleKit.Seat, path=/org/freedesktop/ConsoleKit/Seat1, member=SessionRemoved
D: module-console-kit.c: dbus: interface=org.freedesktop.ConsoleKit.Seat, path=/org/freedesktop/ConsoleKit/Seat1, member=SessionRemoved
D: module-hal-detect.c: dbus: interface=org.freedesktop.ConsoleKit.Seat, path=/org/freedesktop/ConsoleKit/Seat1, member=SessionRemoved
D: module-console-kit.c: dbus: interface=org.freedesktop.ConsoleKit.Seat, path=/org/freedesktop/ConsoleKit/Seat1, member=SessionRemoved

```

From there it's just hanging.

Please help, if you have any clue as what I could possibly do. I've been through most of the basic troubleshooting, but I don't find a solution for what to do when hardware doesn't show up in pulseaudio.

I'd appreciate any hints. Thanks.

---

### Post by zob on 2009-07-07
OK. Progress!

I found out that, for unknown reasons, pulseaudio needed to load a module, not loaded automatically on my system. That is the module-detect.

So I could manually load that pulseaudio-module by doing the following:

```
lars@ubuntu:~$ pactl load-module module-detect
18

```

And whoooooosh, my sound card showed up in pulseaudio output-tab. And sound there was. Glitching sound, but I will figure that out.

Know I just need to make pulseaudio load that module-detect at boot. Any ideas?

I'm winning this battle, finally!

---

### Post by zob on 2009-07-07
Well, well.

Not winning just yet.

I made a change in the /etc/pulse/default.pa to:

```
### Automatically load driver modules depending on the hardware available
## .ifexists module-hal-detect.so
## load-module module-hal-detect tsched=0
## .else
### Alternatively use the static hardware detection module (for systems that
### lack HAL support)
load-module module-detect
## .endif
```

Commenting out the "if-part" of the script (that obviously hindered the module-detect part to get loaded on my system), actually made my sound card show up in the pulseaudio volume control after reboot.

But the problem remains. When I load it manually it works. But this way, I get some kind of "connection terminated" error.

Any ideas?

I'll be working on this.

Also strange that the .ifexists... .endif part didn't let module-detect get loaded. I tried to load the module-hal-detect tsched=0 manually, but couldn't.

---

### Post by malrost on 2009-07-07
I'm also on Ubuntu 9.04 (amd64) w/ a HDSP 9632. It's on a Gigabyte board w/ onboard intel-snd-hda 5.1 surround sound integrated card.

Don't bother w/ pulse for this card. See my config frustrations, w/ screenshots, [here.]("http://ubuntuforums.org/showpost.php?p=7578331&postcount=10") In short, use jack, alsa, and a realtime kernel. Installing the ubuntustudio-audio and ubuntustudio-audio-plugins apps should do it.

Check /etc/modprobe.d/alsa-base.conf to determine which modules are set in it. At a minimum, it needs this line:

```
options snd-hda-intel
```

my alsa-base.conf reads this way, to consistently get the HDSP to load as HW:1,0:

```
# added to ensure consistent order
options snd-hda-intel index=0
options snd-hdsp index=1
```


Install and use HDSPConf and HDSPMixer, also. The first place you'll notice the signal from the 9632 is the HDSPMixer. HDSPConf controls overlap w/ jack settings, somewhat. Make sure they match.

From there it's just a matter of getting the jack config correct: proper device (mine is "hw:1,0"), proper device settings (latency, sampling rate), then proper input/output settings (turn everything on until something works).

Pulseaudio is to me still teh suck, but apparently there's a pulse-alsa module that allows pulse devices to show up in jack, which would improve the situation.

---

### Post by zob on 2009-07-07
Hi malrost.

Thanks a lot for joining my troubleshooting.
I followed your advice. Uninstalled pulseaudio. Chose Alsa in gnome sound setting. And installed the ubuntu-studio stuff.

I do get some sound now. There are terrible glitches though. Do you know how to fix that?

Also I will have to read up on Jack. I'm new to this. And I don't know how "to use jack" or what it means.

I've also tried to configure jack via jack-control. However it doesn't seem to let me choose the interface. It is greyed out. You know the place where you had to choose the hw:1,0 option. And ideas?

Thanks again malrost. I'm getting closer. And goodbye pulse, for now.

---

### Post by Virnik on 2009-08-28
it happened to me in Karmic Koala too, and I found out why it is broken. pulse tries to load up module-udev-detect, which is still failing. so, in /etc/pulse/default.pa, comment whole ¨if¨ statement about it, and leave only module-detect, which is still working fine.

---

### Post by zob on 2009-08-28
Very interesting indeed Virnik. I gave up on pulse-audio. But it is cool, and I would love to get it to work with the HDSP 9632.

You didn't mention your sound card. Is it RME HDSP as well?
Well, I guess I'm going to try this anyway as soon as possible.

Thanks a lot Virnik. I will leave a report here when I know if it works with my HDSP.

---

### Post by zob on 2009-08-28
Well well. I think I've been here before. I don't think it gets loaded as I only have a NULL output in the pulse volume control applet.

Please tell me Virnik if your card is a RME HDSP card.
If it's not, I don't think it's worth working to hard on this. As malrost stated in his comment that card simply doesn't work with pulseaudio.

I'm quite sure it's just because pulse doesn't recognize the snd_hdsp module which by the way IS loaded. And my PC can make a sound, but only if I manually direct the sound around pulse (to ALSA). So no reason for having it installed then.

I'm very interested to hear from you Virkin.

By the way. I would like to file this as a bug. Maybe pulse developers will actually correct it, even though we might not be as many as people with Creative sound cards. Where do I go and report it?

---

### Post by thockin on 2010-01-04
Similar problems with HDSP + Multiface on Ubuntu 9.10.  See:

[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/483237](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/483237)

I'd love to get ALSA/Pulse people working on this.  Was there any progress on it?

---

### Post by zob on 2010-01-20
Actually there was just a short time ago. Some clever pulseaudio user called thockin found a solution that worked for me:
[http://pulseaudio.org/ticket/764](http://pulseaudio.org/ticket/764)

Two lines for:
/etc/pulse/default.pa

The two lines are to load the module:
```
load-module module-alsa-sink device_id=0 tsched=0
load-module module-alsa-source device_id=0 tsched=0
```

Everything else under the headlines of: ### Load audio drivers statically... and ### Automatically load driver modules depending on the hardware available is commented out.

Only the two lines as mentioned are not.

This makes the driver modules for the hdsp load and gets rid af crackling sound. I think you will still have to load the hdspmixer at boot.

The hdspmixer came with a alsa-package. I don't recall which, but it is one of the following (which are all installed one my system) alsa-base                                                                                                                                                                                               
alsa-firmware                                                                                                                                                                    
alsa-firmware-loaders                                                                                                                                                                                               
alsa-tools                                                                                                                                                                           
alsa-tools-gui                                                                                                                                                                    
alsa-utils

Then I made a hdsp startup script which i set to run automatically at startup from the System-settings-startup programs (or whatever it is called, my system speaks danish).

The script is saved as a sh-file and is made executable and contains the following:
```
#!/bin/sh
hdsploader
hdspmixer & sleep 3 && killall hdspmixer
```
The killall-thing is to make the mixer-gui go away, or else it will just sit there.

Please ask if you have any doubts.

I hope I remembered it all (I have done a lot of thing, most were dead ends, and I think this is all that is really necesary).

Now I'm on 9.10. I don't know if it works on earlier versions.

---

### Post by damian.obrien on 2010-03-26
This worked for me!  Thanks.

I did: 

#sudo killall -9 pulseaudio

#sudo pactl load-module module-detect

#pulseaudio -v


Thanks again!

---

