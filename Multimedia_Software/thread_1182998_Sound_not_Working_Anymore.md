---
title: "Sound not Working Anymore"
date: 2009-06-09
forum: Multimedia Software
---

### Post by mbslrm on 2009-06-09
I'm on Ubuntu 9.04 right now. For some reason, the audio isn't working on any application anymore now. I tried playing around with the audio settings to no avail.

I think my audio card is a C-Media device.

And just for the record, the audio still works fine in Windows XP SP3 and it used to work fine in 8.10.

---

### Post by spiceminesofkessel on 2009-06-09
Sound can be a real pain in Linux. It's not always the case, but that's my experience.

Now, concerning your issue. For starters, have you referred to [this article]("https://help.ubuntu.com/community/SoundTroubleshooting?action=show&redirect=DebuggingSoundProblems") before? If not, see if it can guide you in the right direction.

---

### Post by spiceminesofkessel on 2009-06-09
Some items in that article can be advanced in nature.

You might just make sure Ubuntu knows what sound card you are using. Verify by typing in the terminal:
```
aplay -l
```
The output will tell you the driver it has installed for your sound card.

Next, you need to go to System->Preferences->Sound and make sure the bottom field (I believe it's the mixer) is set to match the driver in the output given by the above command. Then, for safe measure, open your volume control and verify that it is also using the same driver.

---

### Post by mbslrm on 2009-06-09
When I put "aplay -l" into Terminal, I get this:
```
**** List of PLAYBACK Hardware Devices ****
card 0: CMI8738 [C-Media CMI8738], device 0: CMI8738-MC6 [C-Media PCI DAC/ADC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CMI8738 [C-Media CMI8738], device 1: CMI8738-MC6 [C-Media PCI 2nd DAC]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CMI8738 [C-Media CMI8738], device 2: CMI8738-MC6 [C-Media PCI IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

---

### Post by mbslrm on 2009-06-09
> **spiceminesofkessel said:**
> Some items in that article can be advanced in nature.

You might just make sure Ubuntu knows what sound card you are using. Verify by typing in the terminal:
```
aplay -l
```
The output will tell you the driver it has installed for your sound card.

Next, you need to go to System->Preferences->Sound and make sure the bottom field (I believe it's the mixer) is set to match the driver in the output given by the above command. Then, for safe measure, open your volume control and verify that it is also using the same driver.

There are so many C-Media CMI8738 options there. Which one do I pick?

---

### Post by mbslrm on 2009-06-09
I also tried recompiling the audio part of the kernel to no avail.

---

### Post by spiceminesofkessel on 2009-06-09
> There are so many C-Media CMI8738 options there. Which one do I pick?

I would begin with device 0 (referring to your output posted). Set the options in the Sound Preferences to the driver matching device 0.
> CMI8738-MC6 [C-Media PCI DAC/ADC]

---

### Post by spiceminesofkessel on 2009-06-09
If you have multiple options for that driver, try the one which has ALSA in the name.

I had a similar problem and I just tried one option and if that didn't work, I tried the next until one finally worked.

---

### Post by spiceminesofkessel on 2009-06-09
You might also try:
```
killall pulseaudio
```and then,
```
pulseaudio -vvv
```See if that outouts any errors.

Another sound article for Ubuntu, specifically, Jaunty, can be found [here]("http://ubuntuforums.org/showthread.php?t=1130384").

---

### Post by mbslrm on 2009-06-09
I've selected the alsa option on both of them and it still doesn't work.

> **spiceminesofkessel said:**
> You might also try:
```
killall pulseaudio
```and then,
```
pulseaudio -vvv
```See if that outouts any errors.

Another sound article for Ubuntu, specifically, Jaunty, can be found [here]("http://ubuntuforums.org/showthread.php?t=1130384").

Here's the output after the second command:

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
D: main.c: Running on host: Linux i686 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009
I: main.c: Page size is 4096 bytes
D: main.c: Compiled with Valgrind support: no
D: main.c: Running in valgrind mode: no
D: main.c: Optimized build: yes
I: main.c: Machine ID is 2c24796ab213a002dbe62b7b49d7e144.
I: main.c: Using runtime directory /home/tahir/.pulse/2c24796ab213a002dbe62b7b49d7e144:runtime.
I: main.c: Using state directory /home/tahir/.pulse.
I: main.c: Running in system mode: no
I: main.c: Fresh high-resolution timers available! Bon appetit!
D: memblock.c: Using shared memory pool with 1024 slots of size 64.0 KiB each, total size is 64.0 MiB, maximum usable slot size is 65496
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9/modules/module-gconf.so': success
I: module.c: Loaded "module-gconf" (index: #0; argument: "").
I: module.c: Loaded "module-suspend-on-idle" (index: #1; argument: "").
I: module-device-restore.c: Sucessfully opened database file '/home/tahir/.pulse/2c24796ab213a002dbe62b7b49d7e144:device-volumes.i486-pc-linux-gnu.gdbm'.
I: module.c: Loaded "module-device-restore" (index: #2; argument: "").
I: module-stream-restore.c: Sucessfully opened database file '/home/tahir/.pulse/2c24796ab213a002dbe62b7b49d7e144:stream-volumes.i486-pc-linux-gnu.gdbm'.
I: module.c: Loaded "module-stream-restore" (index: #3; argument: "").
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9/modules/module-hal-detect.so': success
I: module-hal-detect.c: Trying capability alsa
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/computer_alsa_timer
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/computer_alsa_sequencer
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_13f6_111_sound_card_0_alsa_playback_2
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_13f6_111_sound_card_0_alsa_capture_2
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_13f6_111_sound_card_0_alsa_playback_1
D: module-hal-detect.c: Loading module-alsa-sink with arguments 'device_id=0 sink_name=alsa_output.pci_13f6_111_sound_card_0_alsa_playback_0 tsched=0'
D: alsa-util.c: Trying front:0 with SND_PCM_NO_AUTO_FORMAT ...
I: module-alsa-sink.c: Successfully opened device front:0.
I: module-alsa-sink.c: Successfully enabled mmap() mode.
I: (alsa-lib)control.c: Invalid CTL front:0
I: alsa-util.c: Unable to attach to mixer front:0: No such file or directory
I: alsa-util.c: Successfully attached to mixer 'hw:0'
I: alsa-util.c: Cannot find mixer control "Master" or mixer control is no combination of switch/volume.
I: alsa-util.c: Using mixer control "PCM".
I: module-device-restore.c: Restoring volume for sink alsa_output.pci_13f6_111_sound_card_0_alsa_playback_0.
I: module-device-restore.c: Restoring mute state for sink alsa_output.pci_13f6_111_sound_card_0_alsa_playback_0.
I: sink.c: Created sink 0 "alsa_output.pci_13f6_111_sound_card_0_alsa_playback_0" with sample spec s16le 2ch 44100Hz and channel map front-left,front-right
I: module-device-restore.c: Restoring volume for source alsa_output.pci_13f6_111_sound_card_0_alsa_playback_0.monitor.
I: module-device-restore.c: Restoring mute state for source alsa_output.pci_13f6_111_sound_card_0_alsa_playback_0.monitor.
I: source.c: Created source 0 "alsa_output.pci_13f6_111_sound_card_0_alsa_playback_0.monitor" with sample spec s16le 2ch 44100Hz and channel map front-left,front-right
I: module-alsa-sink.c: Using 8 fragments of size 1764 bytes, buffer time is 80.00ms
D: module-alsa-sink.c: hwbuf_unused=0
D: module-alsa-sink.c: setting avail_min=1
I: module-alsa-sink.c: Volume ranges from 0 to 31.
I: module-alsa-sink.c: Mixer doesn't support dB information.
I: alsa-util.c: All 2 channels can be mapped to mixer channels.
I: module-alsa-sink.c: Using hardware volume control. Hardware dB scale not supported.
D: alsa-util.c: snd_pcm_dump():
D: alsa-util.c: Hardware PCM card 0 'C-Media CMI8738' device 0 subdevice 0
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
I: module-alsa-sink.c: Starting playback.
D: module-suspend-on-idle.c: Source alsa_output.pci_13f6_111_sound_card_0_alsa_playback_0.monitor becomes idle.
D: module-suspend-on-idle.c: Sink alsa_output.pci_13f6_111_sound_card_0_alsa_playback_0 becomes idle.
I: module.c: Loaded "module-alsa-sink" (index: #4; argument: "device_id=0 sink_name=alsa_output.pci_13f6_111_sound_card_0_alsa_playback_0 tsched=0").
D: module-hal-detect.c: Loading module-alsa-source with arguments 'device_id=0 source_name=alsa_input.pci_13f6_111_sound_card_0_alsa_capture_0 tsched=0'
D: alsa-util.c: Trying front:0 with SND_PCM_NO_AUTO_FORMAT ...
I: module-alsa-source.c: Successfully opened device front:0.
I: module-alsa-source.c: Successfully enabled mmap() mode.
I: (alsa-lib)control.c: Invalid CTL front:0
I: alsa-util.c: Unable to attach to mixer front:0: No such file or directory
I: alsa-util.c: Successfully attached to mixer 'hw:0'
I: alsa-util.c: Cannot find mixer control "Capture" or mixer control is no combination of switch/volume.
I: alsa-util.c: Using mixer control "Mic".
I: module-device-restore.c: Restoring volume for source alsa_input.pci_13f6_111_sound_card_0_alsa_capture_0.
I: module-device-restore.c: Restoring mute state for source alsa_input.pci_13f6_111_sound_card_0_alsa_capture_0.
I: source.c: Created source 1 "alsa_input.pci_13f6_111_sound_card_0_alsa_capture_0" with sample spec s16le 2ch 44100Hz and channel map front-left,front-right
I: module-alsa-source.c: Using 8 fragments of size 1764 bytes, buffer time is 80.00ms
D: module-alsa-source.c: hwbuf_unused=0
D: module-alsa-source.c: setting avail_min=1
I: module-alsa-source.c: Volume ranges from 0 to 7.
I: module-alsa-source.c: Mixer doesn't support dB information.
I: alsa-util.c: ALSA device lacks independant volume controls for each channel.
I: module-alsa-source.c: Using hardware volume control. Hardware dB scale not supported.
D: alsa-util.c: snd_pcm_dump():
D: alsa-util.c: Hardware PCM card 0 'C-Media CMI8738' device 0 subdevice 0
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
D: module-suspend-on-idle.c: Source alsa_input.pci_13f6_111_sound_card_0_alsa_capture_0 becomes idle.
I: module.c: Loaded "module-alsa-source" (index: #5; argument: "device_id=0 source_name=alsa_input.pci_13f6_111_sound_card_0_alsa_capture_0 tsched=0").
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_13f6_111_sound_card_0_alsa_midi_0
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_13f6_111_sound_card_0_alsa_hw_specific_0
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_13f6_111_sound_card_0_alsa_control__1
I: module-hal-detect.c: Loaded 2 modules.
I: module.c: Loaded "module-hal-detect" (index: #6; argument: "tsched=0").
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9/modules/module-esound-protocol-unix.so': success
I: module.c: Loaded "module-esound-protocol-unix" (index: #7; argument: "").
I: module.c: Loaded "module-native-protocol-unix" (index: #8; argument: "").
I: module-default-device-restore.c: Restored default sink 'alsa_output.pci_13f6_111_sound_card_0_alsa_playback_0'.
D: core-subscribe.c: Dropped redundant event due to change event.
I: module-default-device-restore.c: Restored default source 'alsa_input.pci_13f6_111_sound_card_0_alsa_capture_0'.
I: module.c: Loaded "module-default-device-restore" (index: #9; argument: "").
I: module.c: Loaded "module-rescue-streams" (index: #10; argument: "").
I: module.c: Loaded "module-always-sink" (index: #11; argument: "").
I: client.c: Created 0 "ConsoleKit Session /org/freedesktop/ConsoleKit/Session1"
D: module-console-kit.c: Added new session /org/freedesktop/ConsoleKit/Session1
I: module.c: Loaded "module-console-kit" (index: #12; argument: "").
I: module.c: Loaded "module-position-event-sounds" (index: #13; argument: "").
I: main.c: Daemon startup complete.
D: module-hal-detect.c: dbus: interface=org.freedesktop.DBus, path=/org/freedesktop/DBus, member=NameAcquired
D: module-console-kit.c: dbus: interface=org.freedesktop.DBus, path=/org/freedesktop/DBus, member=NameAcquired
I: module-suspend-on-idle.c: Source alsa_output.pci_13f6_111_sound_card_0_alsa_playback_0.monitor idle for too long, suspending ...
I: module-suspend-on-idle.c: Sink alsa_output.pci_13f6_111_sound_card_0_alsa_playback_0 idle for too long, suspending ...
I: module-alsa-sink.c: Device suspended...
I: module-suspend-on-idle.c: Source alsa_input.pci_13f6_111_sound_card_0_alsa_capture_0 idle for too long, suspending ...
I: module-alsa-source.c: Device suspended...
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
I: sink.c: Freeing sink 0 "alsa_output.pci_13f6_111_sound_card_0_alsa_playback_0"
I: source.c: Freeing source 0 "alsa_output.pci_13f6_111_sound_card_0_alsa_playback_0.monitor"
I: module.c: Unloaded "module-alsa-sink" (index: #4).
I: module.c: Unloading "module-alsa-source" (index: #5).
D: module-rescue-streams.c: No source outputs to move away.
D: module-alsa-source.c: Thread shutting down
I: source.c: Freeing source 1 "alsa_input.pci_13f6_111_sound_card_0_alsa_capture_0"
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
D: module-console-kit.c: Removing session /org/freedesktop/ConsoleKit/Session1
I: client.c: Freed 0 "ConsoleKit Session /org/freedesktop/ConsoleKit/Session1"
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

---

### Post by spiceminesofkessel on 2009-06-10
[BUMP]

This is getting a little too deep for me. I apologize.

Anyone else have any ideas?

---

### Post by mbslrm on 2009-06-10
Can anyone else help me?

---

### Post by mbslrm on 2009-06-20
I have Mac4Lin. Is this the problem?

---

### Post by IMAGinES on 2009-06-20
Mslrm, I'm having similar trouble but don't have Mac4Lin. I've gone through SoundTroubleshooting to no avail and have filed a bug report with Launchpad.

---

### Post by executorvs on 2009-06-24
can you tell me if when you run 'lsusb' in terminal you see your C-media card?

if so you'll need to change some settings in /etc/modprobe.d/alsa-base as ubuntu prevents sound devices which operate across the usb bus from being loaded as the default device.

---

### Post by mbslrm on 2009-06-25
> **executorvs said:**
> can you tell me if when you run 'lsusb' in terminal you see your C-media card?

if so you'll need to change some settings in /etc/modprobe.d/alsa-base as ubuntu prevents sound devices which operate across the usb bus from being loaded as the default device.

This is what I get:

```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

The sound card is in the mobo...

---

### Post by executorvs on 2009-06-25
I was just checking because some intergrated C-media chipsets use the USB bus as opposed to the PCI bus.

what motherboard do you use?

---

### Post by mbslrm on 2009-06-26
> **executorvs said:**
> I was just checking because some intergrated C-media chipsets use the USB bus as opposed to the PCI bus.

what motherboard do you use?

Where can I check?

---

### Post by skywriter on 2009-07-03
Got similiar ussue with Audugy 4. alsamixer shows it as SB0610.
I hear short click during boot, but there is no sound...

---

### Post by mbslrm on 2009-08-18
This is getting really pathetic now.

Support for something as basic as audio has been fudged up.

---

### Post by IMAGinES on 2010-04-11
Aha! Found a solution for my problem:
[http://www.shareconnector.com/no-sound-issue-sb-audigy-in-ubuntu-904](http://www.shareconnector.com/no-sound-issue-sb-audigy-in-ubuntu-904)

I followed its instructions: Brought alsamixer up via terminal, selected the channel “Audigy Analog/Digital Output Jack” and pressed “M” to turn it on. Sound is back!

My system still says my card is an Audigy 2 Value, not an Audigy 4, but I'm happy enough.

---

