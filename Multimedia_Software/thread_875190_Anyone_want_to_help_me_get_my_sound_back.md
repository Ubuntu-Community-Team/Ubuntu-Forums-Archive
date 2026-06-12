---
title: "Anyone want to help me get my sound back?"
date: 2008-07-30
forum: Multimedia Software
---

### Post by billybag on 2008-07-30
I lost my sound the other day. I have no idea why. I use pulse audio and have followed this guide: [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578) as it was the guide i had to use to get it working in the first place. I am using linux mint 5, but it is basically just Ubuntu Hardy. i have searched and tried all i can... i hope someone feels up to this.

```
$ pulseaudio -k; sleep 4; pulseaudio -vv
I: main.c: Called SUID root and real-time/high-priority scheduling was requested in the configuration. However, we lack the necessary priviliges:
I: main.c: We are not in group 'pulse-rt' and PolicyKit refuse to grant us priviliges. Dropping SUID again.
I: main.c: For enabling real-time scheduling please acquire the appropriate PolicyKit priviliges, or become a member of 'pulse-rt', or increase the RLIMIT_NICE/RLIMIT_RTPRIO resource limits for this user.
I: main.c: Note that real-time/high-priority scheduling is NOT normally required. If you experience crackling or other sound anomalies, consider one or more of the above solutions.
I: main.c: High-priority scheduling enabled in configuration but now allowed by policy. Disabling forcibly.
I: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
I: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
I: main.c: This is PulseAudio 0.9.10
I: main.c: Page size is 4096 bytes
I: main.c: Fresh high-resolution timers available! Bon appetit!
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9/modules/module-hal-detect.so': success
I: module-hal-detect.c: Trying capability alsa
I: module-hal-detect.c: Trying capability oss
I: module-hal-detect.c: Loaded 0 modules.
I: module.c: Loaded "module-hal-detect" (index: #0; argument: "").
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9/modules/module-esound-protocol-unix.so': success
I: module.c: Loaded "module-esound-protocol-unix" (index: #1; argument: "").
I: protocol-native.c: loading cookie from disk.
I: module.c: Loaded "module-native-protocol-unix" (index: #2; argument: "").
I: module.c: Loaded "module-volume-restore" (index: #3; argument: "").
I: module-default-device-restore.c: Saved default sink 'combined' not existant, not restoring default sink setting.
I: module-default-device-restore.c: Saved default source 'combined.monitor' not existant, not restoring default source setting.
I: module.c: Loaded "module-default-device-restore" (index: #4; argument: "").
I: module.c: Loaded "module-rescue-streams" (index: #5; argument: "").
I: module.c: Loaded "module-suspend-on-idle" (index: #6; argument: "").
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9/modules/module-gconf.so': success
D: module-gconf.c: Loading module 'module-combine' with args '' due to GConf configuration.
I: sink.c: Created sink 0 "combined" with sample spec "s16le 2ch 44100Hz"
I: source.c: Created source 0 "combined.monitor" with sample spec "s16le 2ch 44100Hz"
D: module-combine.c: Thread starting up
D: rtpoll.c: Acquired POSIX realtime signal SIGRTMIN+29
D: module-suspend-on-idle.c: Source combined.monitor becomes idle.
D: module-suspend-on-idle.c: Sink combined becomes idle.
I: module.c: Loaded "module-combine" (index: #7; argument: "").
I: module.c: Loaded "module-gconf" (index: #8; argument: "").
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9/modules/module-x11-publish.so': success
D: module-x11-publish.c: using already loaded auth cookie.
I: module.c: Loaded "module-x11-publish" (index: #9; argument: "").
I: main.c: Daemon startup complete.
D: module-hal-detect.c: dbus: interface=org.freedesktop.DBus, path=/org/freedesktop/DBus, member=NameAcquired
I: module-suspend-on-idle.c: Sink combined idle for too long, suspending ...
I: module-combine.c: Device suspended...
I: module-suspend-on-idle.c: Source combined.monitor idle for too long, suspending ...
I: client.c: Created 0 "Native client (UNIX socket client)"
I: protocol-native.c: Got credentials: uid=1000 gid=1000 success=1
I: protocol-native.c: Enabled SHM for new connection
I: client.c: Client 0 changed name from "Native client (UNIX socket client)" to "Pidgin"
I: module-volume-restore.c: Restoring volume for <pulsecore/protocol-native.c$Pidgin>
I: module-combine.c: Resumed successfully...
D: module-suspend-on-idle.c: Sink combined becomes idle.
D: module-suspend-on-idle.c: Sink combined becomes busy.
I: resampler.c: Using resampler 'speex-float-3'
I: resampler.c: Using float32le as working format.
I: resampler.c: Choosing speex quality setting 3.
I: sink-input.c: Created input 0 "Playback Stream" on combined with sample spec s16le 2ch 22050Hz and channel map front-left,front-right
D: memblockq.c: memblockq requested: maxlength=35200, tlength=17600, base=4, prebuf=16720, minreq=880
D: memblockq.c: memblockq sanitized: maxlength=35200, tlength=17600, base=4, prebuf=16720, minreq=880
I: module-volume-restore.c: Saving sink for <pulsecore/protocol-native.c$Pidgin>
I: client.c: Created 1 "Native client (UNIX socket client)"
I: protocol-native.c: Got credentials: uid=1000 gid=1000 success=1
I: protocol-native.c: Enabled SHM for new connection
I: client.c: Client 1 changed name from "Native client (UNIX socket client)" to "Pidgin"
I: module-volume-restore.c: Restoring sink for <pulsecore/protocol-native.c$Pidgin>
I: module-volume-restore.c: Restoring volume for <pulsecore/protocol-native.c$Pidgin>
D: module-suspend-on-idle.c: Sink combined becomes busy.
I: resampler.c: Using resampler 'speex-float-3'
I: resampler.c: Using float32le as working format.
I: resampler.c: Choosing speex quality setting 3.
I: sink-input.c: Created input 1 "Playback Stream" on combined with sample spec s16le 2ch 22050Hz and channel map front-left,front-right
D: memblockq.c: memblockq requested: maxlength=35200, tlength=17600, base=4, prebuf=16720, minreq=880
D: memblockq.c: memblockq sanitized: maxlength=35200, tlength=17600, base=4, prebuf=16720, minreq=880
I: sink-input.c: Freeing output 0 "Playback Stream"
I: client.c: Freed 0 "Pidgin"
I: protocol-native.c: connection died.
I: client.c: Created 2 "Native client (UNIX socket client)"
I: protocol-native.c: Got credentials: uid=1000 gid=1000 success=1
I: protocol-native.c: Enabled SHM for new connection
I: client.c: Client 2 changed name from "Native client (UNIX socket client)" to "Pidgin"
I: module-volume-restore.c: Restoring sink for <pulsecore/protocol-native.c$Pidgin>
I: module-volume-restore.c: Restoring volume for <pulsecore/protocol-native.c$Pidgin>
D: module-suspend-on-idle.c: Sink combined becomes busy.
I: resampler.c: Using resampler 'speex-float-3'
I: resampler.c: Using float32le as working format.
I: resampler.c: Choosing speex quality setting 3.
I: sink-input.c: Created input 2 "Playback Stream" on combined with sample spec s16le 2ch 22050Hz and channel map front-left,front-right
D: memblockq.c: memblockq requested: maxlength=35200, tlength=17600, base=4, prebuf=16720, minreq=880
D: memblockq.c: memblockq sanitized: maxlength=35200, tlength=17600, base=4, prebuf=16720, minreq=880
I: sink-input.c: Freeing output 1 "Playback Stream"
I: client.c: Freed 1 "Pidgin"
I: protocol-native.c: connection died.
I: client.c: Created 3 "Native client (UNIX socket client)"
I: protocol-native.c: Got credentials: uid=1000 gid=1000 success=1
I: protocol-native.c: Enabled SHM for new connection
I: client.c: Client 3 changed name from "Native client (UNIX socket client)" to "Pidgin"
I: module-volume-restore.c: Restoring sink for <pulsecore/protocol-native.c$Pidgin>
I: module-volume-restore.c: Restoring volume for <pulsecore/protocol-native.c$Pidgin>
D: module-suspend-on-idle.c: Sink combined becomes busy.
I: resampler.c: Using resampler 'speex-float-3'
I: resampler.c: Using float32le as working format.
I: resampler.c: Choosing speex quality setting 3.
I: sink-input.c: Created input 3 "Playback Stream" on combined with sample spec s16le 2ch 22050Hz and channel map front-left,front-right
D: memblockq.c: memblockq requested: maxlength=35200, tlength=17600, base=4, prebuf=16720, minreq=880
D: memblockq.c: memblockq sanitized: maxlength=35200, tlength=17600, base=4, prebuf=16720, minreq=880
I: sink-input.c: Freeing output 2 "Playback Stream"
I: client.c: Freed 2 "Pidgin"
I: protocol-native.c: connection died.
D: module-suspend-on-idle.c: Sink combined becomes idle.
D: module-suspend-on-idle.c: Sink combined becomes idle.
I: sink-input.c: Freeing output 3 "Playback Stream"
I: client.c: Freed 3 "Pidgin"
I: protocol-native.c: connection died.
I: module-suspend-on-idle.c: Sink combined idle for too long, suspending ...
I: module-combine.c: Device suspended...
D: module-hal-detect.c: dbus: interface=org.freedesktop.Hal.Device, path=/org/freedesktop/Hal/devices/computer_power_supply_battery_BAT0, member=PropertyModified
I: module-volume-restore.c: Saving rules...
D: module-volume-restore.c: Successfully saved rules...




```

---

### Post by billybag on 2008-07-31
Anything at all. Please?

---

### Post by AFarris01 on 2008-09-13
Hey man, sorry your having issues, and sorry nobody has replied until now.

if you're still having an issue, then the first lines in the output you posted lend some clue to a possible problem.

it looks like you're trying to run pulseaudio as a system instance, with realtime priority.  the trouble is that your user does not appear to be a member of the appropriate group "pulse-rt" which is required to allow pulseaudio to run as a system instance.  so... to fix that issue in ubuntu, you would go to "system> administration > users and groups", type in your password/unlock it, click 'Manage groups', and scroll down until you find the group 'pulse-rt'.  then select it, hit 'properties, and click the checkboxes next to 'root' and whichever users you want to have access tot he sound server.  while you're there, you could try going through all the groups labeled 'pulse-*' and make sure the same members are checked in all of them as well.

homefully htis will help you out, if you havent already fixed it!

---

