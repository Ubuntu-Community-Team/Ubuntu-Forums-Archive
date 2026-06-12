---
title: "PulseAudio has me stumped"
date: 2008-10-23
forum: Multimedia Software
---

### Post by eriqjaffe on 2008-10-23
I've been fighting this off and on for weeks now - I simply can not get the Pulseaudio daemon to start.

I'm in the pulse, pulse-access and pulse-rt groups, I've configured the /etc/asound.conf, but I just can't start the daemon:

```
E: main.c: daemon startup failed.
```

I found a doc on the Arch wiki saying to comment out a ".fail" line in /etc/pulse/default.pa, but there are several .fail lines and I'm not sure which one I'm failing on.

If it'll help any, here's the output of lspci:

```
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:01.0 PCI bridge: Intel Corporation 82865G/PE/P PCI to AGP Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation NV35 [GeForce FX 5900XT] (rev a1)
02:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:09.0 RAID bus controller: Silicon Image, Inc. PCI0680 Ultra ATA-133 Host Controller (rev 02)
02:0a.0 USB Controller: NEC Corporation USB (rev 43)
02:0a.1 USB Controller: NEC Corporation USB (rev 43)
02:0a.2 USB Controller: NEC Corporation USB 2.0 (rev 04)
```

...so that's onboard Intel audio.  It works fine with the OSS driver, but I can only listen to one audio source at a time.  Running pulseaudio -vvv gets me:

```
I: main.c: We're in the group 'pulse-rt', allowing real-time and high-priority scheduling.
I: core-util.c: Successfully gained nice level -11.
I: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
I: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
I: main.c: This is PulseAudio 0.9.10
I: main.c: Page size is 4096 bytes
I: main.c: Fresh high-resolution timers available! Bon appetit!
I: module-alsa-sink.c: Successfully opened device front:ICH5.
I: module-alsa-sink.c: Successfully enabled mmap() mode.
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL front:ICH5
I: alsa-util.c: Unable to attach to mixer front:ICH5: No such file or directory
I: alsa-util.c: Unable to attach to mixer hw:(null): No such device
I: sink.c: Created sink 0 "ICH5" with sample spec "s16le 2ch 44100Hz"
I: source.c: Created source 0 "ICH5.monitor" with sample spec "s16le 2ch 44100Hz"
I: module-alsa-sink.c: Using 4 fragments of size 4408 bytes.
D: module-alsa-sink.c: Thread starting up
D: rtpoll.c: Acquired POSIX realtime signal SIGRTMIN+29
I: module-alsa-sink.c: Starting playback.
I: module.c: Loaded "module-alsa-sink" (index: #0; argument: "device=front:ICH5 sink_name=ICH5").
I: module-alsa-source.c: Successfully opened device hw:ICH5.
I: module-alsa-source.c: Successfully enabled mmap() mode.
I: alsa-util.c: Successfully attached to mixer 'hw:ICH5'
I: alsa-util.c: Using mixer control "Capture".
I: source.c: Created source 1 "alsa_input.hw_ICH5" with sample spec "s16le 2ch 44100Hz"
I: module-alsa-source.c: Using 4 fragments of size 4408 bytes.
I: alsa-util.c: All 2 channels can be mapped to mixer channels. Using hardware volume control.
D: module-alsa-source.c: Thread starting up
D: rtpoll.c: Acquired POSIX realtime signal SIGRTMIN+28
I: module.c: Loaded "module-alsa-source" (index: #1; argument: "device=hw:ICH5").
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9/modules/module-hal-detect.so': success
D: cli-command.c: Checking for existance of '/usr/lib/pulse-0.9/modules/module-esound-protocol-unix.so': success
E: authkey.c: Failed to open cookie file '/home/eriq/.esd_auth': Permission denied
E: authkey.c: Failed to load authorization key '/home/eriq/.esd_auth': Permission denied
E: module.c: Failed to load  module "module-esound-protocol-unix" (argument: ""): initialization failed.
E: main.c: Module load failed.
E: main.c: Failed to initialize daemon.
I: module.c: Unloading "module-alsa-sink" (index: #0).
D: module-alsa-sink.c: Thread shutting down
I: sink.c: Freeing sink 0 "ICH5"
I: source.c: Freeing source 0 "ICH5.monitor"
I: module.c: Unloaded "module-alsa-sink" (index: #0).
I: module.c: Unloading "module-alsa-source" (index: #1).
D: module-alsa-source.c: Thread shutting down
I: source.c: Freeing source 1 "alsa_input.hw_ICH5"
I: module.c: Unloaded "module-alsa-source" (index: #1).
I: main.c: Daemon terminated.

```

...so I kinda see where the problem is, but I have no clue how to go about fixing it.  Any tips would be appreciated.

Thanks!

---

### Post by kostkon on 2008-10-24
So, the problem seems to be here
```
E: authkey.c: Failed to open cookie file '/home/eriq/.esd_auth': Permission denied
E: authkey.c: Failed to load authorization key '/home/eriq/.esd_auth': Permission denied
E: module.c: Failed to load  module "module-esound-protocol-unix" (argument: ""): initialization failed.
E: main.c: Module load failed.
E: main.c: Failed to initialize daemon.
```
Find this file, it is in your home folder and check its permission. Mine belongs to me and I have read/write access. If yours belongs to *root*, then you could try to delete it and I suppose it will be recreated with the right permissions (keep a copy of it, of course, just in case).

You could also try to change its permissions directly, without deleting it.

---

### Post by eriqjaffe on 2008-10-24
Well, I'll be darned, I thought I had checked the permissions on that before, but apparently I hadn't.

That sorted it out, thanks!

:woohoo:

---

