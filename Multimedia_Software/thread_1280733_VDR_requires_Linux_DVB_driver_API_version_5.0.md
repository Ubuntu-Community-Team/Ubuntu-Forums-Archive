---
title: "VDR requires Linux DVB driver API version 5.0"
date: 2009-10-02
forum: Multimedia Software
---

### Post by emmanneil on 2009-10-02
anyone got any ideas on this ?
i am using ubuntu 8.10 with all the latest updates

root@xxxxxx-desktop:/usr/local/src/vdr-1.7.9# make
In file included from audio.c:12:
dvbdevice.h:20:2: error: #error VDR requires Linux DVB driver API version 5.0!
In file included from dvbdevice.c:10:
dvbdevice.h:20:2: error: #error VDR requires Linux DVB driver API version 5.0!
In file included from dvbosd.c:15:
dvbdevice.h:20:2: error: #error VDR requires Linux DVB driver API version 5.0!
In file included from eitscan.c:13:
dvbdevice.h:20:2: error: #error VDR requires Linux DVB driver API version 5.0!
In file included from vdr.c:45:
dvbdevice.h:20:2: error: #error VDR requires Linux DVB driver API version 5.0!
make: *** Deleting file `.dependencies'
g++ -g -O2 -Wall -Woverloaded-virtual -Wno-parentheses -c -DUSE_SETUP -DUSE_TTXTSUBS -DREMOTE_KBD -DLIRC_DEVICE=\"/dev/lircd\" -DRCU_DEVICE=\"/dev/ttyS1\" -D_GNU_SOURCE -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -D_LARGEFILE64_SOURCE -DVIDEODIR=\"/media/video/vdr\" -DCONFDIR=\"/etc/vdr\" -DPLUGINDIR=\"/usr/lib/vdr/plugins\" -DLOCDIR=\"/usr/share/locale\" -I/usr/include/freetype2 -I/usr/local/src/s2-liplianin/linux/include audio.c
In file included from audio.c:12:
dvbdevice.h:20:2: error: #error VDR requires Linux DVB driver API version 5.0!
make: *** [audio.o] Error 1

thanks

---

### Post by caribo on 2009-11-21
same here !  

If I find an answer I will update here..

---

### Post by mammuth on 2009-11-23
I had the same error.
The vdr source requires api version 5.0
```
if DVB_API_VERSION != 5 || DVB_API_VERSION_MINOR != 0
```

The latest dvb drivers has api 5.1.

In vdr-1.7.10 it's changed to 5.0 or higher.

/Mammuth

---

### Post by mammuth on 2009-11-23
Might only be the check that is changed.
If you dont't want to update you could try patching the check in the vdr source (untested).

File: vdr/dvbdevice.h

Before:
```
#if DVB_API_VERSION != 5 || DVB_API_VERSION_MINOR != 0
#error VDR requires Linux DVB driver API version 5.0!
#endif
```

After:
```
#if DVB_API_VERSION < 5
#error VDR requires Linux DVB driver API version 5.0 or higher!
#endif
```

---

### Post by benneton on 2011-03-13
This is reply to an old topic, but maybe someone find this useful... :)

This works for me on VDR version 1.6.0 and 1.7.16!

I've commented out those DVB_API_ VERSION check lines.


```

//#if DVB_API_VERSION != 3
//#error VDR requires Linux DVB driver API version 3!
//#endif

```



Also, use gcc version 4.1 to compile your VDR source.


```

sudo make CC=gcc-4.1 CXX=g++-4.1
sudo make plugins CC=gcc-4.1 CXX=g++-4.1

```

I'm using Ubuntu 10.04 (Lucid Lynx)

Regards!

---

