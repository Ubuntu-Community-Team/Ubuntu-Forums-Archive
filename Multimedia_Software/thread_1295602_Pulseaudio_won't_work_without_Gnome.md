---
title: "Pulseaudio won't work without Gnome"
date: 2009-10-19
forum: Multimedia Software
---

### Post by fungiside on 2009-10-19
Hi guys,

I've been trying to get pulseaudio working without my gnome desktop but with little success.

If I just boot and then ssh in (the desktop is sitting at gdm):

```

fungi@ren:~$ aplay -l
aplay: device_list:217: no soundcards found...

```

But after I log in to gnome:

```

fungi@ren:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: CMI8788 [C-Media CMI8788], device 0: Multichannel [Multichannel]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 1: CMI8788 [C-Media CMI8788], device 1: Digital [Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

Also strange, starting pulseaudio manually seems to do nothing:
```

fungi@ren:~$ pulseaudio -vv -D
D: main.c: Started as real root: no, suid root: yes
I: main.c: We're in the group 'pulse-rt', allowing high-priority scheduling.
I: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
I: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
I: core-util.c: Successfully gained nice level -11.
D: main.c: Can realtime: yes, can high-priority: yes
I: main.c: Giving up CAP_NICE
D: main.c: Can realtime: no, can high-priority: no
I: main.c: Daemon startup successful.

fungi@ren:~$ aplay -l
aplay: device_list:217: no soundcards found...


```


If I start with --v

```

fungi@ren:~$ pulseaudio -vv
D: main.c: Started as real root: no, suid root: yes
I: main.c: We're in the group 'pulse-rt', allowing high-priority scheduling.
I: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
I: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
I: core-util.c: Successfully gained nice level -11.
D: main.c: Can realtime: yes, can high-priority: yes
I: main.c: Giving up CAP_NICE
D: main.c: Can realtime: no, can high-priority: no
I: main.c: This is PulseAudio 0.9.15
D: main.c: Compilation host: i486-pc-linux-gnu
D: main.c: Compilation CFLAGS: -g -O2 -g -Wall -O3 -Wall -W -Wextra -pipe -Wno-long-long -Winline -Wvla -Wno-overlength-strings -Wunsafe-loop-optimizations -Wundef -Wformat=2 -Wlogical-op -Wsign-compare -Wformat-security -Wmissing-include-dirs -Wformat-nonliteral -Wold-style-definition -Wpointer-arith -Winit-self -Wdeclaration-after-statement -Wfloat-equal -Wmissing-prototypes -Wstrict-prototypes -Wredundant-decls -Wmissing-declarations -Wmissing-noreturn -Wshadow -Wendif-labels -Wcast-align -Wstrict-aliasing=2 -Wwrite-strings -Wno-unused-parameter -ffast-math -Wp,-D_FORTIFY_SOURCE=2 -fno-common -fdiagnostics-show-option
D: main.c: Running on host: Linux i686 2.6.28-15-generic #52-Ubuntu SMP Wed Sep 9 10:49:34 UTC 2009
D: main.c: Found 1 CPUs.
I: main.c: Page size is 4096 bytes
D: main.c: Compiled with Valgrind support: no
D: main.c: Running in valgrind mode: no
D: main.c: Optimized build: yes
D: main.c: All asserts enabled.
I: main.c: Machine ID is c175c33c6ee5c964d4d8e84b4a8f1cab.
I: main.c: Session ID is c175c33c6ee5c964d4d8e84b4a8f1cab-1255993290.807568-1833262847.
I: main.c: Using runtime directory /home/fungi/.pulse/c175c33c6ee5c964d4d8e84b4a8f1cab:runtime.
I: main.c: Using state directory /home/fungi/.pulse.
I: main.c: Running in system mode: no
I: main.c: Fresh high-resolution timers available! Bon appetit!
D: rtclock.c: Timer slack is set to 50 us.
D: memblock.c: Using shared memory pool with 1024 slots of size 64.0 KiB each, total size is 64.0 MiB, maximum usable slot size is 65496
I: module.c: Loaded "module-suspend-on-idle" (index: #0; argument: "").
I: module-device-restore.c: Sucessfully opened database file '/home/fungi/.pulse/c175c33c6ee5c964d4d8e84b4a8f1cab:device-volumes.i486-pc-linux-gnu.gdbm'.
I: module.c: Loaded "module-device-restore" (index: #1; argument: "").
I: module-stream-restore.c: Sucessfully opened database file '/home/fungi/.pulse/c175c33c6ee5c964d4d8e84b4a8f1cab:stream-volumes.i486-pc-linux-gnu.gdbm'.
I: module.c: Loaded "module-stream-restore" (index: #2; argument: "").
I: module-card-restore.c: Sucessfully opened database file '/home/fungi/.pulse/c175c33c6ee5c964d4d8e84b4a8f1cab:card-database.i486-pc-linux-gnu.gdbm'.
I: module.c: Loaded "module-card-restore" (index: #3; argument: "").
I: module.c: Loaded "module-augment-properties" (index: #4; argument: "").
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9.15/modules/module-hal-detect.so': success
D: dbus-util.c: Successfully connected to D-Bus system bus 4cee9ce6de24e5be0579d3144adce563 as :1.40
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/computer_alsa_timer
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/computer_alsa_sequencer
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_13f6_8788_sound_card_0_alsa_playback_1
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_13f6_8788_sound_card_0_alsa_capture_1
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_13f6_8788_sound_card_0_alsa_playback_0
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_13f6_8788_sound_card_0_alsa_capture_0
D: module-hal-detect.c: Loading module-alsa-card with arguments 'device_id=1 name=pci_13f6_8788_sound_card_0 card_name=alsa_card.pci_13f6_8788_sound_card_0 tsched=0'
E: module-alsa-card.c: Card '1' doesn't exist: No such file or directory
E: module.c: Failed to load  module "module-alsa-card" (argument: "device_id=1 name=pci_13f6_8788_sound_card_0 card_name=alsa_card.pci_13f6_8788_sound_card_0 tsched=0"): initialization failed.
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_13f6_8788_sound_card_0_alsa_control__1
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_1002_aa38_sound_card_0_alsa_playback_3
D: module-hal-detect.c: Loading module-alsa-card with arguments 'device_id=0 name=pci_1002_aa38_sound_card_0 card_name=alsa_card.pci_1002_aa38_sound_card_0 tsched=0'
E: module-alsa-card.c: Card '0' doesn't exist: No such file or directory
E: module.c: Failed to load  module "module-alsa-card" (argument: "device_id=0 name=pci_1002_aa38_sound_card_0 card_name=alsa_card.pci_1002_aa38_sound_card_0 tsched=0"): initialization failed.
D: module-hal-detect.c: Not loaded device /org/freedesktop/Hal/devices/pci_1002_aa38_sound_card_0_alsa_control__1
I: module-hal-detect.c: Loaded 0 modules.
I: module.c: Loaded "module-hal-detect" (index: #5; argument: "tsched=0").
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9.15/modules/module-bluetooth-discover.so': failure
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9.15/modules/module-esound-protocol-unix.so': success
I: module.c: Loaded "module-esound-protocol-unix" (index: #6; argument: "").
I: module.c: Loaded "module-native-protocol-unix" (index: #7; argument: "").
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9.15/modules/module-gconf.so': success
I: module.c: Loaded "module-gconf" (index: #8; argument: "").
I: module-default-device-restore.c: Saved default sink 'alsa_output.pci_13f6_8788_sound_card_0_alsa_playback_0' not existant, not restoring default sink setting.
I: module-default-device-restore.c: Saved default source 'alsa_input.pci_13f6_8788_sound_card_0_alsa_capture_0' not existant, not restoring default source setting.
I: module.c: Loaded "module-default-device-restore" (index: #9; argument: "").
I: module.c: Loaded "module-rescue-streams" (index: #10; argument: "").
D: module-always-sink.c: Autoloading null-sink as no other sinks detected.
I: module-device-restore.c: Restoring volume for sink auto_null.
I: module-device-restore.c: Restoring mute state for sink auto_null.
I: sink.c: Created sink 0 "auto_null" with sample spec s16le 6ch 44100Hz and channel map front-left,rear-left,front-center,front-right,rear-right,lfe
I: sink.c:     device.description = "Null Output"
I: sink.c:     device.class = "abstract"
I: sink.c:     device.icon_name = "audio-card"
I: module-device-restore.c: Restoring volume for source auto_null.monitor.
I: module-device-restore.c: Restoring mute state for source auto_null.monitor.
I: source.c: Created source 0 "auto_null.monitor" with sample spec s16le 6ch 44100Hz and channel map front-left,rear-left,front-center,front-right,rear-right,lfe
I: source.c:     device.description = "Monitor of Null Output"
I: source.c:     device.class = "monitor"
I: source.c:     device.icon_name = "audio-input-microphone"
D: module-null-sink.c: Thread starting up
D: rtpoll.c: Acquired POSIX realtime signal SIGRTMIN+29
D: module-suspend-on-idle.c: Sink auto_null becomes idle.
I: module.c: Loaded "module-null-sink" (index: #11; argument: "sink_name=auto_null").
I: module.c: Loaded "module-always-sink" (index: #12; argument: "").
I: client.c: Created 0 "ConsoleKit Session /org/freedesktop/ConsoleKit/Session10"
D: module-console-kit.c: Added new session /org/freedesktop/ConsoleKit/Session10
I: module.c: Loaded "module-console-kit" (index: #13; argument: "").
I: module.c: Loaded "module-position-event-sounds" (index: #14; argument: "").
I: module.c: Loaded "module-cork-music-on-phone" (index: #15; argument: "").
W: main.c: Unable to contact D-Bus: org.freedesktop.DBus.Error.Spawn.ExecFailed: dbus-launch failed to autolaunch D-Bus session: Autolaunch error: X11 initialization failed.
I: main.c: Daemon startup complete.
D: module-hal-detect.c: dbus: interface=org.freedesktop.DBus, path=/org/freedesktop/DBus, member=NameAcquired
D: module-console-kit.c: dbus: interface=org.freedesktop.DBus, path=/org/freedesktop/DBus, member=NameAcquired

```

What do I need to do to make pulseaudio initialize fully at system startup time?

Edit: This is with 9.04

---

### Post by markbuntu on 2009-10-20
Looks like alsa is not starting until after you log in, or maybe hal which pulse uses to find the alsa modules. It probably starts in the post gdm scripts or the x-server startup scripts which you have bypassed.

You can run bootchart to find out what starts when and Boot Up Manager (bum) to set what you want to start at boot.

---

### Post by fungiside on 2009-10-28
Well, it looks like pulseaudio isn't starting at all.  Alsa-utils is being called though.  Also, I didn't see any mention of pulseaudio in GUM, which may be part of the problem.

My boot order with gdm autologging in to xbmc is attached.

Edit: I also attached a screen shot of my Gnome sound settings.

Edit again: This is strange, my soundcard shows up in alsamixer but not in aplay -l.

---

### Post by fungiside on 2009-10-28
I've got it all worked out now! 

I tried way too many to list but the final two pieces of the puzzle were adding snd-oxygen to my modules.conf and then setting that card to be my default.  My video card also does audio output for hdmi and alsa was using it instead.

Thanks for the help!

---

