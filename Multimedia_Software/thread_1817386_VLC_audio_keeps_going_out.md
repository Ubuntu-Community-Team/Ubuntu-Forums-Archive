---
title: "VLC audio keeps going out"
date: 2011-08-03
forum: Multimedia Software
---

### Post by floydian_slip on 2011-08-03
Hi,

For some reason, when I use VLC (but *not* when I use Parole), the audio sometimes goes out. Either it'll randomly go out, in which case I get the following error:

```
[0x1af5f70] main input error: ES_OUT_SET_(GROUP_)PCR  is called too late (pts_delay increased to 300 ms)

```

or, any time I pause the video and then resume, it also goes out (this time with no printed error, though).

Luckily I don't have to restart the video to get the audio back... I just click "Audio", "Channels", "Stereo" (which is already chosen), and the audio resets. But you can imagine how annoying this can get. It usually happens 3-4 times during the first 10 mins, then afterwards it tends to stop.

Any idea what could be going on? Here's the whole printout of when I watch a MKV filetype movie, up to the first audio outage.

```
brian@brian-pc:/media/FreeAgent GoFlex Drive/Videos/Series/Seinfeld/Episodes$ vlc 075\ -\ The\ Dinner\ Party.mkv 
VLC media player 1.1.9 The Luggage (revision exported)
Blocked: call to unsetenv("DBUS_ACTIVATION_ADDRESS")
Blocked: call to unsetenv("DBUS_ACTIVATION_BUS_TYPE")
[0x198d120] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
 m_el[mi_level] == NULL
 arrrrrrrrrrrrrg Up cannot escape itself
Blocked: call to setlocale(6, "")
Blocked: call to setenv("ORBIT_SOCKETDIR", "/tmp/orbit-brian", 1)
Warning: call to srand(1312467051)
Warning: call to rand()
Blocked: call to setlocale(6, "")

(process:3205): Gtk-WARNING **: Locale not supported by C library.
	Using the fallback 'C' locale.
 m_el[mi_level] == NULL
 arrrrrrrrrrrrrg Up cannot escape itself
[0x1a832b0] signals interface error: signal 17 overriden (0x7fe6cebcb450)
[0x1a832b0] signals interface error:  /usr/lib/libQtCore.so.4(?)[(nil)]
[0x1af5f70] main input error: ES_OUT_SET_(GROUP_)PCR  is called too late (pts_delay increased to 300 ms)
[0x1a832b0] signals interface error: signal 17 overriden (0x7fe6cebcb450)
[0x1a832b0] signals interface error:  /usr/lib/libQtCore.so.4(?)[(nil)]

```

Thanks for any help.

Brian

P.S. I'm using Xubuntu but assume that the problem isn't related to that, though I don't know for sure...

---

### Post by ajgreeny on 2011-08-03
What hardware and what version of Ubuntu?

---

### Post by floydian_slip on 2011-08-03
I've got an HDA Intel card, Realtek ALC269 chip. And if it helps:

```

  *-multimedia            
       description: Audio device
       product: 82801I (ICH9 Family) HD Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=HDA Intel latency=0
       resources: irq:46 memory:fe9f4000-fe9f7fff

```

I'm running Xubuntu 11.04, and Xfce version 4.8.0.

---

