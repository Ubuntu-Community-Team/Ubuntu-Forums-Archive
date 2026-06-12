---
title: "EVGA 790i / 2xEVGA GTX 260 SLI - no audio or hardware gfx"
date: 2009-02-08
forum: Multimedia Software
---

### Post by kurakin on 2009-02-08
Ubuntu 8.10 installs fine, and gives me full resolution. It appears to detect the sound card properly, but it doesn't work. As soon as I install the nvidia hardware graphics drivers I get the kinit unable to resume from image or whatever error. Looked around and tried a bunch of things to resolve that but the only thing that works is to uninstall the hardware drivers and restore the old xorg.conf, but then I'm in 800x600 failsafe resolution. I've tried using the pre-packaged nvidia 177, also tried from source with 177.68 (suggested on forums), 180.22 (suggested by nvidia), and 180.27 (latest at time of writing), none worked.

The hardware:

[http://www.newegg.com/Product/Product.aspx?Item=N82E16813188031](http://www.newegg.com/Product/Product.aspx?Item=N82E16813188031)
[http://www.newegg.com/Product/Product.aspx?Item=N82E16814130370](http://www.newegg.com/Product/Product.aspx?Item=N82E16814130370)

From lspci -nvv
```

00:0f.1 Audio device [0403]: nVidia Corporation MCP55 High Definition Audio [10de:0371] (rev a2)
	Subsystem: eVga.com. Corp. Device [3842:1004]
	Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 23
	Memory at cfff0000 (32-bit, non-prefetchable) [size=16K]
	Capabilities: [44] Power Management version 2
	Capabilities: [50] Message Signalled Interrupts: Mask+ 64bit+ Queue=0/0 Enable-
	Capabilities: [6c] HyperTransport: MSI Mapping Enable- Fixed+
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel

01:00.0 VGA compatible controller [0300]: nVidia Corporation Device [10de:05e2] (rev a1)
	Subsystem: eVga.com. Corp. Device [3842:1265]
	Flags: bus master, fast devsel, latency 0, IRQ 11
	Memory at cc000000 (32-bit, non-prefetchable) [size=16M]
	Memory at b0000000 (64-bit, prefetchable) [size=256M]
	Memory at ca000000 (64-bit, non-prefetchable) [size=32M]
	I/O ports at 9c00 [size=128]
	[virtual] Expansion ROM at cd000000 [disabled] [size=512K]
	Capabilities: [60] Power Management version 3
	Capabilities: [68] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Capabilities: [78] Express Endpoint, MSI 00
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [128] Power Budgeting <?>
	Capabilities: [600] Vendor Specific Information <?>
	Kernel modules: nvidiafb

02:00.0 VGA compatible controller [0300]: nVidia Corporation Device [10de:05e2] (rev a1)
	Subsystem: eVga.com. Corp. Device [3842:1265]
	Flags: fast devsel, IRQ 10
	Memory at c8000000 (32-bit, non-prefetchable) [disabled] [size=16M]
	Memory at a0000000 (64-bit, prefetchable) [disabled] [size=256M]
	Memory at c6000000 (64-bit, non-prefetchable) [disabled] [size=32M]
	I/O ports at 8c00 [disabled] [size=128]
	[virtual] Expansion ROM at c9000000 [disabled] [size=512K]
	Capabilities: [60] Power Management version 3
	Capabilities: [68] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Capabilities: [78] Express Endpoint, MSI 00
	Capabilities: [100] Virtual Channel <?>
	Capabilities: [128] Power Budgeting <?>
	Capabilities: [600] Vendor Specific Information <?>
	Kernel modules: nvidiafb

```

from syslog:
```

Feb  8 09:34:08 bear pulseaudio[8453]: ltdl-bind-now.c: Failed to find original dlopen loader.
Feb  8 09:34:08 bear pulseaudio[8455]: pid.c: Stale PID file, overwriting.
Feb  8 09:34:08 bear pulseaudio[8455]: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
Feb  8 09:34:08 bear pulseaudio[8455]: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
Feb  8 09:34:19 bear x-session-manager[8364]: WARNING: Application 'libcanberra-login-sound.desktop' failed to register before timeout 
Feb  8 09:34:19 bear pulseaudio[8455]: module-x11-xsmp.c: X11 session manager not running.
Feb  8 09:34:19 bear pulseaudio[8455]: module.c: Failed to load  module "module-x11-xsmp" (argument: ""): initialization failed.

```

That output came from when I ran the Hardware Testing app.

Suggestions?


--- Edit: figured out the audio. Not sure why those errors are in the log, but it does work. Apparently the volume was just MUCH lower, after turning everything up quite a bit I could hear it.

---

