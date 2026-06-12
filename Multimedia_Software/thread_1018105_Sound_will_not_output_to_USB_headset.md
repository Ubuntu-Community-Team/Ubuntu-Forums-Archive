---
title: "Sound will not output to USB headset"
date: 2008-12-21
forum: Multimedia Software
---

### Post by noerrorsfound on 2008-12-21
The USB headset is set as the default device in PulseAudio's volume control, yet the sound test at System | Preferences | Sound outputs to my speakers, whether I've got "Autodetect" or "PulseAudio Sound Server" selected. Selecting "USB Audio" and trying to test the sound yields the following:
```
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open audio device for playback.
```
I've gone through some PulseAudio guide and was given commands to get some output.

Output of _aplay -l_:
```

**** List of PLAYBACK Hardware Devices ****
card 0: CK804 [NVidia CK804], device 0: Intel ICH [NVidia CK804]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CK804 [NVidia CK804], device 2: Intel ICH - IEC958 [NVidia CK804 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: default [Microsoft LifeChat LX-3000 ], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```Output of _pkill pulseaudio; sleep 2; pulseaudio -vv_:
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
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_10de_59_sound_card_0_alsa_playback_2
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_10de_59_sound_card_0_alsa_capture_1
D: module-hal-detect.c: Loading module-alsa-sink with arguments 'device_id=0 sink_name=alsa_output.pci_10de_59_sound_card_0_alsa_playback_0'
D: alsa-util.c: Trying front:0...
W: alsa-util.c: Device front:0 doesn't support 44100 Hz, changed to 48000 Hz.
I: module-alsa-sink.c: Successfully opened device front:0.
I: module-alsa-sink.c: Successfully enabled mmap() mode.
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL front:0
I: alsa-util.c: Unable to attach to mixer front:0: No such file or directory
I: alsa-util.c: Successfully attached to mixer 'hw:0'
I: alsa-util.c: Using mixer control "Master".
I: sink.c: Created sink 0 "alsa_output.pci_10de_59_sound_card_0_alsa_playback_0" with sample spec "s16le 2ch 48000Hz"
I: source.c: Created source 0 "alsa_output.pci_10de_59_sound_card_0_alsa_playback_0.monitor" with sample spec "s16le 2ch 48000Hz"
I: module-alsa-sink.c: Using 8 fragments of size 1764 bytes.
I: alsa-util.c: All 2 channels can be mapped to mixer channels. Using hardware volume control.
D: module-alsa-sink.c: Thread starting up
D: rtpoll.c: Acquired POSIX realtime signal SIGRTMIN+29
I: module-alsa-sink.c: Starting playback.
I: module.c: Loaded "module-alsa-sink" (index: #0; argument: "device_id=0 sink_name=alsa_output.pci_10de_59_sound_card_0_alsa_playback_0").
D: module-hal-detect.c: Loading module-alsa-source with arguments 'device_id=0 source_name=alsa_input.pci_10de_59_sound_card_0_alsa_capture_0'
D: alsa-util.c: Trying front:0...
W: alsa-util.c: Device front:0 doesn't support 44100 Hz, changed to 48000 Hz.
I: module-alsa-source.c: Successfully opened device front:0.
I: module-alsa-source.c: Successfully enabled mmap() mode.
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL front:0
I: alsa-util.c: Unable to attach to mixer front:0: No such file or directory
I: alsa-util.c: Successfully attached to mixer 'hw:0'
I: alsa-util.c: Using mixer control "Capture".
I: source.c: Created source 1 "alsa_input.pci_10de_59_sound_card_0_alsa_capture_0" with sample spec "s16le 2ch 48000Hz"
I: module-alsa-source.c: Using 8 fragments of size 1764 bytes.
I: alsa-util.c: All 2 channels can be mapped to mixer channels. Using hardware volume control.
D: module-alsa-source.c: Thread starting up
D: rtpoll.c: Acquired POSIX realtime signal SIGRTMIN+28
I: module.c: Loaded "module-alsa-source" (index: #1; argument: "device_id=0 source_name=alsa_input.pci_10de_59_sound_card_0_alsa_capture_0").
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_10de_59_sound_card_0_alsa_control__1
D: module-hal-detect.c: Loading module-alsa-sink with arguments 'device_id=1 sink_name=alsa_output.usb_device_45e_70f_noserial_if0_sound_card_0_alsa_playback_0'
D: alsa-util.c: Trying front:1...
I: module-alsa-sink.c: Successfully opened device front:1.
I: module-alsa-sink.c: Successfully enabled mmap() mode.
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL front:1
I: alsa-util.c: Unable to attach to mixer front:1: No such file or directory
I: alsa-util.c: Successfully attached to mixer 'hw:1'
I: alsa-util.c: Cannot find mixer control "Master".
W: alsa-util.c: Cannot find fallback mixer control "PCM".
I: sink.c: Created sink 1 "alsa_output.usb_device_45e_70f_noserial_if0_sound_card_0_alsa_playback_0" with sample spec "s16le 2ch 44100Hz"
I: source.c: Created source 2 "alsa_output.usb_device_45e_70f_noserial_if0_sound_card_0_alsa_playback_0.monitor" with sample spec "s16le 2ch 44100Hz"
I: module-alsa-sink.c: Using 8 fragments of size 1764 bytes.
D: module-alsa-sink.c: Thread starting up
D: rtpoll.c: Acquired POSIX realtime signal SIGRTMIN+27
I: module-alsa-sink.c: Starting playback.
I: module.c: Loaded "module-alsa-sink" (index: #2; argument: "device_id=1 sink_name=alsa_output.usb_device_45e_70f_noserial_if0_sound_card_0_alsa_playback_0").
D: module-hal-detect.c: Loading module-alsa-source with arguments 'device_id=1 source_name=alsa_input.usb_device_45e_70f_noserial_if0_sound_card_0_alsa_capture_0'
D: alsa-util.c: Trying front:1...
I: alsa-util.c: PCM device front:1 refused our hw parameters: Invalid argument
D: alsa-util.c: Trying surround40:1...
I: alsa-util.c: PCM device surround40:1 refused our hw parameters: Invalid argument
D: alsa-util.c: Trying surround41:1...
I: alsa-util.c: PCM device surround41:1 refused our hw parameters: Invalid argument
D: alsa-util.c: Trying surround50:1...
I: alsa-util.c: PCM device surround50:1 refused our hw parameters: Invalid argument
D: alsa-util.c: Trying surround51:1...
I: alsa-util.c: PCM device surround51:1 refused our hw parameters: Invalid argument
D: alsa-util.c: Trying surround71:1...
I: alsa-util.c: PCM device surround71:1 refused our hw parameters: Invalid argument
D: alsa-util.c: Trying hw:1 as last resort...
W: alsa-util.c: Device hw:1 doesn't support 2 channels, changed to 1.
I: module-alsa-source.c: Successfully opened device hw:1.
I: module-alsa-source.c: Successfully enabled mmap() mode.
I: alsa-util.c: Successfully attached to mixer 'hw:1'
I: alsa-util.c: Cannot find mixer control "Capture".
I: alsa-util.c: Using mixer control "Mic".
I: source.c: Created source 3 "alsa_input.usb_device_45e_70f_noserial_if0_sound_card_0_alsa_capture_0" with sample spec "s16le 1ch 44100Hz"
I: module-alsa-source.c: Using 8 fragments of size 882 bytes.
I: alsa-util.c: All 1 channels can be mapped to mixer channels. Using hardware volume control.
D: module-alsa-source.c: Thread starting up
D: rtpoll.c: Acquired POSIX realtime signal SIGRTMIN+26
I: module.c: Loaded "module-alsa-source" (index: #3; argument: "device_id=1 source_name=alsa_input.usb_device_45e_70f_noserial_if0_sound_card_0_alsa_capture_0").
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/usb_device_45e_70f_noserial_if0_sound_card_0_alsa_control__1
I: module-hal-detect.c: Loaded 4 modules.
I: module.c: Loaded "module-hal-detect" (index: #4; argument: "").
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9/modules/module-esound-protocol-unix.so': success
I: module.c: Loaded "module-esound-protocol-unix" (index: #5; argument: "").
I: protocol-native.c: loading cookie from disk.
I: module.c: Loaded "module-native-protocol-unix" (index: #6; argument: "").
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9/modules/module-gconf.so': success
I: module.c: Loaded "module-gconf" (index: #7; argument: "").
I: module.c: Loaded "module-volume-restore" (index: #8; argument: "").
D: module-default-device-restore.c: Restored default sink 'alsa_output.usb_device_45e_70f_noserial_if0_sound_card_0_alsa_playback_0'.
D: core-subscribe.c: dropped redundant event.
D: module-default-device-restore.c: Restored default source 'alsa_input.pci_10de_59_sound_card_0_alsa_capture_0'.
I: module.c: Loaded "module-default-device-restore" (index: #9; argument: "").
I: module.c: Loaded "module-rescue-streams" (index: #10; argument: "").
D: module-suspend-on-idle.c: Sink alsa_output.pci_10de_59_sound_card_0_alsa_playback_0 becomes idle.
D: module-suspend-on-idle.c: Sink alsa_output.usb_device_45e_70f_noserial_if0_sound_card_0_alsa_playback_0 becomes idle.
D: module-suspend-on-idle.c: Source alsa_output.pci_10de_59_sound_card_0_alsa_playback_0.monitor becomes idle.
D: module-suspend-on-idle.c: Source alsa_input.pci_10de_59_sound_card_0_alsa_capture_0 becomes idle.
D: module-suspend-on-idle.c: Source alsa_output.usb_device_45e_70f_noserial_if0_sound_card_0_alsa_playback_0.monitor becomes idle.
D: module-suspend-on-idle.c: Source alsa_input.usb_device_45e_70f_noserial_if0_sound_card_0_alsa_capture_0 becomes idle.
I: module.c: Loaded "module-suspend-on-idle" (index: #11; argument: "").
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9/modules/module-x11-publish.so': success
D: module-x11-publish.c: using already loaded auth cookie.
I: module.c: Loaded "module-x11-publish" (index: #12; argument: "").
I: main.c: Daemon startup complete.
D: module-hal-detect.c: dbus: interface=org.freedesktop.DBus, path=/org/freedesktop/DBus, member=NameAcquired
I: module-suspend-on-idle.c: Source alsa_input.usb_device_45e_70f_noserial_if0_sound_card_0_alsa_capture_0 idle for too long, suspending ...
I: module-alsa-source.c: Device suspended...
I: module-suspend-on-idle.c: Source alsa_output.usb_device_45e_70f_noserial_if0_sound_card_0_alsa_playback_0.monitor idle for too long, suspending ...
I: module-suspend-on-idle.c: Source alsa_input.pci_10de_59_sound_card_0_alsa_capture_0 idle for too long, suspending ...
I: module-alsa-source.c: Device suspended...
I: module-suspend-on-idle.c: Source alsa_output.pci_10de_59_sound_card_0_alsa_playback_0.monitor idle for too long, suspending ...
I: module-suspend-on-idle.c: Sink alsa_output.usb_device_45e_70f_noserial_if0_sound_card_0_alsa_playback_0 idle for too long, suspending ...
I: module-alsa-sink.c: Device suspended...
I: module-suspend-on-idle.c: Sink alsa_output.pci_10de_59_sound_card_0_alsa_playback_0 idle for too long, suspending ...
I: module-alsa-sink.c: Device suspended...

```

---

