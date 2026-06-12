---
title: "Pulseaudio server won't start"
date: 2009-07-04
forum: Multimedia Software
---

### Post by Malcy on 2009-07-04
I have installed a fresh copy of 9.04 32 bit on my laptop (HP-Compaq 6820s) today. As usual, I followed the how to's in this forum to set up the sound properly but hit a brick wall when I found that Pulseaudio server wouldn't start. The sound card is an Analog Devices 1981.

Here is the verbose output from trying to start Pulseaudio server manually:

I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: main.c: We're in the group 'pulse-rt', allowing high-priority scheduling.
I: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
I: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
I: core-util.c: Successfully gained nice level -11.
I: main.c: Giving up CAP_NICE
I: main.c: This is PulseAudio 0.9.14
I: main.c: Page size is 4096 bytes
I: main.c: Machine ID is d00bea4331ee0fa76e94516f4a4f68af.
I: main.c: Using runtime directory /home/mb/.pulse/d00bea4331ee0fa76e94516f4a4f68af:runtime.
I: main.c: Using state directory /home/mb/.pulse.
I: main.c: Running in system mode: no
I: main.c: Fresh high-resolution timers available! Bon appetit!
I: sink.c: Created sink 0 "combined" with sample spec s16le 2ch 44100Hz and channel map front-left,front-right
I: source.c: Created source 0 "combined.monitor" with sample spec s16le 2ch 44100Hz and channel map front-left,front-right
I: module.c: Loaded "module-combine" (index: #0; argument: "").
I: module.c: Loaded "module-gconf" (index: #1; argument: "").
I: module.c: Loaded "module-suspend-on-idle" (index: #2; argument: "").
I: module-device-restore.c: Sucessfully opened database file '/home/mb/.pulse/d00bea4331ee0fa76e94516f4a4f68af:device-volumes.i486-pc-linux-gnu.gdbm'.
I: module.c: Loaded "module-device-restore" (index: #3; argument: "").
I: module-stream-restore.c: Sucessfully opened database file '/home/mb/.pulse/d00bea4331ee0fa76e94516f4a4f68af:stream-volumes.i486-pc-linux-gnu.gdbm'.
I: module.c: Loaded "module-stream-restore" (index: #4; argument: "").
I: (alsa-lib)pcm_params.c: Slave PCM not usable
I: (alsa-lib)pcm_params.c: Slave PCM not usable
I: (alsa-lib)pcm_params.c: Slave PCM not usable
E: alsa-util.c: [COLOR=Red]Failed to set hardware parameters on plug:equalized: No such file or directory[/COLOR]
E: module.c: [COLOR=Red]Failed to load  module "module-alsa-sink" (argument: "device=equalized"): initialization failed.[/COLOR]
E: main.c: [COLOR=Red]Module load failed.[/COLOR]
E: main.c: [COLOR=Red]Failed to initialize daemon.[/COLOR]
I: module.c: Unloading "module-combine" (index: #0).
I: sink.c: Freeing sink 0 "combined"
I: source.c: Freeing source 0 "combined.monitor"
I: module.c: Unloaded "module-combine" (index: #0).
I: module.c: Unloading "module-gconf" (index: #1).
I: module.c: Unloaded "module-gconf" (index: #1).
I: module.c: Unloading "module-suspend-on-idle" (index: #2).
I: module.c: Unloaded "module-suspend-on-idle" (index: #2).
I: module.c: Unloading "module-device-restore" (index: #3).
I: module.c: Unloaded "module-device-restore" (index: #3).
I: module.c: Unloading "module-stream-restore" (index: #4).
I: module.c: Unloaded "module-stream-restore" (index: #4).
I: main.c: Daemon terminated.

It looks like an Alsa issue but I don't know where to go from here. I have tried everything that I could find on the forum without success. Any ideas would be great.

---

### Post by rtalcott on 2009-07-04
E: module.c: Failed to load  module "module-alsa-sink" (argument: "device=hw:0,1"): initialization failed.
E: main.c: Module load failed.
E: main.c: Failed to initialize daemon.
[1]+  Exit 1                  pulseaudio

I need help too.

---

