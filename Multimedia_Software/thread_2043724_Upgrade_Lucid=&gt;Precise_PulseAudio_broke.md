---
title: "Upgrade Lucid=&gt;Precise: PulseAudio broke"
date: 2012-08-17
forum: Multimedia Software
---

### Post by produnis on 2012-08-17
I upgraded my server from Lucid-64 to Precise-64. After the updrade went through without problems, I face PulseAudio-Errors since reboot.


The PC boots into Unity, but PulseAudio won't start, leaving me unable to adjust volume (It has "--" next to the volume-icon in upper panel). 
All Menues in "Audio Settings" are empty, having no device in any list.

I can play music (e.g. via audacious) though...


I removed "~/.pulse*" and rebooted, but that didnt fix my problem.

Starting PulseAudio in Debug-Mode, it gives me:

```

produnis@hoerspiel:~$ pulseaudio -vv
I: [pulseaudio] main.c: setrlimit(RLIMIT_NICE, (31, 31)) fehlgeschlagen: Die Operation ist nicht erlaubt
I: [pulseaudio] main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) fehlgeschlagen: Die Operation ist nicht erlaubt
D: [pulseaudio] core-rtclock.c: Timer slack is set to 50 us.
D: [pulseaudio] core-util.c: RealtimeKit worked.
I: [pulseaudio] core-util.c: Successfully gained nice level -11.
I: [pulseaudio] main.c: Dies ist PulseAudio 1.1
D: [pulseaudio] main.c: Kompilier-Host: x86_64-pc-linux-gnu
D: [pulseaudio] main.c: Kompilier-CFLAGS: -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -g -O2 -fstack-prot
ector --param=ssp-buffer-size=4 -Wformat -Wformat-security -Werror=format-security -Wall -W -Wextra -pipe -Wno-long-long -Wvla -Wno-overlen
gth-strings -Wunsafe-loop-optimizations -Wundef -Wformat=2 -Wlogical-op -Wsign-compare -Wmissing-include-dirs -Wformat-nonliteral -Wpointer
-arith -Winit-self -Wdeclaration-after-statement -Wfloat-equal -Wmissing-prototypes -Wredundant-decls -Wmissing-declarations -Wmissing-nore
turn -Wshadow -Wendif-labels -Wcast-align -Wstrict-aliasing -Wwrite-strings -Wno-unused-parameter -ffast-math -Wp,-D_FORTIFY_SOURCE=2 -fno-
common -fdiagnostics-show-option
D: [pulseaudio] main.c: Laufe auf Host: Linux x86_64 3.2.0-29-generic #46-Ubuntu SMP Fri Jul 27 17:03:23 UTC 2012
D: [pulseaudio] main.c: 1 CPUs gefunden.
I: [pulseaudio] main.c: Seitengröße ist 4096 Bytes.
D: [pulseaudio] main.c: Kompiliere mit Valgrind-Unterstützung: nein
D: [pulseaudio] main.c: Läuft im Valgrind-Modus: no
D: [pulseaudio] main.c: Wird in VM ausgeführt: no
D: [pulseaudio] main.c: Optimiertes Build: ja
D: [pulseaudio] main.c: Alle Ansprüche aktiviert.
I: [pulseaudio] main.c: System- ID ist 70ea37d7dc84bda395edbe914bd9b29c.
I: [pulseaudio] main.c: System- ID ist 70ea37d7dc84bda395edbe914bd9b29c-1345190919.246363-729461659.
I: [pulseaudio] main.c: Nutze Laufzeit-Verzeichnis /home/produnis/.pulse/70ea37d7dc84bda395edbe914bd9b29c-runtime.
I: [pulseaudio] main.c: Nutze Zustands-Verzeichnis /home/produnis/.pulse.
I: [pulseaudio] main.c: Modul-Verzeichnis /usr/lib/pulse-1.1/modules benutzen.
I: [pulseaudio] main.c: Laufe im System-Modus: no
W: [pulseaudio] pid.c: Stale PID file, overwriting.
I: [pulseaudio] main.c: Neue hochauslösende Timer verfügbar! Guten Appetit!
D: [pulseaudio] memblock.c: Using shared memory pool with 1024 slots of size 64,0 KB each, total size is 64,0 MB, maximum usable slot size 
is 65472
I: [pulseaudio] cpu-x86.c: CPU flags: CMOV MMX SSE SSE2 SSE3 MMXEXT 3DNOW 3DNOWEXT 
I: [pulseaudio] svolume_mmx.c: Initialising MMX optimized volume functions.
I: [pulseaudio] remap_mmx.c: Initialising MMX optimized remappers.
I: [pulseaudio] svolume_sse.c: Initialising SSE2 optimized volume functions.
I: [pulseaudio] remap_sse.c: Initialising SSE2 optimized remappers.
I: [pulseaudio] sconv_sse.c: Initialising SSE2 optimized conversions.
I: [pulseaudio] svolume_orc.c: Initialising ORC optimized volume functions.
D: [pulseaudio] database-tdb.c: Opened TDB database '/home/produnis/.pulse/70ea37d7dc84bda395edbe914bd9b29c-device-volumes.tdb'
I: [pulseaudio] module-device-restore.c: Successfully opened database file '/home/produnis/.pulse/70ea37d7dc84bda395edbe914bd9b29c-device-v
olumes'.
I: [pulseaudio] module.c: Loaded "module-device-restore" (index: #0; argument: "").
D: [pulseaudio] database-tdb.c: Opened TDB database '/home/produnis/.pulse/70ea37d7dc84bda395edbe914bd9b29c-stream-volumes.tdb'
I: [pulseaudio] module-stream-restore.c: Successfully opened database file '/home/produnis/.pulse/70ea37d7dc84bda395edbe914bd9b29c-stream-v
olumes'.
D: [pulseaudio] protocol-dbus.c: Interface org.PulseAudio.Ext.StreamRestore1 added for object /org/pulseaudio/stream_restore1
I: [pulseaudio] module.c: Loaded "module-stream-restore" (index: #1; argument: "").
D: [pulseaudio] database-tdb.c: Opened TDB database '/home/produnis/.pulse/70ea37d7dc84bda395edbe914bd9b29c-card-database.tdb'
I: [pulseaudio] module-card-restore.c: Successfully opened database file '/home/produnis/.pulse/70ea37d7dc84bda395edbe914bd9b29c-card-database'.
I: [pulseaudio] module.c: Loaded "module-card-restore" (index: #2; argument: "").
I: [pulseaudio] module.c: Loaded "module-augment-properties" (index: #3; argument: "").
D: [pulseaudio] cli-command.c: Checking for existence of '/usr/lib/pulse-1.1/modules/module-udev-detect.so': success
D: [pulseaudio] module-udev-detect.c: /dev/snd/controlC0 is accessible: yes
D: [pulseaudio] module-udev-detect.c: /devices/pci0000:00/0000:00:05.0/sound/card0 is busy: yes
I: [pulseaudio] module-udev-detect.c: Found 1 cards.
I: [pulseaudio] module.c: Loaded "module-udev-detect" (index: #4; argument: "").
D: [pulseaudio] cli-command.c: Checking for existence of '/usr/lib/pulse-1.1/modules/module-jackdbus-detect.so': failure
D: [pulseaudio] cli-command.c: Checking for existence of '/usr/lib/pulse-1.1/modules/module-bluetooth-discover.so': success
D: [pulseaudio] dbus-util.c: Successfully connected to D-Bus system bus e1b432327048753c4e29213e0000001c as :1.149
D: [pulseaudio] bluetooth-util.c: dbus: interface=org.freedesktop.DBus, path=/org/freedesktop/DBus, member=NameAcquired
I: [pulseaudio] module.c: Loaded "module-bluetooth-discover" (index: #5; argument: "").
D: [pulseaudio] cli-command.c: Checking for existence of '/usr/lib/pulse-1.1/modules/module-esound-protocol-unix.so': success
I: [pulseaudio] module.c: Loaded "module-esound-protocol-unix" (index: #6; argument: "").
I: [pulseaudio] module.c: Loaded "module-native-protocol-unix" (index: #7; argument: "").
D: [pulseaudio] cli-command.c: Checking for existence of '/usr/lib/pulse-1.1/modules/module-gconf.so': success
D: [pulseaudio] module-gconf.c: Loading module 'module-native-protocol-tcp' with args 'auth-anonymous=1' due to GConf configuration.
I: [pulseaudio] module.c: Loaded "module-native-protocol-tcp" (index: #8; argument: "auth-anonymous=1").
D: [pulseaudio] module-gconf.c: Loading module 'module-esound-protocol-tcp' with args 'auth-anonymous=1' due to GConf configuration.
I: [pulseaudio] module.c: Loaded "module-esound-protocol-tcp" (index: #9; argument: "auth-anonymous=1").
D: [pulseaudio] module-gconf.c: Loading module 'module-zeroconf-publish' with args '' due to GConf configuration.
D: [pulseaudio] module-zeroconf-publish.c: Publishing services in Zeroconf
I: [pulseaudio] module.c: Loaded "module-zeroconf-publish" (index: #10; argument: "").
D: [pulseaudio] module-gconf.c: Loading module 'module-zeroconf-discover' with args '' due to GConf configuration.
I: [pulseaudio] module.c: Loaded "module-zeroconf-discover" (index: #11; argument: "").
D: [pulseaudio] module-gconf.c: Loading module 'module-combine' with args '' due to GConf configuration.
W: [pulseaudio] module.c: module-combine is deprecated: Please use module-combine-sink instead of module-combine!
W: [pulseaudio] module-combine.c: We will now load module-combine-sink. Please make sure to remove module-combine from your configuration.
D: [pulseaudio] module-device-restore.c: Database contains invalid data for key: sink:combined (probably pre-v1.0 data)
D: [pulseaudio] module-device-restore.c: Attempting to load legacy (pre-v1.0) data for key: sink:combined
D: [pulseaudio] module-device-restore.c: Size does not match.
D: [pulseaudio] module-device-restore.c: Unable to load legacy (pre-v1.0) data for key: sink:combined. Ignoring.
D: [pulseaudio] module-device-restore.c: Database contains invalid data for key: sink:combined:null
I: [pulseaudio] sink.c: Created sink 0 "combined" with sample spec s16le 2ch 44100Hz and channel map front-left,front-right
I: [pulseaudio] sink.c:     device.class = "filter"
I: [pulseaudio] sink.c:     device.description = "Simultaneous Output"
I: [pulseaudio] sink.c:     device.icon_name = "audio-card"
D: [pulseaudio] core-subscribe.c: Dropped redundant event due to change event.
D: [pulseaudio] module-device-restore.c: Database contains invalid data for key: source:combined.monitor (probably pre-v1.0 data)
D: [pulseaudio] module-device-restore.c: Attempting to load legacy (pre-v1.0) data for key: source:combined.monitor
D: [pulseaudio] module-device-restore.c: Size does not match.
D: [pulseaudio] module-device-restore.c: Unable to load legacy (pre-v1.0) data for key: source:combined.monitor. Ignoring.
D: [pulseaudio] module-device-restore.c: Database contains invalid data for key: source:combined.monitor:null
I: [pulseaudio] source.c: Created source 0 "combined.monitor" with sample spec s16le 2ch 44100Hz and channel map front-left,front-right
I: [pulseaudio] source.c:     device.description = "Monitor of Simultaneous Output"
I: [pulseaudio] source.c:     device.class = "monitor"
I: [pulseaudio] source.c:     device.icon_name = "audio-input-microphone"
D: [combine] module-combine-sink.c: Thread starting up
D: [combine] core-util.c: RealtimeKit worked.
I: [combine] core-util.c: Successfully enabled SCHED_RR scheduling for thread, with priority 6.
Killed

```

```
produnis@hoerspiel:~$ ps -C pulse
  PID TTY          TIME CMD
produnis@hoerspiel:~$ 
```

Any help welcome!

---

### Post by ebernardez on 2012-11-11
I have a very similar problem.

In my case, I've installed ubuntu 12.04, 32 bits, not server, in an empty partition. After that, I move /home to a different partition.

Although the volume control is enable in the choosing session screen, and even in the guest session, every time my personal session starts, the volume control gets disable (--- symbol next to the volume-icon in upper panel).

I can play music, but all the audio controls are disable.

I haven't found any solution yet.

---

