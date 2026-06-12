---
title: "Sound stopped working after using HDMI"
date: 2013-03-30
forum: Multimedia Software
---

### Post by Kreuger on 2013-03-30
So a couple of days ago, I had my laptop hooked up to my tv via HDMI. I used pavucontrol to disable sound on my laptop and play it through the tv. I changed it back when I was done. Can't remember if I used it right away. Last night I tried to use it and it didn't work. I opened pavucontrol again and switched to the configuration tab where there had previously been a drop down menu allowing me to choose what device to output my sound through. Now there's nothing. It says no card available for configuration. When I open asoundconf-gtk it only has "PCH" and selecting that does nothing either. I tried making sure pulseaudio was running.

> kreuger@Kreuger-Lenovo-B570:~$ pulseaudio -D
E: [pulseaudio] main.c: Daemon startup failed.
kreuger@Kreuger-Lenovo-B570:~$ pulseaudio --log-level=4 --log-target=stderr
I: [pulseaudio] main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
I: [pulseaudio] main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
D: [pulseaudio] core-rtclock.c: Timer slack is set to 50 us.
D: [pulseaudio] core-util.c: RealtimeKit worked.
I: [pulseaudio] core-util.c: Successfully gained nice level -11.
I: [pulseaudio] main.c: This is PulseAudio 2.1
D: [pulseaudio] main.c: Compilation host: i686-pc-linux-gnu
D: [pulseaudio] main.c: Compilation CFLAGS: -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Werror=format-security -Wall -W -Wextra -pipe -Wno-long-long -Wvla -Wno-overlength-strings -Wunsafe-loop-optimizations -Wundef -Wformat=2 -Wlogical-op -Wsign-compare -Wformat-security -Wmissing-include-dirs -Wformat-nonliteral -Wpointer-arith -Winit-self -Wdeclaration-after-statement -Wfloat-equal -Wmissing-prototypes -Wredundant-decls -Wmissing-declarations -Wmissing-noreturn -Wshadow -Wendif-labels -Wcast-align -Wstrict-aliasing -Wwrite-strings -Wno-unused-parameter -ffast-math -Wp,-D_FORTIFY_SOURCE=2 -fno-common -fdiagnostics-show-option
D: [pulseaudio] main.c: Running on host: Linux i686 3.5.0-24-generic #37-Ubuntu SMP Thu Feb 7 05:32:22 UTC 2013
D: [pulseaudio] main.c: Found 4 CPUs.
I: [pulseaudio] main.c: Page size is 4096 bytes
D: [pulseaudio] main.c: Compiled with Valgrind support: no
D: [pulseaudio] main.c: Running in Valgrind mode: no
D: [pulseaudio] main.c: Running in VM: no
D: [pulseaudio] main.c: Optimized build: yes
D: [pulseaudio] main.c: FASTPATH defined, only fast path asserts disabled.
I: [pulseaudio] main.c: Machine ID is dede8c4d051e0d61ea80ff9f00000007.
I: [pulseaudio] main.c: Session ID is dede8c4d051e0d61ea80ff9f00000007-1364227283.451700-911705375.
I: [pulseaudio] main.c: Using runtime directory /home/kreuger/.pulse/dede8c4d051e0d61ea80ff9f00000007-runtime.
I: [pulseaudio] main.c: Using state directory /home/kreuger/.pulse.
I: [pulseaudio] main.c: Using modules directory /usr/lib/pulse-2.1/modules.
I: [pulseaudio] main.c: Running in system mode: no
E: [pulseaudio] pid.c: Daemon already running.
E: [pulseaudio] main.c: pa_pid_file_create() failed.

---

### Post by Kreuger on 2013-03-31
Anyone?

---

### Post by Kreuger on 2013-04-01
Someone please help!...

---

### Post by Kreuger on 2013-04-03
Tired of having to boot into Windows to watch something on youtube. :(

---

### Post by Kreuger on 2013-04-04
Using [this guide]("https://wiki.ubuntu.com/PulseAudio/Log"), I've made an output [log]("http://pastebin.com/rmARXUMD") of trying to use pavucontrol to get sound. Maybe someone can find an issue there?

---

### Post by Kreuger on 2013-04-10
Help me!

---

### Post by Kreuger on 2013-07-09
Still having this issue...

---

