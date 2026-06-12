---
title: "Ubuntu 9.10 sound popping"
date: 2009-11-13
forum: Multimedia Software
---

### Post by spearofsolomon on 2009-11-13
New install of Ubuntu 9.10 64bit.  Everything is working well except that sound is still "poppy" - it's subtle but very noticable when I'm wearing headphones.  In particular sound from within vmware pops and is also choppy.

I spent a couple hours reading about pulseaudio and (I think) getting real-time and high priority working.

Here is my sound hardware from lshw:

*-multimedia
             description: Audio device
             product: 82801H (ICH8 Family) HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=HDA Intel latency=0
             resources: irq:21 memory:f6ffc000-f6ffffff


Here is my daemon.conf and the output from the terminal when I run pulseaudio.  

```
cat /etc/pulse/daemon.conf
; daemonize = no
; fail = yes
; allow-module-loading = yes
; allow-exit = yes
; use-pid-file = yes
; system-instance = no
; enable-shm = yes
; shm-size-bytes = 0 # setting this 0 will use the system-default, usually 64 MiB
; lock-memory = no
; cpu-limit = no
cpu-limit = yes

 high-priority = yes
; high-priority = no
 nice-level = -11

 realtime-scheduling = yes
 realtime-priority = 5

; exit-idle-time = 20
; scache-idle-time = 20

; dl-search-path = (depends on architecture)

; load-default-script-file = yes
; default-script-file = 

; log-target = auto
; log-level = notice
; log-meta = no
; log-time = no
; log-backtrace = 0

resample-method = speex-float-1
; enable-remixing = yes
; enable-lfe-remixing = no

flat-volumes = no

; rlimit-fsize = -1
; rlimit-data = -1
; rlimit-stack = -1
; rlimit-core = -1
; rlimit-as = -1
; rlimit-rss = -1
; rlimit-nproc = -1
; rlimit-nofile = 256
; rlimit-memlock = -1
; rlimit-locks = -1
; rlimit-sigpending = -1
; rlimit-msgqueue = -1
; rlimit-nice = 31
; rlimit-rtprio = 9
; rlimit-rttime = 1000000

 default-sample-format = s16le
; default-sample-rate = 44100
 default-sample-channels = 2
default-sample-rate = 48000
; default-channel-map = front-left,front-right
``````
~$ pulseaudio -k
~$ pulseaudio -vvvvv
D: core-rtclock.c: Timer slack is set to 50 us.
D: core-util.c: setpriority() worked.
I: core-util.c: Successfully gained nice level -11.
I: main.c: This is PulseAudio 0.9.19
D: main.c: Compilation host: x86_64-pc-linux-gnu
D: main.c: Compilation CFLAGS: -g -O2 -g -Wall -O3 -Wall -W -Wextra -pipe -Wno-long-long -Winline -Wvla -Wno-overlength-strings -Wunsafe-loop-optimizations -Wundef -Wformat=2 -Wlogical-op -Wsign-compare -Wformat-security -Wmissing-include-dirs -Wformat-nonliteral -Wold-style-definition -Wpointer-arith -Winit-self -Wdeclaration-after-statement -Wfloat-equal -Wmissing-prototypes -Wstrict-prototypes -Wredundant-decls -Wmissing-declarations -Wmissing-noreturn -Wshadow -Wendif-labels -Wcast-align -Wstrict-aliasing=2 -Wwrite-strings -Wno-unused-parameter -ffast-math -Wp,-D_FORTIFY_SOURCE=2 -fno-common -fdiagnostics-show-option
D: main.c: Running on host: Linux x86_64 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:05:01 UTC 2009
D: main.c: Found 2 CPUs.
I: main.c: Page size is 4096 bytes
D: main.c: Compiled with Valgrind support: no
D: main.c: Running in valgrind mode: no
D: main.c: Optimized build: yes
D: main.c: All asserts enabled.
I: main.c: Machine ID is 41ccad37cbce08c75bedb3894af45934.
I: main.c: Session ID is 41ccad37cbce08c75bedb3894af45934-1258137456.625615-622878524.
I: main.c: Using runtime directory /home/nspears/.pulse/41ccad37cbce08c75bedb3894af45934-runtime.
I: main.c: Using state directory /home/nspears/.pulse.
I: main.c: Using modules directory /usr/lib/pulse-0.9.19/modules.
I: main.c: Running in system mode: no
E: pid.c: Daemon already running.
E: main.c: pa_pid_file_create() failed.
```
Suggestions appreciated!

---

### Post by markbuntu on 2009-11-13
You can try adding tsched=0 to the hal detect line in /etc/pulse/default.pa. You can also try adjusting the default fragments and default fragment size.

load-module module-hal-detect tsched=0

You can read about this bug at lauchpad here

[https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/301755](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/301755)

It is marked fix-committed

---

### Post by spearofsolomon on 2009-11-13
Thanks.  I don't have that line in my default.pa yet - where should I add it?

---

