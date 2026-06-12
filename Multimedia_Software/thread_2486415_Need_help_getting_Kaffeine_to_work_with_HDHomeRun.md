---
title: "Need help getting Kaffeine to work with HDHomeRun"
date: 2023-04-29
forum: Multimedia Software
---

### Post by sremick on 2023-04-29
So I have an HDHomeRun Duo Scribe (has built-in DVR abilities) hooked up and running (I can use it using the Windows app). So we know that's working.

I need to be able to get similar functionality for an Ubuntu system. It seems Kaffeine is the best choice to offer similar functionality on Linux as the HDHomeRun app provides on Windows. I'm not wedded to Kaffeine if there's something better, but please no suggestions for Plex, MythTV, or any other separate server solutions as that's not an option here. Thanks

The web interface for the HDHomeRun is more for config and not really usable as your main viewing interface, unfortunately (that'd be too easy).

It seems what I'm missing are the HDHomeRun "dvb" drivers, which will then supposedly allow Kaffeine to magically work? Not clear how, but I've been focusing on that first.

I did find this resource: [https://help.ubuntu.com/community/HDHomeRun](https://help.ubuntu.com/community/HDHomeRun)
And I did download the dvb drivers it links to here: [https://sourceforge.net/apps/trac/dvbhdhomerun/wiki/UbuntuPackages](https://sourceforge.net/apps/trac/dvbhdhomerun/wiki/UbuntuPackages)

Unfortunately that last link lacks any documentation/instructions. I tried following those in build.txt but it fails quickly with errors. For example, if I cd into kernel and then run "make" as it instructs, I get an error:

```
make -C /lib/modules/`uname -r`/build M=/home/scott/Downloads/dvbhdhomerun/kernel modules
make[1]: Entering directory '/usr/src/linux-headers-5.19.0-38-generic'
warning: the compiler differs from the one used to build the kernel
  The kernel was built by: x86_64-linux-gnu-gcc (Ubuntu 11.3.0-1ubuntu1~22.04) 11.3.0
  You are using:           gcc (Ubuntu 11.3.0-1ubuntu1~22.04) 11.3.0
  CC [M]  /home/scott/Downloads/dvbhdhomerun/kernel/dvb_hdhomerun_init.o
/home/scott/Downloads/dvbhdhomerun/kernel/dvb_hdhomerun_init.c:29:10: fatal error: dvb_demux.h: No such file or directory
   29 | #include "dvb_demux.h"
      |          ^~~~~~~~~~~~~
compilation terminated.
make[2]: *** [scripts/Makefile.build:257: /home/scott/Downloads/dvbhdhomerun/kernel/dvb_hdhomerun_init.o] Error 1
make[1]: *** [Makefile:1850: /home/scott/Downloads/dvbhdhomerun/kernel] Error 2
make[1]: Leaving directory '/usr/src/linux-headers-5.19.0-38-generic'
make: *** [Makefile:27: dvb_hdhomerun] Error 2

```

My searching also lead me to this: [https://github.com/h0tw1r3/dvbhdhomerun](https://github.com/h0tw1r3/dvbhdhomerun)
... which I tried, but unfortunately it depends on dh-systemd which doesn't seem to exist anymore.

Hopefully I've shown sufficient effort before posting here. I'm happy with an alternative to Kaffeine if it provides similar functionality (channel guide, changing channels, DVR controls, etc). I'd also be happy with a web interface if I'm missing one and there's a secret web interface that provides the same functionality as the Windows app.

Thanks!

---

### Post by TheFu on 2023-04-29
Newer HDHR tuners support DLNA.  You can use any DLNA controller, renderer, and server together with HDHR models that aren't too old.  For example, I have HDHR5-4US (quad tuner) and HDHR4-2US (dual tuner) models. Previously, I had 2 Dual tuner models, but they required drivers and it was too much hassle getting all that working on Linux.  

With the newer models, I've had no issues getting them to playback to any device ... I even use mplayer/mpv to watch TV and wget to "record" it.  I don't have the DVR model hdhomerun, so I don't know anything about it.

Anyway, for the DVR functionality, I found jellyfin media server to be the easiest way, but you said you aren't interest in that type of solution.  I don't think any other general use TV application will provide the integration you desire. HDHR stuff is just too specific.  Jellyfin has a web interface for TV (live and recordings).  With Android as a DLNA controller (lots of apps can do that if you don't want to install the Jellyfin app), you can tell Jellyfin to play to any "DLNA Renderer" on your network. That can be the local machine, the android device or some other device ... for example, I usually tell it to play to a raspberry pi connected to a large screen.

If you do become interested in other options and decide that it is slightly interesting to consider those other options in the next few days, I can respond.  After about a week, I stop following threads that aren't active/interesting to me.

---

