---
title: "PulseAudio No Audio"
date: 2008-12-27
forum: Multimedia Software
---

### Post by jlr4u on 2008-12-27
I am having problems with PulseAudio.

Running Ubuntu 8.04.1 on and old AMD Athlon(tm) XP 3200+

I have no audio running:

```
cat /dev/video0 > /tmp/test_capture.mpg
vlc /tmp/test_capture.mpg 
```
aplay -l returns:
```
**** List of PLAYBACK Hardware Devices ****
card 0: nForce2 [NVidia nForce2], device 0: Intel ICH [NVidia nForce2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: nForce2 [NVidia nForce2], device 2: Intel ICH - IEC958 [NVidia nForce2 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```
pkill pulseaudio; sleep 2; pulseaudio -vv
```
I: main.c: We're in the group 'pulse-rt', allowing real-time and high-priority scheduling.
I: core-util.c: Successfully gained nice level -11.
[COLOR="Red"][B]W: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
W: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted[/B][/COLOR]
I: main.c: This is PulseAudio 0.9.10
I: main.c: Page size is 4096 bytes
I: main.c: Fresh high-resolution timers available! Bon appetit!
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9/modules/module-hal-detect.so': failure
I: module-alsa-sink.c: Successfully opened device hw:0.
I: module-alsa-sink.c: Successfully enabled mmap() mode.
I: alsa-util.c: Successfully attached to mixer 'hw:0'
I: alsa-util.c: Using mixer control "Master".
I: sink.c: Created sink 0 "alsa_output.hw_0" with sample spec "s16le 2ch 44100Hz"
I: source.c: Created source 0 "alsa_output.hw_0.monitor" with sample spec "s16le 2ch 44100Hz"
I: module-alsa-sink.c: Using 8 fragments of size 880 bytes.
I: alsa-util.c: All 2 channels can be mapped to mixer channels. Using hardware volume control.
D: module-alsa-sink.c: Thread starting up
D: rtpoll.c: Acquired POSIX realtime signal SIGRTMIN+29
I: module-alsa-sink.c: Starting playback.
I: module.c: Loaded "module-alsa-sink" (index: #0; argument: "device=hw:0").
I: module-alsa-source.c: Successfully opened device hw:0.
I: module-alsa-source.c: Successfully enabled mmap() mode.
I: alsa-util.c: Successfully attached to mixer 'hw:0'
I: alsa-util.c: Using mixer control "Capture".
I: source.c: Created source 1 "alsa_input.hw_0" with sample spec "s16le 2ch 44100Hz"
I: module-alsa-source.c: Using 8 fragments of size 880 bytes.
I: alsa-util.c: All 2 channels can be mapped to mixer channels. Using hardware volume control.
D: module-alsa-source.c: Thread starting up
D: rtpoll.c: Acquired POSIX realtime signal SIGRTMIN+28
I: module.c: Loaded "module-alsa-source" (index: #1; argument: "device=hw:0").
I: module-detect.c: loaded 2 modules.
I: module.c: Loaded "module-detect" (index: #2; argument: "").
**[COLOR="Red"]D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9/modules/module-esound-protocol-unix.so': failure[/COLOR]**
I: protocol-native.c: loading cookie from disk.
I: module.c: Loaded "module-native-protocol-unix" (index: #3; argument: "").
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9/modules/module-gconf.so': success
I: module.c: Loaded "module-gconf" (index: #4; argument: "").
I: module.c: Loaded "module-volume-restore" (index: #5; argument: "").
D: module-default-device-restore.c: Restored default sink 'alsa_output.hw_0'.
D: core-subscribe.c: dropped redundant event.
D: module-default-device-restore.c: Restored default source 'alsa_input.hw_0'.
I: module.c: Loaded "module-default-device-restore" (index: #6; argument: "").
I: module.c: Loaded "module-rescue-streams" (index: #7; argument: "").
D: module-suspend-on-idle.c: Sink alsa_output.hw_0 becomes idle.
D: module-suspend-on-idle.c: Source alsa_output.hw_0.monitor becomes idle.
D: module-suspend-on-idle.c: Source alsa_input.hw_0 becomes idle.
I: module.c: Loaded "module-suspend-on-idle" (index: #8; argument: "").
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9/modules/module-x11-publish.so': failure
I: main.c: Daemon startup complete.
I: module.c: Unloading "module-detect" (index: #2).
I: module.c: Unloaded "module-detect" (index: #2).
I: module-suspend-on-idle.c: Source alsa_input.hw_0 idle for too long, suspending ...
I: module-alsa-source.c: Device suspended...
I: module-suspend-on-idle.c: Source alsa_output.hw_0.monitor idle for too long, suspending ...
I: module-suspend-on-idle.c: Sink alsa_output.hw_0 idle for too long, suspending ...
I: module-alsa-sink.c: Device suspended...
[COLOR="Red"]**E: module-gconf.c: Unable to read or parse data from client.**[/COLOR]
I: module.c: Unloading "module-gconf" (index: #4).
I: module.c: Unloaded "module-gconf" (index: #4).
I: main.c: Got signal SIGINT.
I: main.c: Exiting.
I: main.c: Daemon shutdown initiated.
I: module.c: Unloading "module-alsa-sink" (index: #0).
D: module-rescue-streams.c: No sink inputs to move away.
D: module-rescue-streams.c: No source outputs to move away.
D: module-alsa-sink.c: Thread shutting down
I: sink.c: Freeing sink 0 "alsa_output.hw_0"
I: source.c: Freeing source 0 "alsa_output.hw_0.monitor"
I: module.c: Unloaded "module-alsa-sink" (index: #0).
I: module.c: Unloading "module-alsa-source" (index: #1).
D: module-rescue-streams.c: No source outputs to move away.
D: module-alsa-source.c: Thread shutting down
I: source.c: Freeing source 1 "alsa_input.hw_0"
I: module.c: Unloaded "module-alsa-source" (index: #1).
I: module.c: Unloading "module-native-protocol-unix" (index: #3).
I: module.c: Unloaded "module-native-protocol-unix" (index: #3).
I: module.c: Unloading "module-volume-restore" (index: #5).
I: module.c: Unloaded "module-volume-restore" (index: #5).
I: module.c: Unloading "module-default-device-restore" (index: #6).
I: module.c: Unloaded "module-default-device-restore" (index: #6).
I: module.c: Unloading "module-rescue-streams" (index: #7).
I: module.c: Unloaded "module-rescue-streams" (index: #7).
I: module.c: Unloading "module-suspend-on-idle" (index: #8).
I: module.c: Unloaded "module-suspend-on-idle" (index: #8).
I: main.c: Daemon terminated.

```
What do I do?
Thanks

---

