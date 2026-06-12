---
title: "Pulseaudio = $%&amp;@#$!!!!"
date: 2008-07-03
forum: Multimedia Software
---

### Post by slackboxing on 2008-07-03
After reading and following many guides and docs for either fixing or optimizing pulse audio, I still have the same problem. Pulseaudio still crashes on me every 5 minutes or so while playing audio even after restarting pulseaudio. Doesn't matter if it is amarok, exaile, vlc...etc etc. The most recent guide I looked @ was [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578) . After following that guide and the initial reboot, Everything worked flawlessly. Next reboot, pulse goes back to it's crashing self. Hopefully someone has experienced this same problem and knows a possible fix? Also, I have 8.04 installed on my T60 laptop, no problems whatsoever. 

System: 

Ubuntu 8.04
04:05.0 Multimedia audio controller: Creative Labs SB Audigy LS
Linux zimBuntu 2.6.24-18-generic #1 SMP Wed May 28 20:27:26 UTC 2008 i686 GNU/Linux


You'll notice the operation failed pieces below. Seems to be just because I didn't start it with sudo powers. It still fails the same.

```
penfold@zimBuntu:~$ pulseaudio -vv
I: main.c: We're in the group 'pulse-rt', allowing real-time and high-priority scheduling.
I: core-util.c: Successfully gained nice level -11.
I: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
W: main.c: RLIMIT_RTPRIO failed: Operation not permitted
W: pid.c: Stale PID file, overwriting.
I: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
I: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
I: main.c: This is PulseAudio 0.9.10
I: main.c: Page size is 4096 bytes
I: main.c: Fresh high-resolution timers available! Bon appetit!
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9/modules/module-hal-detect.so': success
I: module-hal-detect.c: Trying capability alsa
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/computer_alsa_timer
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/computer_alsa_sequencer
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_1102_7_sound_card_0_alsa_playback_3
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_1102_7_sound_card_0_alsa_capture_3
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_1102_7_sound_card_0_alsa_playback_2
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_1102_7_sound_card_0_alsa_capture_2
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_1102_7_sound_card_0_alsa_playback_1
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_1102_7_sound_card_0_alsa_capture_1
D: module-hal-detect.c: Loading module-alsa-sink with arguments 'device_id=0 sink_name=alsa_output.pci_1102_7_sound_card_0_alsa_playback_0'
D: alsa-util.c: Trying front:0...
W: alsa-util.c: Device front:0 doesn't support 44100 Hz, changed to 48000 Hz.
I: module-alsa-sink.c: Successfully opened device front:0.
I: module-alsa-sink.c: Successfully enabled mmap() mode.
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL front:0
I: alsa-util.c: Unable to attach to mixer front:0: No such file or directory
I: alsa-util.c: Successfully attached to mixer 'hw:0'
I: alsa-util.c: Cannot find mixer control "Master".
W: alsa-util.c: Cannot find fallback mixer control "PCM".
I: sink.c: Created sink 0 "alsa_output.pci_1102_7_sound_card_0_alsa_playback_0" with sample spec "s16le 2ch 48000Hz"
I: source.c: Created source 0 "alsa_output.pci_1102_7_sound_card_0_alsa_playback_0.monitor" with sample spec "s16le 2ch 48000Hz"
I: module-alsa-sink.c: Using 8 fragments of size 896 bytes.
D: module-alsa-sink.c: Thread starting up
I: core-util.c: Successfully enabled SCHED_FIFO scheduling for thread, with priority 5.
D: rtpoll.c: Acquired POSIX realtime signal SIGRTMIN+29
I: module-alsa-sink.c: Starting playback.
I: module.c: Loaded "module-alsa-sink" (index: #0; argument: "device_id=0 sink_name=alsa_output.pci_1102_7_sound_card_0_alsa_playback_0").
D: module-hal-detect.c: Loading module-alsa-source with arguments 'device_id=0 source_name=alsa_input.pci_1102_7_sound_card_0_alsa_capture_0'
D: alsa-util.c: Trying front:0...
I: module-alsa-source.c: Successfully opened device front:0.
I: module-alsa-source.c: Successfully enabled mmap() mode.
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL front:0
I: alsa-util.c: Unable to attach to mixer front:0: No such file or directory
I: alsa-util.c: Successfully attached to mixer 'hw:0'
I: alsa-util.c: Cannot find mixer control "Capture".
I: alsa-util.c: Using mixer control "Mic".
I: source.c: Created source 1 "alsa_input.pci_1102_7_sound_card_0_alsa_capture_0" with sample spec "s16le 2ch 44100Hz"
I: module-alsa-source.c: Using 2 fragments of size 896 bytes.
I: alsa-util.c: All 2 channels can be mapped to mixer channels. Using hardware volume control.
D: module-alsa-source.c: Thread starting up
I: core-util.c: Successfully enabled SCHED_FIFO scheduling for thread, with priority 5.
D: rtpoll.c: Acquired POSIX realtime signal SIGRTMIN+28
I: module.c: Loaded "module-alsa-source" (index: #1; argument: "device_id=0 source_name=alsa_input.pci_1102_7_sound_card_0_alsa_capture_0").
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_1102_7_sound_card_0_alsa_midi_0
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_1102_7_sound_card_0_alsa_control__1
I: module-hal-detect.c: Loaded 2 modules.
I: module.c: Loaded "module-hal-detect" (index: #2; argument: "").
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9/modules/module-esound-protocol-unix.so': success
I: module.c: Loaded "module-esound-protocol-unix" (index: #3; argument: "").
I: protocol-native.c: loading cookie from disk.
I: module.c: Loaded "module-native-protocol-unix" (index: #4; argument: "").
I: module.c: Loaded "module-volume-restore" (index: #5; argument: "").
D: module-default-device-restore.c: Restored default sink 'alsa_output.pci_1102_7_sound_card_0_alsa_playback_0'.
D: core-subscribe.c: dropped redundant event.
D: module-default-device-restore.c: Restored default source 'alsa_input.pci_1102_7_sound_card_0_alsa_capture_0'.
I: module.c: Loaded "module-default-device-restore" (index: #6; argument: "").
I: module.c: Loaded "module-rescue-streams" (index: #7; argument: "").
D: module-suspend-on-idle.c: Sink alsa_output.pci_1102_7_sound_card_0_alsa_playback_0 becomes idle.
D: module-suspend-on-idle.c: Source alsa_output.pci_1102_7_sound_card_0_alsa_playback_0.monitor becomes idle.
D: module-suspend-on-idle.c: Source alsa_input.pci_1102_7_sound_card_0_alsa_capture_0 becomes idle.
I: module.c: Loaded "module-suspend-on-idle" (index: #8; argument: "").
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9/modules/module-gconf.so': success
D: module-gconf.c: Loading module 'module-combine' with args '' due to GConf configuration.
I: sink.c: Created sink 1 "combined" with sample spec "s16le 2ch 44100Hz"
I: source.c: Created source 2 "combined.monitor" with sample spec "s16le 2ch 44100Hz"
D: memblockq.c: memblockq requested: maxlength=174080, tlength=174080, base=4, prebuf=1, minreq=0
D: memblockq.c: memblockq sanitized: maxlength=174080, tlength=174080, base=4, prebuf=4, minreq=4
D: module-suspend-on-idle.c: Sink alsa_output.pci_1102_7_sound_card_0_alsa_playback_0 becomes busy.
I: resampler.c: Using resampler 'trivial'
I: resampler.c: Using s16le as working format.
I: sink-input.c: Created input 0 "Simultaneous output on ALSA PCM on front:0 (CA0106) via DMA" on alsa_output.pci_1102_7_sound_card_0_alsa_playback_0 with sample spec s16le 2ch 44100Hz and channel map front-left,front-right
I: module-combine.c: Master sink is now 'alsa_output.pci_1102_7_sound_card_0_alsa_playback_0'
D: module-combine.c: Thread starting up
I: core-util.c: Successfully enabled SCHED_FIFO scheduling for thread, with priority 6.
D: rtpoll.c: Acquired POSIX realtime signal SIGRTMIN+27
D: module-suspend-on-idle.c: Source combined.monitor becomes idle.
D: module-suspend-on-idle.c: Sink combined becomes idle.
I: module.c: Loaded "module-combine" (index: #9; argument: "").
I: module.c: Loaded "module-gconf" (index: #10; argument: "").
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9/modules/module-x11-publish.so': success
D: module-x11-publish.c: using already loaded auth cookie.
I: module.c: Loaded "module-x11-publish" (index: #11; argument: "").
I: main.c: Daemon startup complete.
D: module-hal-detect.c: dbus: interface=org.freedesktop.DBus, path=/org/freedesktop/DBus, member=NameAcquired
I: module-suspend-on-idle.c: Source alsa_input.pci_1102_7_sound_card_0_alsa_capture_0 idle for too long, suspending ...
I: module-alsa-source.c: Device suspended...
I: module-suspend-on-idle.c: Source alsa_output.pci_1102_7_sound_card_0_alsa_playback_0.monitor idle for too long, suspending ...
I: module-suspend-on-idle.c: Sink combined idle for too long, suspending ...
D: module-suspend-on-idle.c: Sink alsa_output.pci_1102_7_sound_card_0_alsa_playback_0 becomes idle.
D: module-suspend-on-idle.c: Sink alsa_output.pci_1102_7_sound_card_0_alsa_playback_0 becomes idle.
I: sink-input.c: Freeing output 0 "Simultaneous output on ALSA PCM on front:0 (CA0106) via DMA"
I: module-combine.c: No master selected, lacking suitable outputs.
I: module-combine.c: Device suspended...
I: module-suspend-on-idle.c: Source combined.monitor idle for too long, suspending ...
I: module-suspend-on-idle.c: Sink alsa_output.pci_1102_7_sound_card_0_alsa_playback_0 idle for too long, suspending ...
I: module-alsa-sink.c: Device suspended...
I: client.c: Created 0 "Native client (UNIX socket client)"
I: protocol-native.c: Got credentials: uid=1000 gid=1000 success=1
I: protocol-native.c: Enabled SHM for new connection
I: client.c: Client 0 changed name from "Native client (UNIX socket client)" to "amarokapp"
I: module-volume-restore.c: Restoring sink for <pulsecore/protocol-native.c$amarokapp>
I: module-volume-restore.c: Restoring volume for <pulsecore/protocol-native.c$amarokapp>
I: module-alsa-sink.c: Trying resume...
I: module-alsa-sink.c: Resumed successfully...
I: module-alsa-sink.c: Starting playback.
D: module-suspend-on-idle.c: Sink alsa_output.pci_1102_7_sound_card_0_alsa_playback_0 becomes idle.
D: module-suspend-on-idle.c: Sink alsa_output.pci_1102_7_sound_card_0_alsa_playback_0 becomes busy.
I: resampler.c: Using resampler 'trivial'
I: resampler.c: Using s16le as working format.
I: sink-input.c: Created input 1 "Simultaneous output on ALSA PCM on front:0 (CA0106) via DMA" on alsa_output.pci_1102_7_sound_card_0_alsa_playback_0 with sample spec s16le 2ch 44100Hz and channel map front-left,front-right
I: module-combine.c: Master sink is now 'alsa_output.pci_1102_7_sound_card_0_alsa_playback_0'
I: module-combine.c: Resumed successfully...
D: module-suspend-on-idle.c: Sink combined becomes idle.
D: module-suspend-on-idle.c: Sink combined becomes busy.
I: sink-input.c: Created input 2 "Audio Stream" on combined with sample spec s16le 2ch 44100Hz and channel map front-left,front-right
D: memblockq.c: memblockq requested: maxlength=132300, tlength=88200, base=4, prebuf=86436, minreq=1764
D: memblockq.c: memblockq sanitized: maxlength=132300, tlength=88200, base=4, prebuf=86436, minreq=1764
I: module-combine.c: [combined] target latency is 38541 usec.
I: module-combine.c: [combined] master alsa_output.pci_1102_7_sound_card_0_alsa_playback_0 latency 38541 usec.
I: module-combine.c: [Simultaneous output on ALSA PCM on front:0 (CA0106) via DMA] new rate is 44100 Hz; ratio is 1.000; latency is 38541 usec.
I: module-combine.c: [combined] target latency is 41104 usec.
I: module-combine.c: [combined] master alsa_output.pci_1102_7_sound_card_0_alsa_playback_0 latency 41104 usec.
I: module-combine.c: [Simultaneous output on ALSA PCM on front:0 (CA0106) via DMA] new rate is 44100 Hz; ratio is 1.000; latency is 41104 usec.
I: module-combine.c: [combined] target latency is 50187 usec.
I: module-combine.c: [combined] master alsa_output.pci_1102_7_sound_card_0_alsa_playback_0 latency 50187 usec.
I: module-combine.c: [Simultaneous output on ALSA PCM on front:0 (CA0106) via DMA] new rate is 44100 Hz; ratio is 1.000; latency is 50187 usec.
I: module-combine.c: [combined] target latency is 37333 usec.
I: module-combine.c: [combined] master alsa_output.pci_1102_7_sound_card_0_alsa_playback_0 latency 37333 usec.
I: module-combine.c: [Simultaneous output on ALSA PCM on front:0 (CA0106) via DMA] new rate is 44100 Hz; ratio is 1.000; latency is 37333 usec.
I: module-combine.c: [combined] target latency is 37687 usec.
I: module-combine.c: [combined] master alsa_output.pci_1102_7_sound_card_0_alsa_playback_0 latency 37687 usec.
I: module-combine.c: [Simultaneous output on ALSA PCM on front:0 (CA0106) via DMA] new rate is 44100 Hz; ratio is 1.000; latency is 37687 usec.
Soft CPU time limit exhausted, terminating.
Hard CPU time limit exhausted, terminating forcibly.
Aborted
```

Thanks.

---

### Post by steveneddy on 2008-07-03
Have you tried just using ALSA?

---

### Post by slackboxing on 2008-07-03
> **steveneddy said:**
> Have you tried just using ALSA?
I know that is an option. I would like to take advantage of the features of pulse if possible.

---

### Post by steveneddy on 2008-07-04
> **slackboxing said:**
> I know that is an option. I would like to take advantage of the features of pulse if possible.

I understand. 

But until you get your pulse audio issues corrected, ALSA is still a very good alternative. At least you could listen to music again.

---

