---
title: "Sound kills itself about every hour"
date: 2009-02-21
forum: Multimedia Software
---

### Post by BazookaAce on 2009-02-21
Ey yo!

Okay, so i'm sitting here on my computer and listening to The Von Bondies' new album. Oh yeah, very nice, and "BAM!". No sound. This problem showed his ugly face about a week ago, and i'm thinking that it's the damn Pulseaudio that's ******* my system. I used Alsa before, and i didn't have any problems then. 

Another thing. Audacious is dead to. I mean that it starts and all, but it won't play anything. Amarok plays for about one hour and then the sound disappears, and then the only thing i can do is to reboot the computer. 

How can i fix this? How can i remove pulseaudio safely without damaging the computer? I wish to switch back to ALSA again.

Thanks in advance.

---

### Post by markbuntu on 2009-02-21
You can find out yourself what is causing this problem. Kill pulse with

killall pulseaudio

Then start it again with

pulseaudio -vvv

Let it run in the terminal and when the sound stops you will see what is causing it.

It could be a pulse problem but is more likely an ALSA driver problem.

---

### Post by BazookaAce on 2009-02-21
Thanks! I'll check it out, and report back here.

---

### Post by Mercury_Alpha on 2009-02-21
For issues with PulseAudio and ALSA, refer to this thread: [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

For the Audacious issue, I had it too and resolved it with this: [http://ubuntuforums.org/showthread.php?t=756179](http://ubuntuforums.org/showthread.php?t=756179). Replace "adyhasch" with your user name when you get to rm'ing all those directories. Bash may tell you that certain directories could not be found -- that's normal.

---

### Post by BazookaAce on 2009-02-21
OKay, i'm back. Here's what the terminal is telling me: 

```
I: main.c: PolicyKit refuses acquire-high-priority privilige.
I: main.c: Called SUID root and real-time/high-priority scheduling was requested in the configuration. However, we lack the necessary priviliges:
I: main.c: We are not in group 'pulse-rt' and PolicyKit refuse to grant us priviliges. Dropping SUID again.
I: main.c: For enabling real-time scheduling please acquire the appropriate PolicyKit priviliges, or become a member of 'pulse-rt', or increase the RLIMIT_NICE/RLIMIT_RTPRIO resource limits for this user.
I: main.c: Note that real-time/high-priority scheduling is NOT normally required. If you experience crackling or other sound anomalies, consider one or more of the above solutions.
I: main.c: High-priority scheduling enabled in configuration but now allowed by policy. Disabling forcibly.
W: ltdl-bind-now.c: Failed to find original dlopen loader.
W: pid.c: Stale PID file, overwriting.
W: main.c: setrlimit(RLIMIT_NICE, (31, 31)) **failed: Operation not permitted**
W: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) **failed: Operation not permitted**
I: main.c: This is PulseAudio 0.9.10
I: main.c: Page size is 4096 bytes
I: main.c: Fresh high-resolution timers available! Bon appetit!
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9/modules/module-hal-detect.so': success
I: module-hal-detect.c: Trying capability alsa
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/computer_alsa_timer
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/computer_alsa_sequencer
D: module-hal-detect.c: Loading module-alsa-sink with arguments 'device_id=0 sink_name=alsa_output.pci_8086_27d8_sound_card_0_alsa_playback_0'
D: alsa-util.c: Trying front:0...
I: module-alsa-sink.c: Successfully opened device front:0.
I: module-alsa-sink.c: Successfully enabled mmap() mode.
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL front:0
I: alsa-util.c: Unable to attach to mixer front:0: No such file or directory
I: alsa-util.c: Successfully attached to mixer 'hw:0'
I: alsa-util.c: Using mixer control "Master".
I: sink.c: Created sink 0 "alsa_output.pci_8086_27d8_sound_card_0_alsa_playback_0" with sample spec "s16le 2ch 44100Hz"
I: source.c: Created source 0 "alsa_output.pci_8086_27d8_sound_card_0_alsa_playback_0.monitor" with sample spec "s16le 2ch 44100Hz"
I: module-alsa-sink.c: Using 8 fragments of size 1792 bytes.
I: alsa-util.c: All 2 channels can be mapped to mixer channels. Using hardware volume control.
D: module-alsa-sink.c: Thread starting up
D: rtpoll.c: Acquired POSIX realtime signal SIGRTMIN+29
I: module-alsa-sink.c: Starting playback.
I: module.c: Loaded "module-alsa-sink" (index: #0; argument: "device_id=0 sink_name=alsa_output.pci_8086_27d8_sound_card_0_alsa_playback_0").
D: module-hal-detect.c: Loading module-alsa-source with arguments 'device_id=0 source_name=alsa_input.pci_8086_27d8_sound_card_0_alsa_capture_0'
D: alsa-util.c: Trying front:0...
I: module-alsa-source.c: Successfully opened device front:0.
I: module-alsa-source.c: Successfully enabled mmap() mode.
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL front:0
I: alsa-util.c: Unable to attach to mixer front:0: No such file or directory
I: alsa-util.c: Successfully attached to mixer 'hw:0'
I: alsa-util.c: Using mixer control "Capture".
I: source.c: Created source 1 "alsa_input.pci_8086_27d8_sound_card_0_alsa_capture_0" with sample spec "s16le 2ch 44100Hz"
I: module-alsa-source.c: Using 8 fragments of size 1792 bytes.
I: alsa-util.c: All 2 channels can be mapped to mixer channels. Using hardware volume control.
D: module-alsa-source.c: Thread starting up
D: rtpoll.c: Acquired POSIX realtime signal SIGRTMIN+28
I: module.c: Loaded "module-alsa-source" (index: #1; argument: "device_id=0 source_name=alsa_input.pci_8086_27d8_sound_card_0_alsa_capture_0").
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_8086_27d8_sound_card_0_alsa_control__1
I: module-hal-detect.c: Loaded 2 modules.
I: module.c: Loaded "module-hal-detect" (index: #2; argument: "").
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9/modules/module-esound-protocol-unix.so': success
I: module.c: Loaded "module-esound-protocol-unix" (index: #3; argument: "").
I: protocol-native.c: loading cookie from disk.
I: module.c: Loaded "module-native-protocol-unix" (index: #4; argument: "").
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9/modules/module-gconf.so': success
I: module.c: Loaded "module-gconf" (index: #5; argument: "").
I: module.c: Loaded "module-volume-restore" (index: #6; argument: "").
D: module-default-device-restore.c: Restored default sink 'alsa_output.pci_8086_27d8_sound_card_0_alsa_playback_0'.
D: core-subscribe.c: dropped redundant event.
D: module-default-device-restore.c: Restored default source 'alsa_input.pci_8086_27d8_sound_card_0_alsa_capture_0'.
I: module.c: Loaded "module-default-device-restore" (index: #7; argument: "").
I: module.c: Loaded "module-rescue-streams" (index: #8; argument: "").
D: module-suspend-on-idle.c: Sink alsa_output.pci_8086_27d8_sound_card_0_alsa_playback_0 becomes idle.
D: module-suspend-on-idle.c: Source alsa_output.pci_8086_27d8_sound_card_0_alsa_playback_0.monitor becomes idle.
D: module-suspend-on-idle.c: Source alsa_input.pci_8086_27d8_sound_card_0_alsa_capture_0 becomes idle.
I: module.c: Loaded "module-suspend-on-idle" (index: #9; argument: "").
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9/modules/module-x11-publish.so': success
D: module-x11-publish.c: using already loaded auth cookie.
I: module.c: Loaded "module-x11-publish" (index: #10; argument: "").
I: main.c: Daemon startup complete.
D: module-hal-detect.c: dbus: interface=org.freedesktop.DBus, path=/org/freedesktop/DBus, member=NameAcquired
I: module-suspend-on-idle.c: Sink alsa_output.pci_8086_27d8_sound_card_0_alsa_playback_0 idle for too long, suspending ...
I: module-alsa-sink.c: Device suspended...
I: module-suspend-on-idle.c: Source alsa_input.pci_8086_27d8_sound_card_0_alsa_capture_0 idle for too long, suspending ...
I: module-alsa-source.c: Device suspended...
I: module-suspend-on-idle.c: Source alsa_output.pci_8086_27d8_sound_card_0_alsa_playback_0.monitor idle for too long, suspending ...
I: client.c: Created 0 "Native client (UNIX socket client)"
I: client.c: Freed 0 "Native client (UNIX socket client)"
I: protocol-native.c: connection died.
I: client.c: Created 1 "Native client (UNIX socket client)"
I: protocol-native.c: Got credentials: uid=1000 gid=1000 success=1
I: protocol-native.c: Enabled SHM for new connection
I: client.c: Client 1 changed name from "Native client (UNIX socket client)" to "ALSA plug-in [amarokapp]"
I: client.c: Freed 1 "ALSA plug-in [amarokapp]"
I: protocol-native.c: connection died.
I: client.c: Created 2 "Native client (UNIX socket client)"
I: protocol-native.c: Got credentials: uid=1000 gid=1000 success=1
I: protocol-native.c: Enabled SHM for new connection
I: client.c: Client 2 changed name from "Native client (UNIX socket client)" to "ALSA plug-in [amarokapp]"
I: client.c: Freed 2 "ALSA plug-in [amarokapp]"
I: protocol-native.c: connection died.
I: client.c: Created 3 "Native client (UNIX socket client)"
I: protocol-native.c: Got credentials: uid=1000 gid=1000 success=1
I: protocol-native.c: Enabled SHM for new connection
I: client.c: Client 3 changed name from "Native client (UNIX socket client)" to "ALSA plug-in [amarokapp]"
I: client.c: Created 4 "Native client (UNIX socket client)"
I: protocol-native.c: Got credentials: uid=1000 gid=1000 success=1
I: protocol-native.c: Enabled SHM for new connection
I: client.c: Client 4 changed name from "Native client (UNIX socket client)" to "ALSA plug-in [amarokapp]"
I: module-volume-restore.c: Restoring sink for <pulsecore/protocol-native.c$ALSA plug-in [amarokapp]>
I: module-volume-restore.c: Restoring volume for <pulsecore/protocol-native.c$ALSA plug-in [amarokapp]>
I: module-alsa-sink.c: Trying resume...
I: module-alsa-sink.c: Resumed successfully...
D: module-suspend-on-idle.c: Sink alsa_output.pci_8086_27d8_sound_card_0_alsa_playback_0 becomes idle.
D: module-suspend-on-idle.c: Sink alsa_output.pci_8086_27d8_sound_card_0_alsa_playback_0 becomes busy.
I: sink-input.c: Created input 0 "ALSA Playback" on alsa_output.pci_8086_27d8_sound_card_0_alsa_playback_0 with sample spec s16le 2ch 44100Hz and channel map front-left,front-right
D: memblockq.c: memblockq requested: maxlength=4194304, tlength=176384, base=4, prebuf=154336, minreq=22048
D: memblockq.c: memblockq sanitized: maxlength=4194304, tlength=176384, base=4, prebuf=154336, minreq=22048
I: module-alsa-sink.c: Starting playback.
D: module-suspend-on-idle.c: Sink alsa_output.pci_8086_27d8_sound_card_0_alsa_playback_0 becomes idle.
D: module-suspend-on-idle.c: Sink alsa_output.pci_8086_27d8_sound_card_0_alsa_playback_0 becomes idle.
I: sink-input.c: Freeing output 0 "ALSA Playback"
I: module-volume-restore.c: Restoring sink for <pulsecore/protocol-native.c$ALSA plug-in [amarokapp]>
I: module-volume-restore.c: Restoring volume for <pulsecore/protocol-native.c$ALSA plug-in [amarokapp]>
D: module-suspend-on-idle.c: Sink alsa_output.pci_8086_27d8_sound_card_0_alsa_playback_0 becomes busy.
I: sink-input.c: Created input 1 "ALSA Playback" on alsa_output.pci_8086_27d8_sound_card_0_alsa_playback_0 with sample spec s16le 2ch 44100Hz and channel map front-left,front-right
D: memblockq.c: memblockq requested: maxlength=4194304, tlength=176384, base=4, prebuf=154336, minreq=22048
D: memblockq.c: memblockq sanitized: maxlength=4194304, tlength=176384, base=4, prebuf=154336, minreq=22048
D: module-suspend-on-idle.c: Sink alsa_output.pci_8086_27d8_sound_card_0_alsa_playback_0 becomes idle.
D: module-suspend-on-idle.c: Sink alsa_output.pci_8086_27d8_sound_card_0_alsa_playback_0 becomes idle.
I: sink-input.c: Freeing output 1 "ALSA Playback"
I: client.c: Freed 4 "ALSA plug-in [amarokapp]"
I: protocol-native.c: connection died.
I: client.c: Created 5 "Native client (UNIX socket client)"
I: protocol-native.c: Got credentials: uid=1000 gid=1000 success=1
I: protocol-native.c: Enabled SHM for new connection
I: client.c: Client 5 changed name from "Native client (UNIX socket client)" to "ALSA plug-in [amarokapp]"
I: module-volume-restore.c: Restoring sink for <pulsecore/protocol-native.c$ALSA plug-in [amarokapp]>
I: module-volume-restore.c: Restoring volume for <pulsecore/protocol-native.c$ALSA plug-in [amarokapp]>
D: module-suspend-on-idle.c: Sink alsa_output.pci_8086_27d8_sound_card_0_alsa_playback_0 becomes busy.
I: sink-input.c: Created input 2 "ALSA Playback" on alsa_output.pci_8086_27d8_sound_card_0_alsa_playback_0 with sample spec s16le 2ch 44100Hz and channel map front-left,front-right
D: memblockq.c: memblockq requested: maxlength=4194304, tlength=176384, base=4, prebuf=154336, minreq=22048
D: memblockq.c: memblockq sanitized: maxlength=4194304, tlength=176384, base=4, prebuf=154336, minreq=22048
D: module-hal-detect.c: dbus: interface=org.freedesktop.Hal.Device, path=/org/freedesktop/Hal/devices/computer_power_supply_battery_BAT1, member=PropertyModified
Soft CPU time limit exhausted, terminating.
Hard CPU time limit exhausted, terminating forcibly.
Aborted
```

---

### Post by BazookaAce on 2009-02-21
> **Mercury_Alpha said:**
> For issues with PulseAudio and ALSA, refer to this thread: [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

For the Audacious issue, I had it too and resolved it with this: [http://ubuntuforums.org/showthread.php?t=756179](http://ubuntuforums.org/showthread.php?t=756179). Replace "adyhasch" with your user name when you get to rm'ing all those directories. Bash may tell you that certain directories could not be found -- that's normal.

Thank you :) I'll check it out.

---

### Post by Reeman on 2009-02-21
> **BazookaAce said:**
> OKay, i'm back. Here's what the terminal is telling me: 

```
 D: memblockq.c: memblockq requested: maxlength=4194304, tlength=176384, base=4, prebuf=154336, minreq=22048
D: memblockq.c: memblockq sanitized: maxlength=4194304, tlength=176384, base=4, prebuf=154336, minreq=22048
D: module-hal-detect.c: dbus: interface=org.freedesktop.Hal.Device, path=/org/freedesktop/Hal/devices/computer_power_supply_battery_BAT1, member=PropertyModified
Soft CPU time limit exhausted, terminating.
Hard CPU time limit exhausted, terminating forcibly.
Aborted
```
From the output you displayed it is possible that you have discovered a memory leak in pulse. If your soft cpu is limiting out then holy cow it sounds like playing audio is causing a looped memory leak that multi tasks the hard and soft cpu processes to the max. Run your cpu monitor while this is happening. If the usage climbs slowly over an hour then that is most likely what is happening.

I think I am going to give pulse and all the Ubuntu/Oss/pulse audio associated crap a dbpg -uninstall for good after seeing that readout!

---

### Post by BazookaAce on 2009-02-21
Ok. Update. I've followed Pulseaudio from the terminal (top) and it uses about 1-3% of the CPU and 0.1-0.4% of the resources (ram). I've reinstalled pulseaudio and all the plugins and stuff, so now i'm waiting.

Update2: Xorg uses about 60% of the CPU :s Running Amarok and Firefox. (Aspire One A150 1GB RAM 1,6GHz)

---

### Post by BazookaAce on 2009-02-22
I just came across this in the system log:

```
Feb 17 03:52:12 steffen-laptop Cleanup, done. Exitting... 
Feb 17 04:15:30 steffen-laptop pulseaudio[5692]: ltdl-bind-now.c: Failed to find original dlopen loader.
Feb 17 04:15:30 steffen-laptop pulseaudio[5694]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Feb 17 04:15:30 steffen-laptop pulseaudio[5694]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Feb 17 04:15:49 steffen-laptop pulseaudio[5694]: module-x11-xsmp.c: X11 session manager not running.
Feb 17 04:15:49 steffen-laptop pulseaudio[5694]: module.c: Failed to load  module "module-x11-xsmp" (argument: ""): initialization failed.
Feb 17 04:15:54 steffen-laptop python: hp-systray(init)[5814]: warning: No hp: or hpfax: devices found in any installed CUPS queue. Exiting.
Feb 17 04:51:17 steffen-laptop bonobo-activation-server (steffen-6665): could not associate with desktop session: Failed to connect to socket /tmp/dbus-LGAH6rDw3e: Connection refused
Feb 17 04:51:19 steffen-laptop Cleanup, done. Exitting... 
Feb 17 15:16:10 steffen-laptop pulseaudio[5731]: ltdl-bind-now.c: Failed to find original dlopen loader.
Feb 17 15:16:10 steffen-laptop pulseaudio[5733]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Feb 17 15:16:10 steffen-laptop pulseaudio[5733]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Feb 17 15:16:28 steffen-laptop pulseaudio[5733]: module-x11-xsmp.c: X11 session manager not running.
Feb 17 15:16:28 steffen-laptop pulseaudio[5733]: module.c: Failed to load  module "module-x11-xsmp" (argument: ""): initialization failed.
Feb 17 15:16:36 steffen-laptop python: hp-systray(init)[5853]: warning: No hp: or hpfax: devices found in any installed CUPS queue. Exiting.
Feb 18 03:58:52 steffen-laptop Failed to open the panel socket 
Feb 18 03:58:53 steffen-laptop Failed to open the panel socket 
Feb 18 12:28:20 steffen-laptop pulseaudio[5693]: ltdl-bind-now.c: Failed to find original dlopen loader.
Feb 18 12:28:21 steffen-laptop pulseaudio[5695]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Feb 18 12:28:21 steffen-laptop pulseaudio[5695]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Feb 18 12:28:40 steffen-laptop pulseaudio[5695]: module-x11-xsmp.c: X11 session manager not running.
Feb 18 12:28:40 steffen-laptop pulseaudio[5695]: module.c: Failed to load  module "module-x11-xsmp" (argument: ""): initialization failed.
Feb 18 12:28:45 steffen-laptop python: hp-systray(init)[5815]: warning: No hp: or hpfax: devices found in any installed CUPS queue. Exiting.
Feb 18 14:28:12 steffen-laptop pulseaudio[5715]: ltdl-bind-now.c: Failed to find original dlopen loader.
Feb 18 14:28:12 steffen-laptop pulseaudio[5717]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Feb 18 14:28:12 steffen-laptop pulseaudio[5717]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Feb 18 14:28:30 steffen-laptop pulseaudio[5717]: module-x11-xsmp.c: X11 session manager not running.
Feb 18 14:28:30 steffen-laptop pulseaudio[5717]: module.c: Failed to load  module "module-x11-xsmp" (argument: ""): initialization failed.
Feb 18 14:28:36 steffen-laptop python: hp-systray(init)[5837]: warning: No hp: or hpfax: devices found in any installed CUPS queue. Exiting.
Feb 18 17:10:33 steffen-laptop Failed to open the panel socket 
Feb 18 17:10:33 steffen-laptop Failed to open the panel socket 
Feb 18 17:52:45 steffen-laptop pulseaudio[5747]: ltdl-bind-now.c: Failed to find original dlopen loader.
Feb 18 17:52:45 steffen-laptop pulseaudio[5749]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Feb 18 17:52:45 steffen-laptop pulseaudio[5749]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Feb 18 17:53:04 steffen-laptop pulseaudio[5749]: module-x11-xsmp.c: X11 session manager not running.
Feb 18 17:53:04 steffen-laptop pulseaudio[5749]: module.c: Failed to load  module "module-x11-xsmp" (argument: ""): initialization failed.
Feb 18 17:53:06 steffen-laptop python: hp-systray(init)[5869]: warning: No hp: or hpfax: devices found in any installed CUPS queue. Exiting.
Feb 19 13:37:33 steffen-laptop pulseaudio[5783]: ltdl-bind-now.c: Failed to find original dlopen loader.
Feb 19 13:37:33 steffen-laptop pulseaudio[5785]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Feb 19 13:37:33 steffen-laptop pulseaudio[5785]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Feb 19 13:37:52 steffen-laptop pulseaudio[5785]: module-x11-xsmp.c: X11 session manager not running.
Feb 19 13:37:52 steffen-laptop pulseaudio[5785]: module.c: Failed to load  module "module-x11-xsmp" (argument: ""): initialization failed.
Feb 19 13:37:53 steffen-laptop python: hp-systray(init)[5905]: warning: No hp: or hpfax: devices found in any installed CUPS queue. Exiting.
Feb 19 14:52:53 steffen-laptop pulseaudio[5674]: ltdl-bind-now.c: Failed to find original dlopen loader.
Feb 19 14:52:53 steffen-laptop pulseaudio[5676]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Feb 19 14:52:53 steffen-laptop pulseaudio[5676]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Feb 19 14:53:11 steffen-laptop pulseaudio[5676]: module-x11-xsmp.c: X11 session manager not running.
Feb 19 14:53:11 steffen-laptop pulseaudio[5676]: module.c: Failed to load  module "module-x11-xsmp" (argument: ""): initialization failed.
Feb 19 14:53:17 steffen-laptop python: hp-systray(init)[5796]: warning: No hp: or hpfax: devices found in any installed CUPS queue. Exiting.
Feb 19 23:27:33 steffen-laptop pulseaudio[5691]: ltdl-bind-now.c: Failed to find original dlopen loader.
Feb 19 23:27:33 steffen-laptop pulseaudio[5693]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Feb 19 23:27:33 steffen-laptop pulseaudio[5693]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Feb 19 23:27:53 steffen-laptop pulseaudio[5693]: module-x11-xsmp.c: X11 session manager not running.
Feb 19 23:27:53 steffen-laptop pulseaudio[5693]: module.c: Failed to load  module "module-x11-xsmp" (argument: ""): initialization failed.
Feb 19 23:28:01 steffen-laptop python: hp-systray(init)[5815]: warning: No hp: or hpfax: devices found in any installed CUPS queue. Exiting.
Feb 19 23:30:26 steffen-laptop Cleanup, done. Exitting... 
Feb 19 23:31:52 steffen-laptop pulseaudio[5683]: ltdl-bind-now.c: Failed to find original dlopen loader.
Feb 19 23:31:52 steffen-laptop pulseaudio[5685]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Feb 19 23:31:52 steffen-laptop pulseaudio[5685]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Feb 19 23:32:10 steffen-laptop pulseaudio[5685]: module-x11-xsmp.c: X11 session manager not running.
Feb 19 23:32:10 steffen-laptop pulseaudio[5685]: module.c: Failed to load  module "module-x11-xsmp" (argument: ""): initialization failed.
Feb 19 23:35:04 steffen-laptop pulseaudio[6192]: ltdl-bind-now.c: Failed to find original dlopen loader.
Feb 19 23:35:04 steffen-laptop pulseaudio[6194]: pid.c: Stale PID file, overwriting.
Feb 19 23:35:04 steffen-laptop pulseaudio[6194]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Feb 19 23:35:04 steffen-laptop pulseaudio[6194]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Feb 19 23:35:06 steffen-laptop pulseaudio[6194]: source.c: Assertion 'PA_SOURCE_OPENED(s->thread_info.state)' failed at pulsecore/source.c:278, function pa_source_post(). Aborting.
Feb 19 23:37:00 steffen-laptop bonobo-activation-server (steffen-6483): could not associate with desktop session: Failed to connect to socket /tmp/dbus-1Ed2c85ZmT: Connection refused
Feb 19 23:37:01 steffen-laptop Failed to open the panel socket 
Feb 19 23:37:02 steffen-laptop Failed to open the panel socket 
Feb 19 23:37:12 steffen-laptop pulseaudio[6602]: ltdl-bind-now.c: Failed to find original dlopen loader.
Feb 19 23:37:12 steffen-laptop pulseaudio[6604]: pid.c: Stale PID file, overwriting.
Feb 19 23:37:12 steffen-laptop pulseaudio[6604]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Feb 19 23:37:12 steffen-laptop pulseaudio[6604]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Feb 19 23:37:24 steffen-laptop pulseaudio[6604]: module-x11-xsmp.c: X11 session manager not running.
Feb 19 23:37:24 steffen-laptop pulseaudio[6604]: module.c: Failed to load  module "module-x11-xsmp" (argument: ""): initialization failed.
Feb 20 00:57:49 steffen-laptop pulseaudio[5726]: ltdl-bind-now.c: Failed to find original dlopen loader.
Feb 20 00:57:49 steffen-laptop pulseaudio[5728]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Feb 20 00:57:49 steffen-laptop pulseaudio[5728]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Feb 20 00:58:07 steffen-laptop pulseaudio[5728]: module-x11-xsmp.c: X11 session manager not running.
Feb 20 00:58:07 steffen-laptop pulseaudio[5728]: module.c: Failed to load  module "module-x11-xsmp" (argument: ""): initialization failed.
Feb 20 01:30:04 steffen-laptop pulseaudio[24605]: ltdl-bind-now.c: Failed to find original dlopen loader.
Feb 20 01:30:04 steffen-laptop pulseaudio[24608]: pid.c: Stale PID file, overwriting.
Feb 20 01:30:04 steffen-laptop pulseaudio[24608]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Feb 20 01:30:04 steffen-laptop pulseaudio[24608]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Feb 20 01:30:16 steffen-laptop pulseaudio[24608]: module-x11-xsmp.c: X11 session manager not running.
Feb 20 01:30:16 steffen-laptop pulseaudio[24608]: module.c: Failed to load  module "module-x11-xsmp" (argument: ""): initialization failed.
Feb 20 01:34:52 steffen-laptop pulseaudio[5701]: ltdl-bind-now.c: Failed to find original dlopen loader.
Feb 20 01:34:52 steffen-laptop pulseaudio[5703]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Feb 20 01:34:52 steffen-laptop pulseaudio[5703]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Feb 20 01:35:09 steffen-laptop pulseaudio[5703]: module-x11-xsmp.c: X11 session manager not running.
Feb 20 01:35:09 steffen-laptop pulseaudio[5703]: module.c: Failed to load  module "module-x11-xsmp" (argument: ""): initialization failed.
Feb 20 01:43:00 steffen-laptop pulseaudio[10111]: ltdl-bind-now.c: Failed to find original dlopen loader.
Feb 20 01:43:00 steffen-laptop pulseaudio[10113]: pid.c: Stale PID file, overwriting.
Feb 20 01:43:00 steffen-laptop pulseaudio[10113]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Feb 20 01:43:00 steffen-laptop pulseaudio[10113]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Feb 20 01:43:12 steffen-laptop pulseaudio[10113]: module-x11-xsmp.c: X11 session manager not running.
Feb 20 01:43:12 steffen-laptop pulseaudio[10113]: module.c: Failed to load  module "module-x11-xsmp" (argument: ""): initialization failed.
Feb 20 01:46:32 steffen-laptop pulseaudio[10629]: ltdl-bind-now.c: Failed to find original dlopen loader.
Feb 20 01:46:32 steffen-laptop pulseaudio[10633]: pid.c: Stale PID file, overwriting.
Feb 20 01:46:32 steffen-laptop pulseaudio[10633]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Feb 20 01:46:32 steffen-laptop pulseaudio[10633]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Feb 20 01:46:43 steffen-laptop pulseaudio[10633]: module-x11-xsmp.c: X11 session manager not running.
Feb 20 01:46:43 steffen-laptop pulseaudio[10633]: module.c: Failed to load  module "module-x11-xsmp" (argument: ""): initialization failed.
Feb 20 04:04:02 steffen-laptop pulseaudio[14023]: ltdl-bind-now.c: Failed to find original dlopen loader.
Feb 20 04:04:02 steffen-laptop pulseaudio[14025]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Feb 20 04:04:02 steffen-laptop pulseaudio[14025]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Feb 20 04:04:15 steffen-laptop pulseaudio[14025]: module-x11-xsmp.c: X11 session manager not running.
Feb 20 04:04:15 steffen-laptop pulseaudio[14025]: module.c: Failed to load  module "module-x11-xsmp" (argument: ""): initialization failed.
Feb 20 15:58:36 steffen-laptop pulseaudio[5708]: ltdl-bind-now.c: Failed to find original dlopen loader.
Feb 20 15:58:37 steffen-laptop pulseaudio[5710]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Feb 20 15:58:37 steffen-laptop pulseaudio[5710]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Feb 20 15:58:54 steffen-laptop pulseaudio[5710]: module-x11-xsmp.c: X11 session manager not running.
Feb 20 15:58:54 steffen-laptop pulseaudio[5710]: module.c: Failed to load  module "module-x11-xsmp" (argument: ""): initialization failed.
Feb 20 16:56:30 steffen-laptop Cleanup, done. Exitting... 
Feb 20 16:56:45 steffen-laptop pulseaudio[2712]: ltdl-bind-now.c: Failed to find original dlopen loader.
Feb 20 16:56:45 steffen-laptop pulseaudio[2714]: pid.c: Stale PID file, overwriting.
Feb 20 16:56:45 steffen-laptop pulseaudio[2714]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Feb 20 16:56:45 steffen-laptop pulseaudio[2714]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Feb 20 16:56:57 steffen-laptop pulseaudio[2714]: module-x11-xsmp.c: X11 session manager not running.
Feb 20 16:56:57 steffen-laptop pulseaudio[2714]: module.c: Failed to load  module "module-x11-xsmp" (argument: ""): initialization failed.
Feb 20 17:54:06 steffen-laptop pulseaudio[2228]: ltdl-bind-now.c: Failed to find original dlopen loader.
Feb 20 17:54:06 steffen-laptop pulseaudio[2230]: pid.c: Stale PID file, overwriting.
Feb 20 17:54:06 steffen-laptop pulseaudio[2230]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Feb 20 17:54:06 steffen-laptop pulseaudio[2230]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Feb 20 17:54:18 steffen-laptop pulseaudio[2230]: module-x11-xsmp.c: X11 session manager not running.
Feb 20 17:54:18 steffen-laptop pulseaudio[2230]: module.c: Failed to load  module "module-x11-xsmp" (argument: ""): initialization failed.
Feb 21 00:13:00 steffen-laptop pulseaudio[5720]: ltdl-bind-now.c: Failed to find original dlopen loader.
Feb 21 00:13:00 steffen-laptop pulseaudio[5722]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Feb 21 00:13:00 steffen-laptop pulseaudio[5722]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Feb 21 00:13:18 steffen-laptop pulseaudio[5722]: module-x11-xsmp.c: X11 session manager not running.
Feb 21 00:13:18 steffen-laptop pulseaudio[5722]: module.c: Failed to load  module "module-x11-xsmp" (argument: ""): initialization failed.
Feb 21 03:21:34 steffen-laptop pulseaudio[10642]: ltdl-bind-now.c: Failed to find original dlopen loader.
Feb 21 03:21:34 steffen-laptop pulseaudio[10646]: pid.c: Stale PID file, overwriting.
Feb 21 03:21:34 steffen-laptop pulseaudio[10646]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Feb 21 03:21:34 steffen-laptop pulseaudio[10646]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Feb 21 03:21:48 steffen-laptop pulseaudio[10646]: module-x11-xsmp.c: X11 session manager not running.
Feb 21 03:21:48 steffen-laptop pulseaudio[10646]: module.c: Failed to load  module "module-x11-xsmp" (argument: ""): initialization failed.
Feb 21 03:24:37 steffen-laptop Cleanup, done. Exitting... 
Feb 21 03:24:50 steffen-laptop pulseaudio[11154]: ltdl-bind-now.c: Failed to find original dlopen loader.
Feb 21 03:24:50 steffen-laptop pulseaudio[11156]: pid.c: Stale PID file, overwriting.
Feb 21 03:24:50 steffen-laptop pulseaudio[11156]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Feb 21 03:24:50 steffen-laptop pulseaudio[11156]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Feb 21 03:25:02 steffen-laptop pulseaudio[11156]: module-x11-xsmp.c: X11 session manager not running.
Feb 21 03:25:02 steffen-laptop pulseaudio[11156]: module.c: Failed to load  module "module-x11-xsmp" (argument: ""): initialization failed.
Feb 21 03:27:25 steffen-laptop Cleanup, done. Exitting... 
Feb 21 03:27:34 steffen-laptop pulseaudio[11599]: ltdl-bind-now.c: Failed to find original dlopen loader.
Feb 21 03:27:34 steffen-laptop pulseaudio[11601]: pid.c: Stale PID file, overwriting.
Feb 21 03:27:34 steffen-laptop pulseaudio[11601]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Feb 21 03:27:34 steffen-laptop pulseaudio[11601]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Feb 21 03:27:46 steffen-laptop pulseaudio[11601]: module-x11-xsmp.c: X11 session manager not running.
Feb 21 03:27:46 steffen-laptop pulseaudio[11601]: module.c: Failed to load  module "module-x11-xsmp" (argument: ""): initialization failed.
Feb 21 03:48:53 steffen-laptop pulseaudio[22873]: ltdl-bind-now.c: Failed to find original dlopen loader.
Feb 21 03:48:53 steffen-laptop pulseaudio[22877]: pid.c: Stale PID file, overwriting.
Feb 21 03:48:53 steffen-laptop pulseaudio[22877]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Feb 21 03:48:53 steffen-laptop pulseaudio[22877]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Feb 21 03:49:05 steffen-laptop pulseaudio[22877]: module-x11-xsmp.c: X11 session manager not running.
Feb 21 03:49:05 steffen-laptop pulseaudio[22877]: module.c: Failed to load  module "module-x11-xsmp" (argument: ""): initialization failed.
Feb 21 03:54:32 steffen-laptop pulseaudio[25759]: ltdl-bind-now.c: Failed to find original dlopen loader.
Feb 21 03:54:32 steffen-laptop pulseaudio[25761]: pid.c: Stale PID file, overwriting.
Feb 21 03:54:32 steffen-laptop pulseaudio[25761]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Feb 21 03:54:32 steffen-laptop pulseaudio[25761]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Feb 21 03:54:44 steffen-laptop pulseaudio[25761]: module-x11-xsmp.c: X11 session manager not running.
Feb 21 03:54:44 steffen-laptop pulseaudio[25761]: module.c: Failed to load  module "module-x11-xsmp" (argument: ""): initialization failed.
Feb 21 03:56:50 steffen-laptop Cleanup, done. Exitting... 
Feb 21 03:57:02 steffen-laptop pulseaudio[27053]: ltdl-bind-now.c: Failed to find original dlopen loader.
Feb 21 03:57:02 steffen-laptop pulseaudio[27055]: pid.c: Stale PID file, overwriting.
Feb 21 03:57:02 steffen-laptop pulseaudio[27055]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Feb 21 03:57:02 steffen-laptop pulseaudio[27055]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Feb 21 03:57:13 steffen-laptop pulseaudio[27055]: module-x11-xsmp.c: X11 session manager not running.
Feb 21 03:57:13 steffen-laptop pulseaudio[27055]: module.c: Failed to load  module "module-x11-xsmp" (argument: ""): initialization failed.
Feb 21 03:58:36 steffen-laptop Failed to open the panel socket 
Feb 21 03:58:37 steffen-laptop Failed to open the panel socket 
Feb 21 03:58:48 steffen-laptop pulseaudio[27976]: ltdl-bind-now.c: Failed to find original dlopen loader.
Feb 21 03:58:48 steffen-laptop pulseaudio[27978]: pid.c: Stale PID file, overwriting.
Feb 21 03:58:48 steffen-laptop pulseaudio[27978]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Feb 21 03:58:48 steffen-laptop pulseaudio[27978]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Feb 21 03:59:00 steffen-laptop pulseaudio[27978]: module-x11-xsmp.c: X11 session manager not running.
Feb 21 03:59:00 steffen-laptop pulseaudio[27978]: module.c: Failed to load  module "module-x11-xsmp" (argument: ""): initialization failed.
Feb 21 04:07:37 steffen-laptop pulseaudio[32481]: ltdl-bind-now.c: Failed to find original dlopen loader.
Feb 21 04:07:37 steffen-laptop pulseaudio[32483]: pid.c: Stale PID file, overwriting.
Feb 21 04:07:37 steffen-laptop pulseaudio[32483]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Feb 21 04:07:37 steffen-laptop pulseaudio[32483]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Feb 21 04:07:49 steffen-laptop pulseaudio[32483]: module-x11-xsmp.c: X11 session manager not running.
Feb 21 04:07:49 steffen-laptop pulseaudio[32483]: module.c: Failed to load  module "module-x11-xsmp" (argument: ""): initialization failed.
Feb 21 16:05:55 steffen-laptop pulseaudio[5775]: ltdl-bind-now.c: Failed to find original dlopen loader.
Feb 21 16:05:55 steffen-laptop pulseaudio[5777]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Feb 21 16:05:55 steffen-laptop pulseaudio[5777]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Feb 21 16:06:13 steffen-laptop pulseaudio[5777]: module-x11-xsmp.c: X11 session manager not running.
Feb 21 16:06:13 steffen-laptop pulseaudio[5777]: module.c: Failed to load  module "module-x11-xsmp" (argument: ""): initialization failed.
Feb 21 18:37:53 steffen-laptop pulseaudio[5777]: module-hal-detect.c: Error getting capability: org.freedesktop.Hal.NoSuchDevice: No device with id /org/freedesktop/Hal/devices/usb_device_5ac_1261_000A2700155C7C5E_if0_scsi_host_0_scsi_device_lun0_scsi_generic
Feb 21 21:13:05 steffen-laptop pulseaudio[7762]: ltdl-bind-now.c: Failed to find original dlopen loader.
Feb 21 21:13:05 steffen-laptop pulseaudio[7764]: pid.c: Stale PID file, overwriting.
Feb 21 21:13:05 steffen-laptop pulseaudio[7764]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Feb 21 21:13:05 steffen-laptop pulseaudio[7764]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Feb 21 21:13:17 steffen-laptop pulseaudio[7764]: module-x11-xsmp.c: X11 session manager not running.
Feb 21 21:13:17 steffen-laptop pulseaudio[7764]: module.c: Failed to load  module "module-x11-xsmp" (argument: ""): initialization failed.
Feb 22 03:25:35 steffen-laptop pulseaudio[5782]: ltdl-bind-now.c: Failed to find original dlopen loader.
Feb 22 03:25:35 steffen-laptop pulseaudio[5784]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Feb 22 03:25:35 steffen-laptop pulseaudio[5784]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Feb 22 03:25:53 steffen-laptop pulseaudio[5784]: module-x11-xsmp.c: X11 session manager not running.
Feb 22 03:25:53 steffen-laptop pulseaudio[5784]: module.c: Failed to load  module "module-x11-xsmp" (argument: ""): initialization failed.
Feb 22 04:36:06 steffen-laptop Cleanup, done. Exitting... 
Feb 22 04:37:17 steffen-laptop pulseaudio[4041]: ltdl-bind-now.c: Failed to find original dlopen loader.
Feb 22 04:37:17 steffen-laptop pulseaudio[4044]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Feb 22 04:37:17 steffen-laptop pulseaudio[4044]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Feb 22 04:37:35 steffen-laptop pulseaudio[4044]: module-x11-xsmp.c: X11 session manager not running.
Feb 22 04:37:35 steffen-laptop pulseaudio[4044]: module.c: Failed to load  module "module-x11-xsmp" (argument: ""): initialization failed.
Feb 22 04:53:25 steffen-laptop pulseaudio[5785]: ltdl-bind-now.c: Failed to find original dlopen loader.
Feb 22 04:53:25 steffen-laptop pulseaudio[5787]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Feb 22 04:53:25 steffen-laptop pulseaudio[5787]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Feb 22 04:53:43 steffen-laptop pulseaudio[5787]: module-x11-xsmp.c: X11 session manager not running.
Feb 22 04:53:43 steffen-laptop pulseaudio[5787]: module.c: Failed to load  module "module-x11-xsmp" (argument: ""): initialization failed.
Feb 22 05:15:36 steffen-laptop pulseaudio[5444]: ltdl-bind-now.c: Failed to find original dlopen loader.
Feb 22 05:15:36 steffen-laptop pulseaudio[5446]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Feb 22 05:15:36 steffen-laptop pulseaudio[5446]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Feb 22 05:15:54 steffen-laptop pulseaudio[5446]: module-x11-xsmp.c: X11 session manager not running.
Feb 22 05:15:54 steffen-laptop pulseaudio[5446]: module.c: Failed to load  module "module-x11-xsmp" (argument: ""): initialization failed.
Feb 22 05:25:46 steffen-laptop pulseaudio[10817]: ltdl-bind-now.c: Failed to find original dlopen loader.
Feb 22 05:25:46 steffen-laptop pulseaudio[10819]: pid.c: Stale PID file, overwriting.
Feb 22 05:25:46 steffen-laptop pulseaudio[10819]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Feb 22 05:25:46 steffen-laptop pulseaudio[10819]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Feb 22 05:25:58 steffen-laptop pulseaudio[10819]: module-x11-xsmp.c: X11 session manager not running.
Feb 22 05:25:58 steffen-laptop pulseaudio[10819]: module.c: Failed to load  module "module-x11-xsmp" (argument: ""): initialization failed.
Feb 22 05:33:02 steffen-laptop Cleanup, done. Exitting... 
Feb 22 05:33:13 steffen-laptop pulseaudio[16193]: ltdl-bind-now.c: Failed to find original dlopen loader.
Feb 22 05:33:13 steffen-laptop pulseaudio[16195]: pid.c: Stale PID file, overwriting.
Feb 22 05:33:13 steffen-laptop pulseaudio[16195]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Feb 22 05:33:13 steffen-laptop pulseaudio[16195]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Feb 22 05:33:25 steffen-laptop pulseaudio[16195]: module-x11-xsmp.c: X11 session manager not running.
Feb 22 05:33:25 steffen-laptop pulseaudio[16195]: module.c: Failed to load  module "module-x11-xsmp" (argument: ""): initialization failed.
Feb 22 05:34:52 steffen-laptop Cleanup, done. Exitting... 
Feb 22 05:35:03 steffen-laptop pulseaudio[17417]: ltdl-bind-now.c: Failed to find original dlopen loader.
Feb 22 05:35:03 steffen-laptop pulseaudio[17419]: pid.c: Stale PID file, overwriting.
Feb 22 05:35:03 steffen-laptop pulseaudio[17419]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Feb 22 05:35:03 steffen-laptop pulseaudio[17419]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Feb 22 05:35:14 steffen-laptop pulseaudio[17419]: module-x11-xsmp.c: X11 session manager not running.
Feb 22 05:35:14 steffen-laptop pulseaudio[17419]: module.c: Failed to load  module "module-x11-xsmp" (argument: ""): initialization failed.
Feb 22 10:32:22 steffen-laptop pulseaudio[5445]: ltdl-bind-now.c: Failed to find original dlopen loader.
Feb 22 10:32:22 steffen-laptop pulseaudio[5447]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Feb 22 10:32:22 steffen-laptop pulseaudio[5447]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Feb 22 10:32:39 steffen-laptop pulseaudio[5447]: module-x11-xsmp.c: X11 session manager not running.
Feb 22 10:32:39 steffen-laptop pulseaudio[5447]: module.c: Failed to load  module "module-x11-xsmp" (argument: ""): initialization failed.
```

---

### Post by markbuntu on 2009-02-22
W: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
W: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted

These messages usually mean that the user is not a member of the following groups

pulse
pulse-rt
pulse-access
You can fix that by making changes in System/Administration/Users and Groups. Be sure to add root to these.


Soft CPU time limit exhausted, terminating.
Hard CPU time limit exhausted, terminating forcibly.
Aborted

These messages may be just a result from pulse not having real time kernel access because or the user and group permissions problem. 

Could someone please check this out and get back here.

---

### Post by BazookaAce on 2009-02-22
Thanks for the answer, but both, user and root have full system permission, so it can't be that? Or...?

---

### Post by markbuntu on 2009-02-22
It is looking more and more like a kernel scheduling problem.....

---

### Post by BazookaAce on 2009-02-22
Damn, i hate installing new kernels. Everytime i'm doing it, like yesterday, the computer freezed after startup. It's always some problems with me and my enemy; Mr. Custom Kernel :(

---

### Post by markbuntu on 2009-02-22
If you are building custom kernels then you can probably fix this with the next one you build. There has been some talk about this issue at the pulseaudio mailing list the last day or so. 

I am not that familiar with kernel ins and outs but from what I could gather if the scheduling is set for too high a number ie 1000 instead of 100 then pulseaudio not allowed to access the kernel in time to refill the alsa buffer which is a fixed size. 

It seems that SUSE has accomplished this with their latest release. This has pushed audio latency to about 285 msec or so instead of <5 which is normal. Maybe the Ubuntu team is doing something similar.

---

### Post by BazookaAce on 2009-02-23
I'm not building my own kernel, but i used Sickboy-kernel for the Aspire One, and everytime i'm trying it, i'm begging for trouble. But i listened to music quite a while yesterday, and it worked fine then, so i'll start Amarok now, and try again, and see how long it goes without any errors :)

---

### Post by BazookaAce on 2009-02-23
[SIZE="3"]Update:[/SIZE] 

After several hours with music it's still going strong! Isn't that just typical! Just wait till this thread is "Solved", cause then ladys and gentlemen, the problem will be back ;)

But just be prepeard! It will happen :p So, have a nice day!

---

