---
title: "Broken audio in Hardy 64"
date: 2009-04-25
forum: Multimedia Software
---

### Post by afrodeity on 2009-04-25
My audio is broken. For some reason or other. I was trying to get the PSX emulator working and there is an issue there about pulseaudio. So I ran a script posted [here]("http://ubuntuforums.org/showpost.php?p=6127662&postcount=246"). 

```
#!/bin/bash
# A script to disable pulseaudio, run pSX, then renable pulseaudio

gksu /etc/init.d/pulseaudio stop
sleep 1
gksu killall pulseaudio         # Forcefully ends pulseaudio if still running
sleep 1
exec /usr/local/games/psx/pSX
sleep 1
gksu /etc/init.d/pulseaudio start
```

which turned the sound off, but it doesn't turn back on. I've tried everything. It could also be because I installed a number of updates in the process according to [this guide]("http://ubuntuforums.org/showthread.php?t=789578")  which might have kludged the sound. Alsamixer now only has one slider. I have also tried to update alsa with libsdl1.2debian-all but no luck

Please help.

---

### Post by afrodeity on 2009-04-25
afrodeity@afrodeity-desktop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: VT82xx [HDA VIA VT82xx], device 0: ALC662 Analog [ALC662 Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: VT82xx [HDA VIA VT82xx], device 1: ALC662 Digital [ALC662 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
afrodeity@afrodeity-desktop:~$

---

### Post by afrodeity on 2009-04-25
afrodeity@afrodeity-desktop:~$  pkill pulseaudio; sleep 2; pulseaudio -vv
I: main.c: We're in the group 'pulse-rt', allowing real-time and high-priority scheduling.
I: core-util.c: Successfully gained nice level -11.
W: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
W: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
I: main.c: This is PulseAudio 0.9.10
I: main.c: Page size is 4096 bytes
I: main.c: Fresh high-resolution timers available! Bon appetit!
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9/modules/module-hal-detect.so': success
I: module-hal-detect.c: Trying capability alsa
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/computer_alsa_timer
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/computer_alsa_sequencer
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_1106_3288_sound_card_0_alsa_playback_1
D: module-hal-detect.c: Loading module-alsa-sink with arguments 'device_id=0 sink_name=alsa_output.pci_1106_3288_sound_card_0_alsa_playback_0'
D: alsa-util.c: Trying front:0...
I: module-alsa-sink.c: Successfully opened device front:0.
I: module-alsa-sink.c: Successfully enabled mmap() mode.
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL front:0
I: alsa-util.c: Unable to attach to mixer front:0: No such file or directory
I: alsa-util.c: Successfully attached to mixer 'hw:0'
I: alsa-util.c: Using mixer control "Master".
I: sink.c: Created sink 0 "alsa_output.pci_1106_3288_sound_card_0_alsa_playback_0" with sample spec "s16le 2ch 44100Hz"
I: source.c: Created source 0 "alsa_output.pci_1106_3288_sound_card_0_alsa_playback_0.monitor" with sample spec "s16le 2ch 44100Hz"
I: module-alsa-sink.c: Using 8 fragments of size 896 bytes.
I: alsa-util.c: ALSA device lacks independant volume controls for each channel, falling back to software volume control.
D: module-alsa-sink.c: Thread starting up
D: rtpoll.c: Acquired POSIX realtime signal SIGRTMIN+29
I: module-alsa-sink.c: Starting playback.
I: module.c: Loaded "module-alsa-sink" (index: #0; argument: "device_id=0 sink_name=alsa_output.pci_1106_3288_sound_card_0_alsa_playback_0").
D: module-hal-detect.c: Loading module-alsa-source with arguments 'device_id=0 source_name=alsa_input.pci_1106_3288_sound_card_0_alsa_capture_0'
D: alsa-util.c: Trying front:0...
I: module-alsa-source.c: Successfully opened device front:0.
I: module-alsa-source.c: Successfully enabled mmap() mode.
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL front:0
I: alsa-util.c: Unable to attach to mixer front:0: No such file or directory
I: alsa-util.c: Successfully attached to mixer 'hw:0'
I: alsa-util.c: Using mixer control "Capture".
I: source.c: Created source 1 "alsa_input.pci_1106_3288_sound_card_0_alsa_capture_0" with sample spec "s16le 2ch 44100Hz"
I: module-alsa-source.c: Using 8 fragments of size 896 bytes.
I: alsa-util.c: All 2 channels can be mapped to mixer channels. Using hardware volume control.
D: module-alsa-source.c: Thread starting up
D: rtpoll.c: Acquired POSIX realtime signal SIGRTMIN+28
I: module.c: Loaded "module-alsa-source" (index: #1; argument: "device_id=0 source_name=alsa_input.pci_1106_3288_sound_card_0_alsa_capture_0").
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_1106_3288_sound_card_0_alsa_hw_specific_0
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_1106_3288_sound_card_0_alsa_control__1
I: module-hal-detect.c: Loaded 2 modules.
I: module.c: Loaded "module-hal-detect" (index: #2; argument: "").
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9/modules/module-esound-protocol-unix.so': success
I: module.c: Loaded "module-esound-protocol-unix" (index: #3; argument: "").
I: protocol-native.c: loading cookie from disk.
I: module.c: Loaded "module-native-protocol-unix" (index: #4; argument: "").
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9/modules/module-gconf.so': success
D: module-gconf.c: Loading module 'module-combine' with args '' due to GConf configuration.
I: sink.c: Created sink 1 "combined" with sample spec "s16le 2ch 44100Hz"
I: source.c: Created source 2 "combined.monitor" with sample spec "s16le 2ch 44100Hz"
D: memblockq.c: memblockq requested: maxlength=174080, tlength=174080, base=4, prebuf=1, minreq=0
D: memblockq.c: memblockq sanitized: maxlength=174080, tlength=174080, base=4, prebuf=4, minreq=4
I: resampler.c: Using resampler 'trivial'
I: resampler.c: Using s16le as working format.
I: sink-input.c: Created input 0 "Simultaneous output on ALSA PCM on front:0 (ALC662 Analog) via DMA" on alsa_output.pci_1106_3288_sound_card_0_alsa_playback_0 with sample spec s16le 2ch 44100Hz and channel map front-left,front-right
I: module-combine.c: Master sink is now 'alsa_output.pci_1106_3288_sound_card_0_alsa_playback_0'
D: module-combine.c: Thread starting up
D: rtpoll.c: Acquired POSIX realtime signal SIGRTMIN+27
I: module.c: Loaded "module-combine" (index: #5; argument: "").
D: module-gconf.c: Loading module 'module-rtp-recv' with args '' due to GConf configuration.
I: module.c: Loaded "module-rtp-recv" (index: #6; argument: "").
D: module-gconf.c: Loading module 'module-native-protocol-tcp' with args '' due to GConf configuration.
I: protocol-native.c: using already loaded auth cookie.
I: protocol-native.c: using already loaded auth cookie.
I: module.c: Loaded "module-native-protocol-tcp" (index: #7; argument: "").
D: module-gconf.c: Loading module 'module-esound-protocol-tcp' with args '' due to GConf configuration.
I: module.c: Loaded "module-esound-protocol-tcp" (index: #8; argument: "").
D: module-gconf.c: Loading module 'module-zeroconf-discover' with args '' due to GConf configuration.
I: module.c: Loaded "module-zeroconf-discover" (index: #9; argument: "").
I: module.c: Loaded "module-gconf" (index: #10; argument: "").
I: module.c: Loaded "module-volume-restore" (index: #11; argument: "").
D: module-default-device-restore.c: Restored default sink 'alsa_output.pci_1106_3288_sound_card_0_alsa_playback_0'.
D: core-subscribe.c: dropped redundant event.
D: module-default-device-restore.c: Restored default source 'alsa_input.pci_1106_3288_sound_card_0_alsa_capture_0'.
I: module.c: Loaded "module-default-device-restore" (index: #12; argument: "").
I: module.c: Loaded "module-rescue-streams" (index: #13; argument: "").
D: module-suspend-on-idle.c: Sink combined becomes idle.
D: module-suspend-on-idle.c: Source alsa_output.pci_1106_3288_sound_card_0_alsa_playback_0.monitor becomes idle.
D: module-suspend-on-idle.c: Source alsa_input.pci_1106_3288_sound_card_0_alsa_capture_0 becomes idle.
D: module-suspend-on-idle.c: Source combined.monitor becomes idle.
I: module.c: Loaded "module-suspend-on-idle" (index: #14; argument: "").
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9/modules/module-x11-publish.so': success
D: module-x11-publish.c: using already loaded auth cookie.
I: module.c: Loaded "module-x11-publish" (index: #15; argument: "").
I: main.c: Daemon startup complete.
D: module-hal-detect.c: dbus: interface=org.freedesktop.DBus, path=/org/freedesktop/DBus, member=NameAcquired
I: module-suspend-on-idle.c: Source combined.monitor idle for too long, suspending ...
I: module-suspend-on-idle.c: Source alsa_input.pci_1106_3288_sound_card_0_alsa_capture_0 idle for too long, suspending ...
I: module-alsa-source.c: Device suspended...
I: module-suspend-on-idle.c: Source alsa_output.pci_1106_3288_sound_card_0_alsa_playback_0.monitor idle for too long, suspending ...
I: module-suspend-on-idle.c: Sink combined idle for too long, suspending ...
D: module-suspend-on-idle.c: Sink alsa_output.pci_1106_3288_sound_card_0_alsa_playback_0 becomes idle.
D: module-suspend-on-idle.c: Sink alsa_output.pci_1106_3288_sound_card_0_alsa_playback_0 becomes idle.
I: sink-input.c: Freeing output 0 "Simultaneous output on ALSA PCM on front:0 (ALC662 Analog) via DMA"
I: module-combine.c: No master selected, lacking suitable outputs.
I: module-combine.c: Device suspended...
I: module-suspend-on-idle.c: Sink alsa_output.pci_1106_3288_sound_card_0_alsa_playback_0 idle for too long, suspending ...
I: module-alsa-sink.c: Device suspended...

---

### Post by afrodeity on 2009-04-25
[According to the troubleshooting section of HOWTO: PulseAudio Fixes & System-Wide Equalizer Support]("http://ubuntuforums.org/showthread.php?t=789578")

C: The application does not play audio and does list an entry in the Playback tab;
- the application is using PulseAudio but there is a problem, such as: a bug in PulseAudio, a problem with your ALSA kernel module or libraries, or your PCM/Master volume is muted.

---

### Post by afrodeity on 2009-04-25
I guess its getting a bit confusing because there are now two distributions ahead of Hardy.

How does one reinstate the status quo viz vi.

```
The following NEW packages will be installed:
  libsdl1.2debian-pulseaudio
0 upgraded, 1 newly installed, 1 to remove and 1 not upgraded.
Need to get 203kB of archives.
After this operation, 4096B disk space will be freed.
Do you want to continue [Y/n]? y
Get:1 http://za.archive.ubuntu.com hardy/universe libsdl1.2debian-pulseaudio 1.2.13-1ubuntu1 [203kB]
Fetched 203kB in 7s (27.2kB/s)                                                 
dpkg: libsdl1.2debian-alsa: dependency problems, but removing anyway as you request:
 libsdl1.2debian depends on libsdl1.2debian-alsa (= 1.2.13-1ubuntu1) | libsdl1.2debian-all (= 1.2.13-1ubuntu1) | libsdl1.2debian-esd (= 1.2.13-1ubuntu1) | libsdl1.2debian-arts (= 1.2.13-1ubuntu1) | libsdl1.2debian-oss (= 1.2.13-1ubuntu1) | libsdl1.2debian-nas (= 1.2.13-1ubuntu1) | libsdl1.2debian-pulseaudio (= 1.2.13-1ubuntu1); however:
  Package libsdl1.2debian-alsa is to be removed.
  Package libsdl1.2debian-all is not installed.
  Package libsdl1.2debian-esd is not installed.
  Package libsdl1.2debian-arts is not installed.
  Package libsdl1.2debian-oss is not installed.
  Package libsdl1.2debian-nas is not installed.
  Package libsdl1.2debian-pulseaudio is not installed.
(Reading database ... 170385 files and directories currently installed.)
Removing libsdl1.2debian-alsa ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Selecting previously deselected package libsdl1.2debian-pulseaudio.
(Reading database ... 170377 files and directories currently installed.)
Unpacking libsdl1.2debian-pulseaudio (from .../libsdl1.2debian-pulseaudio_1.2.13-1ubuntu1_amd64.deb) ...
Setting up libsdl1.2debian-pulseaudio (1.2.13-1ubuntu1) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
```

There is probably a dependency problem here, which is making matters worse. I have to resolve this issue in order to track back and resolve the earlier problem.

---

