---
title: "Flash 10 (x86-64) through pulseaudio crashes"
date: 2009-01-09
forum: Multimedia Software
---

### Post by dax2112rush on 2009-01-09
Hello all,
I have a problem with Flash 10 x86-64 (10.0 d21) crashing when it tries to output sound. I can reproduce the problem simply by tring to play any video on youtube.

I get the following output when running firefox from console

```

ALSA lib pcm_pulse.c:616:(pulse_prepare) PulseAudio: Unable to create stream: Invalid argument

firefox: pcm_pulse.c:361: pulse_write: Assertion `pcm->stream' failed.

```

I took a look at the pcm_pulse.c file (got it through apt-get source libasound2-plugins), and the corresponding lines dont contain assertion or output to console). Grepping through the file returns a print with PULSEAUDIO: Unable to create stream, but I notice the case is not the same as my error message.

I suspect flash/firefox are using a wrong version of libasound2-plugins.
Any help as to how to figure that out would be appreciated!

My current sound config is:

Alsa default sink: pcm_pulse (routes all audio through pulseaudio)
Pulseaudio (0.9.10): realtime
                     sources: alsa, jackd
                     sinks: jackd
jackd (0.116.1)    : realtime 
                     all output/input routed to/from hw alsa device

Most of applications seem to work fine including amarok2, totem, etc...

Additionnal info:

Ubuntu 8.10 x86-64 running generic kernel

```

dax@RockStar:/usr/lib/firefox-addons/plugins$ file libflashplayer.so 
libflashplayer.so: ELF 64-bit LSB shared object, x86-64, version 1 (SYSV), dynamically linked, stripped
```

```

dax@RockStar:/usr/lib/firefox-addons/plugins$ ldd libflashplayer.so 
	linux-vdso.so.1 =>  (0x00007fff679ff000)
	libstdc++.so.6 => /usr/lib/libstdc++.so.6 (0x00007f775a8e5000)
	libpthread.so.0 => /lib/libpthread.so.0 (0x00007f775a6c9000)
	libX11.so.6 => /usr/lib/libX11.so.6 (0x00007f775a3c0000)
	libXext.so.6 => /usr/lib/libXext.so.6 (0x00007f775a1ae000)
	libXt.so.6 => /usr/lib/libXt.so.6 (0x00007f7759f4a000)
	libfreetype.so.6 => /usr/lib/libfreetype.so.6 (0x00007f7759cc5000)
	libfontconfig.so.1 => /usr/lib/libfontconfig.so.1 (0x00007f7759a93000)
	libgtk-x11-2.0.so.0 => /usr/lib/libgtk-x11-2.0.so.0 (0x00007f77594ac000)
	libgdk-x11-2.0.so.0 => /usr/lib/libgdk-x11-2.0.so.0 (0x00007f775920a000)
	libatk-1.0.so.0 => /usr/lib/libatk-1.0.so.0 (0x00007f7758fe9000)
	libgdk_pixbuf-2.0.so.0 => /usr/lib/libgdk_pixbuf-2.0.so.0 (0x00007f7758dcd000)
	libpangocairo-1.0.so.0 => /usr/lib/libpangocairo-1.0.so.0 (0x00007f7758bc0000)
	libpango-1.0.so.0 => /usr/lib/libpango-1.0.so.0 (0x00007f7758977000)
	libcairo.so.2 => /usr/lib/libcairo.so.2 (0x00007f77586fc000)
	libgobject-2.0.so.0 => /usr/lib/libgobject-2.0.so.0 (0x00007f77584b5000)
	libgmodule-2.0.so.0 => /usr/lib/libgmodule-2.0.so.0 (0x00007f77582b1000)
	libdl.so.2 => /lib/libdl.so.2 (0x00007f77580ad000)
	libglib-2.0.so.0 => /usr/lib/libglib-2.0.so.0 (0x00007f7757de7000)
	libnss3.so => /usr/lib/libnss3.so (0x00007f7757a9a000)
	libsmime3.so => /usr/lib/libsmime3.so (0x00007f775786e000)
	libssl3.so => /usr/lib/libssl3.so (0x00007f7757636000)
	libplds4.so => /usr/lib/libplds4.so (0x00007f7757432000)
	libplc4.so => /usr/lib/libplc4.so (0x00007f775722d000)
	libnspr4.so => /usr/lib/libnspr4.so (0x00007f7756fef000)
	libm.so.6 => /lib/libm.so.6 (0x00007f7756d6a000)
	libgcc_s.so.1 => /lib/libgcc_s.so.1 (0x00007f7756b52000)
	libc.so.6 => /lib/libc.so.6 (0x00007f77567df000)
	/lib64/ld-linux-x86-64.so.2 (0x00007f775f819000)
	libxcb-xlib.so.0 => /usr/lib/libxcb-xlib.so.0 (0x00007f77565dd000)
	libxcb.so.1 => /usr/lib/libxcb.so.1 (0x00007f77563c1000)
	libXau.so.6 => /usr/lib/libXau.so.6 (0x00007f77561be000)
	libSM.so.6 => /usr/lib/libSM.so.6 (0x00007f7755fb5000)
	libICE.so.6 => /usr/lib/libICE.so.6 (0x00007f7755d9a000)
	libz.so.1 => /usr/lib/libz.so.1 (0x00007f7755b81000)
	libexpat.so.1 => /usr/lib/libexpat.so.1 (0x00007f7755957000)
	libXcomposite.so.1 => /usr/lib/libXcomposite.so.1 (0x00007f7755754000)
	libXdamage.so.1 => /usr/lib/libXdamage.so.1 (0x00007f7755551000)
	libXfixes.so.3 => /usr/lib/libXfixes.so.3 (0x00007f775534c000)
	libgio-2.0.so.0 => /usr/lib/libgio-2.0.so.0 (0x00007f77550d5000)
	libpangoft2-1.0.so.0 => /usr/lib/libpangoft2-1.0.so.0 (0x00007f7754ea7000)
	libXrender.so.1 => /usr/lib/libXrender.so.1 (0x00007f7754c9d000)
	libXinerama.so.1 => /usr/lib/libXinerama.so.1 (0x00007f7754a9b000)
	libXi.so.6 => /usr/lib/libXi.so.6 (0x00007f775488f000)
	libXrandr.so.2 => /usr/lib/libXrandr.so.2 (0x00007f7754687000)
	libXcursor.so.1 => /usr/lib/libXcursor.so.1 (0x00007f775447d000)
	libpixman-1.so.0 => /usr/lib/libpixman-1.so.0 (0x00007f7754238000)
	libpng12.so.0 => /usr/lib/libpng12.so.0 (0x00007f7754011000)
	libxcb-render-util.so.0 => /usr/lib/libxcb-render-util.so.0 (0x00007f7753e0c000)
	libxcb-render.so.0 => /usr/lib/libxcb-render.so.0 (0x00007f7753c03000)
	libpcre.so.3 => /lib/libpcre.so.3 (0x00007f77539d3000)
	libnssutil3.so.1d => /usr/lib/libnssutil3.so.1d (0x00007f77537b4000)
	libXdmcp.so.6 => /usr/lib/libXdmcp.so.6 (0x00007f77535af000)
	libselinux.so.1 => /lib/libselinux.so.1 (0x00007f7753392000)

```

I wish Gnash would be able to play Youtube/Last.fm!
Thanks!

---

### Post by dax2112rush on 2009-01-09
I think I found the problem... to install latest version of jackd, I added Jaunty repositories and it required update of libasound2*. Updating pulseaudio to Jaunty's repository latest version seems to have fixed it (0.9.13). However, I now get no sound since pulseaudio aborts on startup, showing this:

```

dax@RockStar:~/SourceBuilds/pulseaudio-0.9.13/src/pulsecore$ pulseaudio -vvv
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root priviliges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
D: main.c: Started as real root: no, suid root: yes
I: main.c: We're in the group 'pulse-rt', allowing high-priority scheduling.
I: main.c: RLIMIT_RTPRIO is set to 99, allowing real-time scheduling.
I: main.c: RLIMIT_NICE is set to 40, allowing high-priority scheduling.
I: core-util.c: Successfully gained nice level -11.
D: main.c: Can realtime: yes, can high-priority: yes
I: main.c: Giving up CAP_NICE
D: main.c: Can realtime: yes, can high-priority: yes
I: main.c: This is PulseAudio 0.9.13
D: main.c: Compilation host: x86_64-pc-linux-gnu
D: main.c: Compilation CFLAGS: -g -O2 -g -Wall -O2 -Wall -W -Wextra -pedantic -pipe -Wno-long-long -Wvla -Wno-overlength-strings -Wconversion -Wundef -Wformat -Wlogical-op -Wpacked -Wformat-security -Wmissing-include-dirs -Wformat-nonliteral -Wold-style-definition -Wdeclaration-after-statement -Wfloat-equal -Wmissing-declarations -Wmissing-prototypes -Wstrict-prototypes -Wredundant-decls -Wmissing-noreturn -Wshadow -Wendif-labels -Wpointer-arith -Wcast-align -Wwrite-strings -Wno-unused-parameter -ffast-math
D: main.c: Running on host: Linux x86_64 2.6.27-9-generic #1 SMP Thu Nov 20 22:15:32 UTC 2008
I: main.c: Page size is 4096 bytes
D: main.c: Compiled with Valgrind support: no
D: main.c: Running in valgrind mode: no
D: main.c: Optimized build: yes
I: main.c: Machine ID is dea21f1f72d16b48d2a69b9b48ed5940.
I: main.c: Using runtime directory /home/dax/.pulse/dea21f1f72d16b48d2a69b9b48ed5940:runtime.
I: main.c: Using state directory /home/dax/.pulse.
I: main.c: Running in system mode: no
W: pid.c: Stale PID file, overwriting.
I: main.c: Fresh high-resolution timers available! Bon appetit!
D: memblock.c: Using shared memory pool with 1024 slots of size 64.0 KiB each, total size is 64.0 MiB
E: rtpoll.c: Assertion 'p' failed at pulsecore/rtpoll.c:710, function pa_rtpoll_item_new_asyncmsgq_read(). Aborting.
Aborted

```

Perhaps libasound2-plugins should be listed as incompatible with libpulse0 corresponding to pulseaudio 0.9.10 (I'd need to confirm whether it works once I can get pulseaudio to start...)

---

### Post by dax2112rush on 2009-01-09
Another incompatible version problem... pulesaudio-module-jack(from debian) was out of sync with pulseaudio... 

Why isn't it included in Ubuntu's repositories?

---

### Post by markbuntu on 2009-01-09
Dependency issues and other problems should be expected when installing from outside the repositories and/or grabbing packages from upstream. You are lucky you don't have larger problems as Jaunty is still very unstable.

Pulse 0.9.13 is far removed from 0.9.10 so it is no wonder the pulseaudio-jack modules you have no longer work. Debian Lenny, where those modules came from, is using 0.9.10 as far as I know. There may be a newer version of those modules in Debian Unstable but you should check that they are built for 0.9.13.

Anyway, flash 10 should work just fine if you put everything back the way it was.

---

