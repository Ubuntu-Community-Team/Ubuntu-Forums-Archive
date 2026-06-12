---
title: "pulseaudio fails after new install of 9.10 64 bit ( module-console-kit )"
date: 2010-01-19
forum: Multimedia Software
---

### Post by hanasaki on 2010-01-19
Linux usa 2.6.31-17-generic #54-Ubuntu SMP Thu Dec 10 17:01:44 UTC 2009 x86_64 GNU/Linux

Jan 19 12:13:24 usa pulseaudio[17720]: module-console-kit.c: GetSessionsForUnixUser() call failed: org.freedesktop.DBus.Error.Spawn.ExecFailed: Failed to execute program /lib/dbus-1.0/dbus-daemon-launch-helper: Success
Jan 19 12:13:24 usa pulseaudio[17720]: module.c: Failed to load  module "module-console-kit" (argument: ""): initialization failed.
Jan 19 12:13:24 usa pulseaudio[17720]: main.c: Module load failed.
Jan 19 12:13:24 usa pulseaudio[17720]: main.c: Failed to initialize daemon.
Jan 19 12:13:24 usa pulseaudio[17718]: main.c: Daemon startup failed.

lspci 
00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge
00:01.0 PCI bridge: ASUSTeK Computer Inc. Device 9602
00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)
00:06.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 2)
00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode]
00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller
00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller
00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)
00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)
00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon HD 3200 Graphics
01:05.1 Audio device: ATI Technologies Inc RS780 Azalia controller
02:00.0 FireWire (IEEE 1394): JMicron Technology Corp. IEEE 1394 Host Controller
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)

pkill pulseaudio; sleep 2; pulseaudio -vv
I: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
I: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
D: core-rtclock.c: Timer slack is set to 50 us.
I: core-util.c: Failed to acquire high-priority scheduling: No such file or directory
I: main.c: This is PulseAudio 0.9.19
D: main.c: Compilation host: x86_64-pc-linux-gnu
D: main.c: Compilation CFLAGS: -g -O2 -g -Wall -O3 -Wall -W -Wextra -pipe -Wno-long-long -Winline -Wvla -Wno-overlength-strings -Wunsafe-loop-optimizations -Wundef -Wformat=2 -Wlogical-op -Wsign-compare -Wformat-security -Wmissing-include-dirs -Wformat-nonliteral -Wold-style-definition -Wpointer-arith -Winit-self -Wdeclaration-after-statement -Wfloat-equal -Wmissing-prototypes -Wstrict-prototypes -Wredundant-decls -Wmissing-declarations -Wmissing-noreturn -Wshadow -Wendif-labels -Wcast-align -Wstrict-aliasing=2 -Wwrite-strings -Wno-unused-parameter -ffast-math -Wp,-D_FORTIFY_SOURCE=2 -fno-common -fdiagnostics-show-option
D: main.c: Running on host: Linux x86_64 2.6.31-17-generic #54-Ubuntu SMP Thu Dec 10 17:01:44 UTC 2009
D: main.c: Found 2 CPUs.
I: main.c: Page size is 4096 bytes
D: main.c: Compiled with Valgrind support: no
D: main.c: Running in valgrind mode: no
D: main.c: Optimized build: yes
D: main.c: All asserts enabled.
I: main.c: Machine ID is 7f2f5873d4fa5ad06ed8a5fa4b53de11.
I: main.c: Using runtime directory /home/user/.pulse/7f2f5873d4fa5ad06ed8a5fa4b53de11-runtime.
I: main.c: Using state directory /home/user/.pulse.
I: main.c: Using modules directory /usr/lib/pulse-0.9.19/modules.
I: main.c: Running in system mode: no
I: main.c: Fresh high-resolution timers available! Bon appetit!
I: cpu-x86.c: CPU flags: MMX SSE SSE2 SSE3 MMXEXT 3DNOW 3DNOWEXT 
I: svolume_mmx.c: Initialising MMX optimized functions.
I: remap_mmx.c: Initialising MMX optimized remappers.
I: svolume_sse.c: Initialising SSE2 optimized functions.
I: remap_sse.c: Initialising SSE2 optimized remappers.
I: sconv_sse.c: Initialising SSE2 optimized conversions.
D: memblock.c: Using shared memory pool with 1024 slots of size 64.0 KiB each, total size is 64.0 MiB, maximum usable slot size is 65472
D: database-tdb.c: Opened TDB database '/home/user/.pulse/7f2f5873d4fa5ad06ed8a5fa4b53de11-device-volumes.tdb'
I: module-device-restore.c: Sucessfully opened database file '/home/user/.pulse/7f2f5873d4fa5ad06ed8a5fa4b53de11-device-volumes'.
I: module.c: Loaded "module-device-restore" (index: #0; argument: "").
D: database-tdb.c: Opened TDB database '/home/user/.pulse/7f2f5873d4fa5ad06ed8a5fa4b53de11-stream-volumes.tdb'
I: module-stream-restore.c: Sucessfully opened database file '/home/user/.pulse/7f2f5873d4fa5ad06ed8a5fa4b53de11-stream-volumes'.
I: module.c: Loaded "module-stream-restore" (index: #1; argument: "").
D: database-tdb.c: Opened TDB database '/home/user/.pulse/7f2f5873d4fa5ad06ed8a5fa4b53de11-card-database.tdb'
I: module-card-restore.c: Sucessfully opened database file '/home/user/.pulse/7f2f5873d4fa5ad06ed8a5fa4b53de11-card-database'.
I: module.c: Loaded "module-card-restore" (index: #2; argument: "").
I: module.c: Loaded "module-augment-properties" (index: #3; argument: "").
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9.19/modules/module-udev-detect.so': success
D: module-udev-detect.c: /dev/snd/controlC2 is accessible: no
D: module-udev-detect.c: /dev/snd/controlC1 is accessible: no
D: module-udev-detect.c: /dev/snd/controlC0 is accessible: no
I: module-udev-detect.c: Found 3 cards.
I: module.c: Loaded "module-udev-detect" (index: #4; argument: "").
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9.19/modules/module-bluetooth-discover.so': success
D: dbus-util.c: Successfully connected to D-Bus system bus 4b84b039bf4504238c7e0a654b5413b5 as :1.108971
D: bluetooth-util.c: dbus: interface=org.freedesktop.DBus, path=/org/freedesktop/DBus, member=NameAcquired
D: bluetooth-util.c: dbus: interface=org.freedesktop.DBus.Introspectable, path=/, member=Introspect
D: bluetooth-util.c: Bluetooth daemon is apparently not available.
I: module.c: Loaded "module-bluetooth-discover" (index: #5; argument: "").
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9.19/modules/module-esound-protocol-unix.so': success
I: module.c: Loaded "module-esound-protocol-unix" (index: #6; argument: "").
I: module.c: Loaded "module-native-protocol-unix" (index: #7; argument: "").
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9.19/modules/module-gconf.so': success
I: module.c: Loaded "module-gconf" (index: #8; argument: "").
I: module.c: Loaded "module-default-device-restore" (index: #9; argument: "").
I: module.c: Loaded "module-rescue-streams" (index: #10; argument: "").
D: module-always-sink.c: Autoloading null-sink as no other sinks detected.
I: sink.c: Created sink 0 "auto_null" with sample spec s16le 2ch 44100Hz and channel map front-left,front-right
I: sink.c:     device.description = "Dummy Output"
I: sink.c:     device.class = "abstract"
I: sink.c:     device.icon_name = "audio-card"
D: core-subscribe.c: Dropped redundant event due to change event.
I: source.c: Created source 0 "auto_null.monitor" with sample spec s16le 2ch 44100Hz and channel map front-left,front-right
I: source.c:     device.description = "Monitor of Dummy Output"
I: source.c:     device.class = "monitor"
I: source.c:     device.icon_name = "audio-input-microphone"
D: module-null-sink.c: Thread starting up
I: module.c: Loaded "module-null-sink" (index: #11; argument: "sink_name=auto_null sink_properties='device.description="Dummy Output"'").
I: module.c: Loaded "module-always-sink" (index: #12; argument: "").
I: module.c: Loaded "module-intended-roles" (index: #13; argument: "").
D: module-suspend-on-idle.c: Sink auto_null becomes idle, timeout in 5 seconds.
I: module.c: Loaded "module-suspend-on-idle" (index: #14; argument: "").
E: module-console-kit.c: GetSessionsForUnixUser() call failed: org.freedesktop.DBus.Error.Spawn.ExecFailed: Failed to execute program /lib/dbus-1.0/dbus-daemon-launch-helper: Success
E: module.c: Failed to load  module "module-console-kit" (argument: ""): initialization failed.
E: main.c: Module load failed.
E: main.c: Failed to initialize daemon.
I: module.c: Unloading "module-device-restore" (index: #0).
I: module.c: Unloaded "module-device-restore" (index: #0).
D: core-subscribe.c: Dropped redundant event due to remove event.
I: module.c: Unloading "module-stream-restore" (index: #1).
I: module.c: Unloaded "module-stream-restore" (index: #1).
D: core-subscribe.c: Dropped redundant event due to remove event.
I: module.c: Unloading "module-card-restore" (index: #2).
I: module.c: Unloaded "module-card-restore" (index: #2).
D: core-subscribe.c: Dropped redundant event due to remove event.
I: module.c: Unloading "module-augment-properties" (index: #3).
I: module.c: Unloaded "module-augment-properties" (index: #3).
D: core-subscribe.c: Dropped redundant event due to remove event.
I: module.c: Unloading "module-udev-detect" (index: #4).
I: module.c: Unloaded "module-udev-detect" (index: #4).
D: core-subscribe.c: Dropped redundant event due to remove event.
I: module.c: Unloading "module-bluetooth-discover" (index: #5).
I: module.c: Unloaded "module-bluetooth-discover" (index: #5).
D: core-subscribe.c: Dropped redundant event due to remove event.
I: module.c: Unloading "module-esound-protocol-unix" (index: #6).
I: module.c: Unloaded "module-esound-protocol-unix" (index: #6).
D: core-subscribe.c: Dropped redundant event due to remove event.
I: module.c: Unloading "module-native-protocol-unix" (index: #7).
I: module.c: Unloaded "module-native-protocol-unix" (index: #7).
D: core-subscribe.c: Dropped redundant event due to remove event.
I: module.c: Unloading "module-gconf" (index: #8).
I: module.c: Unloaded "module-gconf" (index: #8).
D: core-subscribe.c: Dropped redundant event due to remove event.
I: module.c: Unloading "module-default-device-restore" (index: #9).
I: module.c: Unloaded "module-default-device-restore" (index: #9).
D: core-subscribe.c: Dropped redundant event due to remove event.
I: module.c: Unloading "module-rescue-streams" (index: #10).
I: module.c: Unloaded "module-rescue-streams" (index: #10).
D: core-subscribe.c: Dropped redundant event due to remove event.
I: module.c: Unloading "module-null-sink" (index: #11).
D: module-always-sink.c: Autoloaded null-sink removed
D: core-subscribe.c: Dropped redundant event due to remove event.
D: core-subscribe.c: Dropped redundant event due to remove event.
D: core-subscribe.c: Dropped redundant event due to remove event.
D: core-subscribe.c: Dropped redundant event due to remove event.
D: module-null-sink.c: Thread shutting down
I: sink.c: Freeing sink 0 "auto_null"
I: source.c: Freeing source 0 "auto_null.monitor"
I: module.c: Unloaded "module-null-sink" (index: #11).
D: core-subscribe.c: Dropped redundant event due to remove event.
I: module.c: Unloading "module-always-sink" (index: #12).
I: module.c: Unloaded "module-always-sink" (index: #12).
D: core-subscribe.c: Dropped redundant event due to remove event.
I: module.c: Unloading "module-intended-roles" (index: #13).
I: module.c: Unloaded "module-intended-roles" (index: #13).
D: core-subscribe.c: Dropped redundant event due to remove event.
I: module.c: Unloading "module-suspend-on-idle" (index: #14).
I: module.c: Unloaded "module-suspend-on-idle" (index: #14).
D: core-subscribe.c: Dropped redundant event due to remove event.
I: main.c: Daemon terminated.

---

### Post by alpharesearch on 2010-02-26
[Look Here!]("http://forums.gentoo.org/viewtopic-p-6177439.html?sid=fc23f7e21ca5e22a230f90d724fa51e9")

 fastest fix is to remove gdbm files from ${HOME}/.pulse

This worked for me...

Markus

---

