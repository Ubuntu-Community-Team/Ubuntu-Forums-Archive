---
title: "I need to use old oss modules, unable to without recompiling kernel. padsp=no work"
date: 2013-04-06
forum: Multimedia Software
---

### Post by interzoneuk on 2013-04-06
Hi.

For some games I _**need**_ the old oss modules.

snd-seq-oss
snd-pcm-oss

However the Ubuntu kernel is now compiled without those modules. 

As a solution I have just downloaded the ubuntu kernel source and recompiled it including these modules. 


CONFIG_SND_PCM_OSS:
CONFIG_SND_SEQUENCER_OSS:

Is there another way to get them so I can avoid the hassle of having to do this (its annoying due to the frequency of kernel updates)?

alsa-oss and oss-compat do not contain the modules. The game I am trying to run (dplogin.com although any game that needs oss modules does the same)  is 32bit I have tried to use the i386 versions of 'alsa-oss' and 'oss-compat' - same result.

aoss and padsp do not work with the game I am trying . 

```
aoss ./paintball2

---------------------------------------
ERROR: ld.so: object '/usr/lib/i386-linux-gnu/libaoss.so' from LD_PRELOAD cannot be preloaded: ignored.
---------------------------------------
```

```
padsp ./paintball2

ERROR: ld.so: object '/usr/lib/x86_64-linux-gnu/pulseaudio/libpulsedsp.so' from LD_PRELOAD cannot be preloaded: ignored.
```

Just to confirm I have the following packages installed

-----------------------------------------------------------------------
dpkg -l |egrep "pulse|alsa|oss-c"
ii alsa-base 1.0.25+dfsg-0ubuntu3.1 all ALSA driver configuration files
ii alsa-oss 1.0.25-1 i386 ALSA wrapper for OSS applications
ii alsa-utils 1.0.25-3ubuntu2 amd64 Utilities for configuring and using ALSA
ii bluez-alsa:amd64 4.101-0ubuntu6 amd64 Bluetooth ALSA support
ii gstreamer0.10-alsa:amd64 0.10.36-1ubuntu1.1 amd64 GStreamer plugin for ALSA
ii gstreamer0.10-pulseaudio:amd64 0.10.31-3ubuntu1.2 amd64 GStreamer plugin for PulseAudio
ii libcanberra-pulse:amd64 0.29-0ubuntu2 amd64 PulseAudio backend for libcanberra
ii libpulse-mainloop-glib0:amd64 1:2.1-0ubuntu4 amd64 PulseAudio client libraries (glib support)
ii libpulse-mainloop-glib0:i386 1:2.1-0ubuntu4 i386 PulseAudio client libraries (glib support)
ii libpulse0:amd64 1:2.1-0ubuntu4 amd64 PulseAudio client libraries
ii libpulse0:i386 1:2.1-0ubuntu4 i386 PulseAudio client libraries
ii libpulsedsp:amd64 1:2.1-0ubuntu4 amd64 PulseAudio OSS pre-load library
ii libpulsedsp:i386 1:2.1-0ubuntu4 i386 PulseAudio OSS pre-load library
ii oss-compat 2ubuntu1 amd64 Open Sound System (OSS) compatibility package
ii pulseaudio 1:2.1-0ubuntu4 amd64 PulseAudio sound server
ii pulseaudio-module-bluetooth 1:2.1-0ubuntu4 amd64 Bluetooth module for PulseAudio sound server
ii pulseaudio-module-x11 1:2.1-0ubuntu4 amd64 X11 module for PulseAudio sound server
ii pulseaudio-utils 1:2.1-0ubuntu4 amd64 Command line tools for the PulseAudio sound server
-----------------------------------

As mentioned if I recompile the kernel and include 

CONFIG_SND_PCM_OSS:
CONFIG_SND_SEQUENCER_OSS:

I can then modprobe 

snd-pcm-oss
snd-pcm-oss

And all oss apps work...

lspci shows the device as

```
00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04) 
```

Does anyone have any ideas how to avoid the pain of recompiling the entire kernel just to get those 2 oss modules ? (or another way I can get oss emulation?)

Regards

---

### Post by tgalati4 on 2013-04-06
What are the games?  Perhaps send an email to the developers/maintainers and ask them to update them to alsa or pulseaudio.  It can't be that difficult to upgrade an audio framework within a game.

Or delay your kernel updates to once a year and save up your agony units.

Or, try modifying the games yourself, if you have the source.

Thanks for the dpkg one-liner for extracting all of the sound frameworks on a system.  That could be handy.

---

### Post by interzoneuk on 2013-04-07
The game is digital paint 2 (dplogin.com) - but the same thing happens with all games/apps that use OSS...

The developer is planning to do openal support in the future, he hates developing for Linux so is unlikely to put the effort into the game client (linux is mainly used for servers in the game however he does grudgingly create the clint too..) 

Sorry the one liner had a mistake... corrected now.

---

### Post by kostkon on 2013-04-07
Tried running it with padsp? i.e.
```
padsp digitalpaint2_executable_here
```

---

### Post by interzoneuk on 2013-04-07
> **kostkon said:**
> Tried running it with padsp? i.e.
```
padsp digitalpaint2_executable_here
```

yes (its mentioned in the 1st post)

----------------------------------------------------------------------
ERROR: ld.so: object '/usr/lib/x86_64-linux-gnu/pulseaudio/libpulsedsp.so' from LD_PRELOAD cannot be preloaded: ignored.

Paintball 2 -- Version 2.0
Execing configs/config.cfg.
Console initialized.

------- Sound initialization -------
LoadLibrary("./snd_oss.so")
/dev/dsp: No such file or directory
SNDDMA_Init: Could not open /dev/dsp.
----------------------------------------------------------------------

---

