---
title: "PulseAudio - messed up the working pulse and now after reistalling won't work"
date: 2011-10-24
forum: Multimedia Software
---

### Post by ales on 2011-10-24
Hello,

i messed up my Ubuntu 11.10. Just played a bit with sound system, because one game is not working with Pulse. After installing some alsa, oss libraries the sound stopped to work, I can see in Pulse only "Dummy output device". Tries to reinstall Pulseaudio completely, udes forums etc. but no sound at all. If anyone knows how to reinstall it let me know. This is what I get with pulseuadio -vvv. It seems as it is not detecting my sound card SB LIve. WOrked always fine till I didn't mess it up.

dreamwalker@dreamwalker-System-Product-Name:~$ **pulseaudio -vvv**
I: [pulseaudio] main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
I: [pulseaudio] main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
D: [pulseaudio] core-rtclock.c: Timer slack is set to 50 us.
D: [pulseaudio] core-util.c: RealtimeKit worked.
I: [pulseaudio] core-util.c: Successfully gained nice level -11.
I: [pulseaudio] main.c: This is PulseAudio 1.0
D: [pulseaudio] main.c: Compilation host: i686-pc-linux-gnu
D: [pulseaudio] main.c: Compilation CFLAGS: -g -O2 -g -O2 -Wall -W -Wextra -pipe -Wno-long-long -Wvla -Wno-overlength-strings -Wunsafe-loop-optimizations -Wundef -Wformat=2 -Wlogical-op -Wsign-compare -Wformat-security -Wmissing-include-dirs -Wformat-nonliteral -Wpointer-arith -Winit-self -Wdeclaration-after-statement -Wfloat-equal -Wmissing-prototypes -Wredundant-decls -Wmissing-declarations -Wmissing-noreturn -Wshadow -Wendif-labels -Wcast-align -Wstrict-aliasing -Wwrite-strings -Wno-unused-parameter -ffast-math -Wp,-D_FORTIFY_SOURCE=2 -fno-common -fdiagnostics-show-option
D: [pulseaudio] main.c: Running on host: Linux i686 3.0.0-12-generic #20-Ubuntu SMP Fri Oct 7 14:50:42 UTC 2011
D: [pulseaudio] main.c: Found 1 CPUs.
I: [pulseaudio] main.c: Page size is 4096 bytes
D: [pulseaudio] main.c: Compiled with Valgrind support: no
D: [pulseaudio] main.c: Running in valgrind mode: no
D: [pulseaudio] main.c: Running in VM: no
D: [pulseaudio] main.c: Optimized build: yes
D: [pulseaudio] main.c: All asserts enabled.
I: [pulseaudio] main.c: Machine ID is d38f526d5ca5d1acb18e462d00000008.
I: [pulseaudio] main.c: Session ID is d38f526d5ca5d1acb18e462d00000008-1319485686.511594-12224990.
I: [pulseaudio] main.c: Using runtime directory /home/dreamwalker/.pulse/d38f526d5ca5d1acb18e462d00000008-runtime.
I: [pulseaudio] main.c: Using state directory /home/dreamwalker/.pulse.
I: [pulseaudio] main.c: Using modules directory /usr/lib/pulse-1.0/modules.
I: [pulseaudio] main.c: Running in system mode: no
E: [pulseaudio] pid.c: Daemon already running.
E: [pulseaudio] main.c: pa_pid_file_create() failed.
dreamwalker@dreamwalker-System-Product-Name:~$


Solution
sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils

and then....

sudo apt-get install linux-sound-base alsa-base alsa-utils

---

