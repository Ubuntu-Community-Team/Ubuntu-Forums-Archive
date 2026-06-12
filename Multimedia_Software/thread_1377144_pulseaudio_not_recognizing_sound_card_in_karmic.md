---
title: "pulseaudio not recognizing sound card in karmic"
date: 2010-01-09
forum: Multimedia Software
---

### Post by markthefart on 2010-01-09
I had sound in Jaunty, and I just upgraded to Karmic, and everything else is working 100% ok. Except for sound. I have no sound at all if I use any other driver than OSS. I have pulseaudio installed but it doesn't recognize my sound card.

[IMG]http://img413.imageshack.us/img413/9531/snapshot1fd.png[/IMG]

I searched google and these and kubuntu forums and there is a lot of people having trouble with karmic and pulseaudio and nvidia hda cards but I can't seem to find a solution. 
Here's the output from pulseaudio -vvvv:

```
mark@moomoo:~$ pulseaudio -vvvv
I: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
I: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
D: core-rtclock.c: Timer slack is set to 50 us.
I: core-util.c: Failed to acquire high-priority scheduling: Input/output error
I: main.c: This is PulseAudio 0.9.21
D: main.c: Compilation host: x86_64-pc-linux-gnu
D: main.c: Compilation CFLAGS: -g -O2 -g -Wall -O3 -Wall -W -Wextra -pipe -Wno-long-long -Winline -Wvla -Wno-overlength-strings -Wunsafe-loop-optimizations -Wundef -Wformat=2 -Wlogical-op -Wsign-compare -Wformat-security -Wmissing-include-dirs -Wformat-nonliteral -Wold-style-definition -Wpointer-arith -Winit-self -Wdeclaration-after-statement -Wfloat-equal -Wmissing-prototypes -Wstrict-prototypes -Wredundant-decls -Wmissing-declarations -Wmissing-noreturn -Wshadow -Wendif-labels -Wcast-align -Wstrict-aliasing=2 -Wwrite-strings -Wno-unused-parameter -ffast-math -Wp,-D_FORTIFY_SOURCE=2 -fno-common -fdiagnostics-show-option
D: main.c: Running on host: Linux x86_64 2.6.28-17-generic #58-Ubuntu SMP Tue Dec 1 21:27:25 UTC 2009
D: main.c: Found 2 CPUs.
I: main.c: Page size is 4096 bytes
D: main.c: Compiled with Valgrind support: no
D: main.c: Running in valgrind mode: no
D: main.c: Running in VM: no
D: main.c: Optimized build: yes
D: main.c: All asserts enabled.
I: main.c: Machine ID is bff001fe2ac1259b94ac3d724a4e2699.
I: main.c: Session ID is bff001fe2ac1259b94ac3d724a4e2699-1263096657.626377-205770779.
I: main.c: Using runtime directory /home/mark/.pulse/bff001fe2ac1259b94ac3d724a4e2699-runtime.
I: main.c: Using state directory /home/mark/.pulse.
I: main.c: Using modules directory /usr/lib/pulse-0.9.21/modules.
I: main.c: Running in system mode: no
E: pid.c: Daemon already running.
E: main.c: pa_pid_file_create() failed.

```

and aplay -l

```

mark@moomoo:~$ aplay -l
aplay: device_list:223: no soundcards found...

```

and hwinfo --sound
```


mark@moomoo:~$ hwinfo --sound
14: PCI 05.0: 0403 Audio device
  [Created at pci.318]
  UDI: /org/freedesktop/Hal/devices/pci_10de_3f0
  Unique ID: CvwD._cBF2M4D_Q4
  SysFS ID: /devices/pci0000:00/0000:00:05.0
  SysFS BusID: 0000:00:05.0
  Hardware Class: sound
  Model: "nVidia MCP61 High Definition Audio"
  Vendor: pci 0x10de "nVidia Corporation"
  Device: pci 0x03f0 "MCP61 High Definition Audio"
  SubVendor: pci 0x1028 "Dell"
  SubDevice: pci 0x020e
  Revision: 0xa2
  Driver: "HDA Intel"
  Driver Modules: "snd_hda_intel"
  Memory Range: 0xfe024000-0xfe027fff (rw,non-prefetchable)
  IRQ: 23 (32290 events)
  Module Alias: "pci:v000010DEd000003F0sv00001028sd0000020Ebc04sc03i00"
  Driver Info #0:
    Driver Status: snd_hda_intel is active
    Driver Activation Cmd: "modprobe snd_hda_intel"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

```

Hope somebody can shed some light! :)
Cheers,
Mark

---

### Post by markthefart on 2010-01-10
I completely uninstalled PulseAudio and now my sound card is recognized again and works great with Alsa. No low volume problems anymore. Going to leave it like this I guess. I don't do any intensive video/audio edititing so I suppose working without PulseAudio is do-able.

---

