---
title: "Pulseaudio can not find module-jack-source"
date: 2009-06-06
forum: Multimedia Software
---

### Post by Weisswurst on 2009-06-06
Although I copied the modules to here:
/usr/lib/pulse-0.9/modules/module-jack-source.so and
/usr/lib/pulse-0.9/modules/module-jack-sink.so

I get following messages if I dare to start pulseaudio with the edited default.pa.

```

marco@marco-desktop:~$ pulseaudio -vv
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
D: main.c: Started as real root: no, suid root: yes
I: main.c: We're in the group 'pulse-rt', allowing high-priority scheduling.
I: main.c: RLIMIT_RTPRIO is set to 90, allowing real-time scheduling.
I: main.c: RLIMIT_NICE is set to 30, allowing high-priority scheduling.
I: main.c: setrlimit(RLIMIT_NICE, (31, 31)) fehlgeschlagen: Operation not permitted
I: core-util.c: Successfully gained nice level -11.
D: main.c: Can realtime: yes, can high-priority: yes
I: main.c: Giving up CAP_NICE
D: main.c: Can realtime: yes, can high-priority: yes
I: main.c: Dies ist PulseAudio 0.9.14
D: main.c: Compilation host: i486-pc-linux-gnu
D: main.c: Compilation CFLAGS: -g -O2 -g -Wall -O3 -Wall -W -Wextra -pedantic -pipe -Wno-long-long -Wvla -Wno-overlength-strings -Wconversion -Wundef -Wformat -Wlogical-op -Wpacked -Wformat-security -Wmissing-include-dirs -Wformat-nonliteral -Wold-style-definition -Wdeclaration-after-statement -Wfloat-equal -Wmissing-declarations -Wmissing-prototypes -Wstrict-prototypes -Wredundant-decls -Wmissing-noreturn -Wshadow -Wendif-labels -Wpointer-arith -Wcast-align -Wwrite-strings -Wno-unused-parameter -ffast-math
D: main.c: Running on host: Linux i686 2.6.29.4-rt16-all-nvk-060109-1 #1 SMP PREEMPT RT Mon Jun 1 08:12:13 CEST 2009
I: main.c: Seitengröße ist 4096 Bytes.
D: main.c: Compiled with Valgrind support: no
D: main.c: Running in valgrind mode: no
D: main.c: Optimized build: yes
I: main.c: System- ID ist c93a792ead3022c397bdc30045ccce03.
I: main.c: Using runtime directory /home/marco/.pulse/c93a792ead3022c397bdc30045ccce03:runtime.
I: main.c: Using state directory /home/marco/.pulse.
I: main.c: Running in system mode: no
I: main.c: Fresh high-resolution timers available! Bon appetit!
D: memblock.c: Using shared memory pool with 1024 slots of size 64,0 KiB each, total size is 64,0 MiB, maximum usable slot size is 65496
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9/modules/module-gconf.so': success
I: module.c: Loaded "module-gconf" (index: #0; argument: "").
I: module.c: Loaded "module-suspend-on-idle" (index: #1; argument: "").
I: module-device-restore.c: Sucessfully opened database file '/home/marco/.pulse/c93a792ead3022c397bdc30045ccce03:device-volumes.i486-pc-linux-gnu.gdbm'.
I: module.c: Loaded "module-device-restore" (index: #2; argument: "").
I: module-stream-restore.c: Sucessfully opened database file '/home/marco/.pulse/c93a792ead3022c397bdc30045ccce03:stream-volumes.i486-pc-linux-gnu.gdbm'.
I: module.c: Loaded "module-stream-restore" (index: #3; argument: "").
E: module.c: Failed to open module "module-jack-source": file not found
E: main.c: Module load failed.
E: main.c: Failed to initialize daemon.
I: module.c: Unloading "module-gconf" (index: #0).
I: module.c: Unloaded "module-gconf" (index: #0).
I: module.c: Unloading "module-suspend-on-idle" (index: #1).
I: module.c: Unloaded "module-suspend-on-idle" (index: #1).
I: module.c: Unloading "module-device-restore" (index: #2).
I: module.c: Unloaded "module-device-restore" (index: #2).
D: core-subscribe.c: Dropped redundant event due to remove event.
I: module.c: Unloading "module-stream-restore" (index: #3).
I: module.c: Unloaded "module-stream-restore" (index: #3).
D: core-subscribe.c: Dropped redundant event due to remove event.
I: main.c: Dämon beendet.
marco@marco-desktop:~$ 

```

Or in short:
```

marco@marco-desktop:~$ pulseaudio
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
E: module.c: Failed to open module "module-jack-source": file not found
E: main.c: Module load failed.
E: main.c: Failed to initialize daemon.

```

The Jack modules in /usr/lib/pulse-0.9/modules/ have the same access rights like the other modules. 
I'm running Jaunty now. Before I updated yesterday I was running Intrepid on an old Hardy realtime kernel. There the Jack modules worked. Instable but they worked... Now I can't even load them.
Any ideas?

---

