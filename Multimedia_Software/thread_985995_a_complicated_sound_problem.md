---
title: "a complicated sound problem"
date: 2008-11-18
forum: Multimedia Software
---

### Post by randName on 2008-11-18
I had my laptop running on Ibex (dual-boot) for 2 weeks already, and I had no problems with sound so far (excluding the small disagreement with Stepmania which had been long solved), but just today after rebooting I had no sound coming from the login screen and no startup sound. I played something on VLC and there was no sound (even with earphones) Pidgin also stopped producing sounds.

After further testing I found that the beeps caused by either typing in the wrong places or backspacing where you shouldn't be were still there, and adjustable with the volume. Of course none of my channels were muted or low.

I went through most of the troubleshooters and all checks indicated all systems go, but still no sound. I actually did not expect much results as my problem was rather different.

Then I booted into XP and my sound worked normally. Leaving my laptop off for a while to rest did not solve the problem.

I did nothing significant to the sound recently, other than the troubleshooting steps that I went through. And even now as I check there are no more beeps.

Any help would be very much appreciated (my Anime is waiting lol).

---

### Post by psyke83 on 2008-11-18
> **randName said:**
> I had my laptop running on Ibex (dual-boot) for 2 weeks already, and I had no problems with sound so far (excluding the small disagreement with Stepmania which had been long solved), but just today after rebooting I had no sound coming from the login screen and no startup sound. I played something on VLC and there was no sound (even with earphones) Pidgin also stopped producing sounds.

After further testing I found that the beeps caused by either typing in the wrong places or backspacing where you shouldn't be were still there, and adjustable with the volume. Of course none of my channels were muted or low.

I went through most of the troubleshooters and all checks indicated all systems go, but still no sound. I actually did not expect much results as my problem was rather different.

Then I booted into XP and my sound worked normally. Leaving my laptop off for a while to rest did not solve the problem.

I did nothing significant to the sound recently, other than the troubleshooting steps that I went through. And even now as I check there are no more beeps.

Any help would be very much appreciated (my Anime is waiting lol).

Check the PCM mixer level:
```
$ alsamixer -Dhw
```

A lot of Intrepid users are experiencing a bug where it gets reset to 0%.

If you're using Intrepid (or Hardy), you may also want to check the [PulseAudio Fixes]("http://ubuntuforums.org/showthread.php?t=789578") guide.

---

### Post by randName on 2008-11-18
Erm, my PCM is set to full (like I did in the normal Volume Control panel)

Following the PulseAudio guide did not really work. As stated in the final resort, I list many things:

Intrepid Ibex running on Dell Latitude D410 (forgot the architecture...)

Output from aplay -l
```
**** List of PLAYBACK Hardware Devices ****
card 0: ICH6 [Intel ICH6], device 0: Intel ICH [Intel ICH6]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH6 [Intel ICH6], device 4: Intel ICH - IEC958 [Intel ICH6 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

Output from pkill pulseaudio && sleep 2 && pulseaudio -vv
```
I: main.c: PolicyKit refuses acquire-high-priority privilige.
I: main.c: Called SUID root and real-time/high-priority scheduling was requested in the configuration. However, we lack the necessary priviliges:
I: main.c: We are not in group 'pulse-rt' and PolicyKit refuse to grant us priviliges. Dropping SUID again.
I: main.c: For enabling real-time scheduling please acquire the appropriate PolicyKit priviliges, or become a member of 'pulse-rt', or increase the RLIMIT_NICE/RLIMIT_RTPRIO resource limits for this user.
I: main.c: Note that real-time/high-priority scheduling is NOT normally required. If you experience crackling or other sound anomalies, consider one or more of the above solutions.
I: main.c: High-priority scheduling enabled in configuration but now allowed by policy. Disabling forcibly.
W: ltdl-bind-now.c: Failed to find original dlopen loader.
W: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
W: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
I: main.c: This is PulseAudio 0.9.10
I: main.c: Page size is 4096 bytes
I: main.c: Fresh high-resolution timers available! Bon appetit!
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9/modules/module-hal-detect.so': success
I: module-hal-detect.c: Trying capability alsa
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/computer_alsa_timer
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/computer_alsa_sequencer
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_8086_266e_sound_card_0_alsa_playback_4
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_8086_266e_sound_card_0_alsa_capture_3
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_8086_266e_sound_card_0_alsa_capture_2
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_8086_266e_sound_card_0_alsa_capture_1
D: module-hal-detect.c: Loading module-alsa-sink with arguments 'device_id=0 sink_name=alsa_output.pci_8086_266e_sound_card_0_alsa_playback_0'
D: alsa-util.c: Trying front:0...
I: module-alsa-sink.c: Successfully opened device front:0.
I: module-alsa-sink.c: Successfully enabled mmap() mode.
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL front:0
I: alsa-util.c: Unable to attach to mixer front:0: No such file or directory
I: alsa-util.c: Successfully attached to mixer 'hw:0'
I: alsa-util.c: Using mixer control "Master".
I: sink.c: Created sink 0 "alsa_output.pci_8086_266e_sound_card_0_alsa_playback_0" with sample spec "s16le 2ch 44100Hz"
I: source.c: Created source 0 "alsa_output.pci_8086_266e_sound_card_0_alsa_playback_0.monitor" with sample spec "s16le 2ch 44100Hz"
I: module-alsa-sink.c: Using 8 fragments of size 1760 bytes.
I: alsa-util.c: All 2 channels can be mapped to mixer channels. Using hardware volume control.
D: module-alsa-sink.c: Thread starting up
D: rtpoll.c: Acquired POSIX realtime signal SIGRTMIN+29
I: module-alsa-sink.c: Starting playback.
I: module.c: Loaded "module-alsa-sink" (index: #0; argument: "device_id=0 sink_name=alsa_output.pci_8086_266e_sound_card_0_alsa_playback_0").
D: module-hal-detect.c: Loading module-alsa-source with arguments 'device_id=0 source_name=alsa_input.pci_8086_266e_sound_card_0_alsa_capture_0'
D: alsa-util.c: Trying front:0...
I: module-alsa-source.c: Successfully opened device front:0.
I: module-alsa-source.c: Successfully enabled mmap() mode.
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL front:0
I: alsa-util.c: Unable to attach to mixer front:0: No such file or directory
I: alsa-util.c: Successfully attached to mixer 'hw:0'
I: alsa-util.c: Using mixer control "Capture".
I: source.c: Created source 1 "alsa_input.pci_8086_266e_sound_card_0_alsa_capture_0" with sample spec "s16le 2ch 44100Hz"
I: module-alsa-source.c: Using 8 fragments of size 1760 bytes.
I: alsa-util.c: All 2 channels can be mapped to mixer channels. Using hardware volume control.
D: module-alsa-source.c: Thread starting up
D: rtpoll.c: Acquired POSIX realtime signal SIGRTMIN+28
I: module.c: Loaded "module-alsa-source" (index: #1; argument: "device_id=0 source_name=alsa_input.pci_8086_266e_sound_card_0_alsa_capture_0").
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_8086_266e_sound_card_0_alsa_control__1
I: module-hal-detect.c: Loaded 2 modules.
I: module.c: Loaded "module-hal-detect" (index: #2; argument: "").
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9/modules/module-esound-protocol-unix.so': success
I: module.c: Loaded "module-esound-protocol-unix" (index: #3; argument: "").
I: protocol-native.c: loading cookie from disk.
I: module.c: Loaded "module-native-protocol-unix" (index: #4; argument: "").
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9/modules/module-gconf.so': success
I: module.c: Loaded "module-gconf" (index: #5; argument: "").
I: module.c: Loaded "module-volume-restore" (index: #6; argument: "").
D: module-default-device-restore.c: Restored default sink 'alsa_output.pci_8086_266e_sound_card_0_alsa_playback_0'.
D: core-subscribe.c: dropped redundant event.
D: module-default-device-restore.c: Restored default source 'alsa_input.pci_8086_266e_sound_card_0_alsa_capture_0'.
I: module.c: Loaded "module-default-device-restore" (index: #7; argument: "").
I: module.c: Loaded "module-rescue-streams" (index: #8; argument: "").
D: module-suspend-on-idle.c: Sink alsa_output.pci_8086_266e_sound_card_0_alsa_playback_0 becomes idle.
D: module-suspend-on-idle.c: Source alsa_output.pci_8086_266e_sound_card_0_alsa_playback_0.monitor becomes idle.
D: module-suspend-on-idle.c: Source alsa_input.pci_8086_266e_sound_card_0_alsa_capture_0 becomes idle.
I: module.c: Loaded "module-suspend-on-idle" (index: #9; argument: "").
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9/modules/module-x11-publish.so': success
D: module-x11-publish.c: using already loaded auth cookie.
I: module.c: Loaded "module-x11-publish" (index: #10; argument: "").
I: main.c: Daemon startup complete.
D: module-hal-detect.c: dbus: interface=org.freedesktop.DBus, path=/org/freedesktop/DBus, member=NameAcquired
I: module-suspend-on-idle.c: Source alsa_input.pci_8086_266e_sound_card_0_alsa_capture_0 idle for too long, suspending ...
I: module-alsa-source.c: Device suspended...
I: module-suspend-on-idle.c: Source alsa_output.pci_8086_266e_sound_card_0_alsa_playback_0.monitor idle for too long, suspending ...
I: module-suspend-on-idle.c: Sink alsa_output.pci_8086_266e_sound_card_0_alsa_playback_0 idle for too long, suspending ...
I: module-alsa-sink.c: Device suspended...
D: module-hal-detect.c: dbus: interface=org.freedesktop.Hal.Device, path=/org/freedesktop/Hal/devices/computer_power_supply_battery_BAT0, member=PropertyModified
D: module-hal-detect.c: dbus: interface=org.freedesktop.Hal.Device, path=/org/freedesktop/Hal/devices/computer_power_supply_battery_BAT0, member=PropertyModified
D: module-hal-detect.c: dbus: interface=org.freedesktop.Hal.Device, path=/org/freedesktop/Hal/devices/computer_power_supply_battery_BAT0, member=PropertyModified
D: module-hal-detect.c: dbus: interface=org.freedesktop.Hal.Device, path=/org/freedesktop/Hal/devices/computer_power_supply_battery_BAT0, member=PropertyModified
^CI: main.c: Got signal SIGINT.
I: main.c: Exiting.
I: main.c: Daemon shutdown initiated.
I: module.c: Unloading "module-alsa-sink" (index: #0).
D: module-rescue-streams.c: No sink inputs to move away.
D: module-rescue-streams.c: No source outputs to move away.
D: module-alsa-sink.c: Thread shutting down
I: sink.c: Freeing sink 0 "alsa_output.pci_8086_266e_sound_card_0_alsa_playback_0"
I: source.c: Freeing source 0 "alsa_output.pci_8086_266e_sound_card_0_alsa_playback_0.monitor"
I: module.c: Unloaded "module-alsa-sink" (index: #0).
I: module.c: Unloading "module-alsa-source" (index: #1).
D: module-rescue-streams.c: No source outputs to move away.
D: module-alsa-source.c: Thread shutting down
I: source.c: Freeing source 1 "alsa_input.pci_8086_266e_sound_card_0_alsa_capture_0"
I: module.c: Unloaded "module-alsa-source" (index: #1).
I: module.c: Unloading "module-hal-detect" (index: #2).
D: module-hal-detect.c: dbus: interface=org.freedesktop.DBus.Local, path=/org/freedesktop/DBus/Local, member=Disconnected
I: module.c: Unloaded "module-hal-detect" (index: #2).
I: module.c: Unloading "module-esound-protocol-unix" (index: #3).
I: module.c: Unloaded "module-esound-protocol-unix" (index: #3).
I: module.c: Unloading "module-native-protocol-unix" (index: #4).
I: module.c: Unloaded "module-native-protocol-unix" (index: #4).
I: module.c: Unloading "module-gconf" (index: #5).
I: module.c: Unloaded "module-gconf" (index: #5).
I: module.c: Unloading "module-volume-restore" (index: #6).
I: module.c: Unloaded "module-volume-restore" (index: #6).
I: module.c: Unloading "module-default-device-restore" (index: #7).
I: module.c: Unloaded "module-default-device-restore" (index: #7).
I: module.c: Unloading "module-rescue-streams" (index: #8).
I: module.c: Unloaded "module-rescue-streams" (index: #8).
I: module.c: Unloading "module-suspend-on-idle" (index: #9).
I: module.c: Unloaded "module-suspend-on-idle" (index: #9).
I: module.c: Unloading "module-x11-publish" (index: #10).
I: module.c: Unloaded "module-x11-publish" (index: #10).
I: main.c: Daemon terminated.

```

I noticed 3 bolded lines:
```
W: ltdl-bind-now.c: Failed to find original dlopen loader.
W: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
W: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted

```

Could that be part of the problem?

---

