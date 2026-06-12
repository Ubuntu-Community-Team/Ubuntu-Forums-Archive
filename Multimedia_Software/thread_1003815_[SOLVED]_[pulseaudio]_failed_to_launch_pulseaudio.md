---
title: "[SOLVED] [pulseaudio] failed to launch pulseaudio"
date: 2008-12-06
forum: Multimedia Software
---

### Post by kakyoism on 2008-12-06
Below is the verbose output of launching pulseaudio.
I followed this link to try to fix things but it didn't help.

me@my-laptop:~/Desktop$ pulseaudio -vv
```
I: main.c: We're in the group 'pulse-rt', allowing real-time and high-priority scheduling.
I: core-util.c: Successfully gained nice level -11.
W: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
W: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
I: main.c: This is PulseAudio 0.9.10
I: main.c: Page size is 4096 bytes
I: main.c: Fresh high-resolution timers available! Bon appetit!
E: alsa-util.c: Error opening PCM device hw:0,2: No such file or directory
E: module.c: Failed to load  module "module-alsa-sink" (argument: "device=hw:0,2"): initialization failed.
E: main.c: Module load failed.
E: main.c: Failed to initialize daemon.
I: main.c: Daemon terminated.
```

---

### Post by kakyoism on 2008-12-06
Solved it myself.
I shouldn't have followed some instructions to change the two lines in 
/etc/pulse/default.pa, about load sink and source.

Previously I specified hw:0, 1 to the sink and source but one of them is a USB card which is not connected at the moment.
Problem is I also specified in the system->preference->sound that all major tasks use "Autodetect", which I think links to the module hal-detect.


The two lines should remain like this:
```
load-module module-alsa-sink
load-module module-alsa-source
```

---

