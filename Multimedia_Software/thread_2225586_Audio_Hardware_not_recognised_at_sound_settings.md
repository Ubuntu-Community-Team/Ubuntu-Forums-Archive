---
title: "Audio Hardware not recognised at sound settings"
date: 2014-05-22
forum: Multimedia Software
---

### Post by gcanada on 2014-05-22
Hello,
First of all, i am very noob at Linux. Some days ago, my Ubuntu 12.04 stopped recognising the audio device. ( Maybe after a change anywhere, i dont remember exactly)

the alsa log is this:
[http://www.alsa-project.org/db/?f=1bb1ea38bdff330ea25bdc5a4712e451beed4d88](http://www.alsa-project.org/db/?f=1bb1ea38bdff330ea25bdc5a4712e451beed4d88)

When i go into audio/sound settings i dont see any "hardware" option, and the input and output ones are totally empty.

---

### Post by Yellow Pasque on 2014-05-22
```
Pulseaudio:
      Installed - Yes (/usr/bin/pulseaudio)
      Running - No
```

Pulseaudio's not running. First, try resetting config:
```
rm -r ~/.pulse*
```
Log out and back in. If that didn't work, make a verbose log: [https://wiki.ubuntu.com/PulseAudio/Log](https://wiki.ubuntu.com/PulseAudio/Log)

---

### Post by gcanada on 2014-05-23
EDIT 1:  PROBLEM 2: now i have my pulseaudio running, but only detecting a dummy output, so i have no sound anyway, trying to find he solution :(

EDIT 2: SOLUTION OF PROBLEM 2:  [http://www.ubuntu-es.org/node/147246#.U380OnJ5OPK](http://www.ubuntu-es.org/node/147246#.U380OnJ5OPK)   ( SPOILER: spanish). Just to make a resume:
sudo apt-get purge linux-sound-base alsa-base alsa-utils
sudo apt-get install linux-sound-base alsa-base alsa-utils


EDIT 1: SOLUTION OF ORIGINAL PROBLEM : The solution of the problem below was that the daemon wasnt working properly. 
[http://hwswbits.blogspot.com.es/2013/03/picuntu-09-rc3-crash-in-xfce-dbus.html](http://hwswbits.blogspot.com.es/2013/03/picuntu-09-rc3-crash-in-xfce-dbus.html)


ORIGINAL PROBLEM :This happens when i try to start the pulseaudio:

gcanada@gcanada:~$ pulseaudio --start
E: [pulseaudio] main.c: Falló el inicio del demonio.
gcanada@gcanada:~$ pulseaudio
E: [pulseaudio] module-console-kit.c: GetSessionsForUnixUser() call failed: org.freedesktop.DBus.Error.Spawn.ExecFailed: Failed to execute program /usr/lib/dbus-1.0/dbus-daemon-launch-helper: Success
E: [pulseaudio] module.c: Failed to load module "module-console-kit" (argument: ""): initialization failed.
E: [pulseaudio] main.c: Module load failed.
E: [pulseaudio] main.c: Fallo al intentar iniciar el demonio.

So i think the problem is at modulekit and dbus:

gcanada@gcanada:~$ /etc/init.d/dbus status
bash: /etc/init.d/dbus: No existe el archivo o el directorio
gcanada@gcanada:~$ /etc/init.d/consolekit status
bash: /etc/init.d/consolekit: No existe el archivo o el directorio

consolekit dont exists at init.d . Dbus exists but it is not recognised.

And the pulseverbose.log is the following:

(   0.000|   0.000) I: [pulseaudio] main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
(   0.000|   0.000) I: [pulseaudio] main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
(   0.000|   0.000) D: [pulseaudio] core-rtclock.c: Timer slack is set to 50 us.
(   0.015|   0.014) I: [pulseaudio] core-util.c: Failed to acquire high-priority scheduling: Input/output error
(   0.015|   0.000) I: [pulseaudio] main.c: This is PulseAudio 1.1
(   0.015|   0.000) D: [pulseaudio] main.c: Compilation host: x86_64-pc-linux-gnu
(   0.015|   0.000) D: [pulseaudio] main.c: Compilation CFLAGS: -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -Werror=format-security -Wall -W -Wextra -pipe -Wno-long-long -Wvla -Wno-overlength-strings -Wunsafe-loop-optimizations -Wundef -Wformat=2 -Wlogical-op -Wsign-compare -Wmissing-include-dirs -Wformat-nonliteral -Wpointer-arith -Winit-self -Wdeclaration-after-statement -Wfloat-equal -Wmissing-prototypes -Wredundant-decls -Wmissing-declarations -Wmissing-noreturn -Wshadow -Wendif-labels -Wcast-align -Wstrict-aliasing -Wwrite-strings -Wno-unused-parameter -ffast-math -Wp,-D_FORTIFY_SOURCE=2 -fno-common -fdiagnostics-show-option
(   0.015|   0.000) D: [pulseaudio] main.c: Running on host: Linux x86_64 3.11.0-17-generic #31~precise1-Ubuntu SMP Tue Feb 4 21:25:43 UTC 2014
(   0.015|   0.000) D: [pulseaudio] main.c: Found 4 CPUs.
(   0.015|   0.000) I: [pulseaudio] main.c: Page size is 4096 bytes
(   0.015|   0.000) D: [pulseaudio] main.c: Compiled with Valgrind support: no
(   0.015|   0.000) D: [pulseaudio] main.c: Running in valgrind mode: no
(   0.015|   0.000) D: [pulseaudio] main.c: Running in VM: no
(   0.015|   0.000) D: [pulseaudio] main.c: Optimized build: yes
(   0.015|   0.000) D: [pulseaudio] main.c: All asserts enabled.
(   0.015|   0.000) I: [pulseaudio] main.c: Machine ID is 67e6f46331d5a5b20798ea660000000b.
(   0.015|   0.000) I: [pulseaudio] main.c: Using runtime directory /home/gcanada/.pulse/67e6f46331d5a5b20798ea660000000b-runtime.
(   0.015|   0.000) I: [pulseaudio] main.c: Using state directory /home/gcanada/.pulse.
(   0.015|   0.000) I: [pulseaudio] main.c: Using modules directory /usr/lib/pulse-1.1/modules.
(   0.015|   0.000) I: [pulseaudio] main.c: Running in system mode: no
(   0.015|   0.000) I: [pulseaudio] main.c: Fresh high-resolution timers available! Bon appetit!
(   0.015|   0.000) D: [pulseaudio] memblock.c: Using shared memory pool with 1024 slots of size 64.0 KiB each, total size is 64.0 MiB, maximum usable slot size is 65472
(   0.016|   0.000) I: [pulseaudio] cpu-x86.c: CPU flags: CMOV MMX SSE SSE2 SSE3 SSSE3 SSE4_1 SSE4_2 
(   0.016|   0.000) I: [pulseaudio] svolume_mmx.c: Initialising MMX optimized volume functions.
(   0.016|   0.000) I: [pulseaudio] remap_mmx.c: Initialising MMX optimized remappers.
(   0.016|   0.000) I: [pulseaudio] svolume_sse.c: Initialising SSE2 optimized volume functions.
(   0.016|   0.000) I: [pulseaudio] remap_sse.c: Initialising SSE2 optimized remappers.
(   0.016|   0.000) I: [pulseaudio] sconv_sse.c: Initialising SSE2 optimized conversions.
(   0.016|   0.000) I: [pulseaudio] svolume_orc.c: Initialising ORC optimized volume functions.
(   0.016|   0.000) D: [pulseaudio] cli-command.c: Checking for existence of '/usr/lib/pulse-1.1/modules/module-udev-detect.so': success
(   0.016|   0.000) D: [pulseaudio] cli-command.c: Checking for existence of '/usr/lib/pulse-1.1/modules/module-jackdbus-detect.so': failure
(   0.016|   0.000) D: [pulseaudio] cli-command.c: Checking for existence of '/usr/lib/pulse-1.1/modules/module-bluetooth-discover.so': failure
(   0.016|   0.000) D: [pulseaudio] cli-command.c: Checking for existence of '/usr/lib/pulse-1.1/modules/module-esound-protocol-unix.so': failure
(   0.016|   0.000) D: [pulseaudio] cli-command.c: Checking for existence of '/usr/lib/pulse-1.1/modules/module-gconf.so': failure
(   0.016|   0.000) D: [pulseaudio] cli-command.c: Checking for existence of '/usr/lib/pulse-1.1/modules/module-console-kit.so': success
(   0.016|   0.000) E: [pulseaudio] main.c: Daemon startup without any loaded modules, refusing to work.
(   0.016|   0.000) I: [pulseaudio] main.c: Daemon terminated.

---

### Post by Yellow Pasque on 2014-05-23
^That's very confusing. Are you still experiencing the problem or not?

---

