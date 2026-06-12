---
title: "No video playback"
date: 2010-01-06
forum: Multimedia Software
---

### Post by quini on 2010-01-06
Hi,

I've installed Ubuntu 9.10 64bit in my brand new mini-pc.  It's got an Nvidia ION chipset (Nvidia graphics are in it), and an Atom 330.

Everything went fine, also video (mainly xvid) playback, but that was yesterday...

Today **I get only audio; video shows black only.  The strange is that the same behaviour happens with Totem, Xine and Vlc, so I guess it must be graphic driver related**... I'm using Nvidia driver 185.18.36, installed automatically by Ubuntu.

Here's some output from totem & vlc; maybe it helps:

```
quini@atom:~$ totem --gst-debug-level=2
0:00:00.079695828  6878       0x8d10e0 WARN      GST_PLUGIN_LOADING gstplugin.c:422:gst_plugin_register_func: plugin "/usr/lib/gstreamer-0.10/libgstladspa.so" failed to initialise
0:00:00.086435931  6878       0x8d10e0 WARN                pyplugin gstpythonplugin.c:343:plugin_init: Couldn't g_module_open libpython. Reason: /usr/lib/libpython2.6.so: cannot open shared object file: No such file or directory
0:00:00.086524401  6878       0x8d10e0 WARN      GST_PLUGIN_LOADING gstplugin.c:422:gst_plugin_register_func: plugin "/usr/lib/gstreamer-0.10/libgstpython.so" failed to initialise
0:00:21.164567197  6877      0x1c10170 WARN                   pulse pulsesink.c:523:gst_pulsering_stream_underflow_cb:<audio-sink> Got underflow
```
```
quini@atom:~$ vlc
VLC media player 1.0.2 Goldeneye
[0x1cf8168] main interface error: no interface module matched "globalhotkeys,none"
[0x1cf8168] main interface error: no suitable interface module
[0x1be1888] main libvlc error: interface "globalhotkeys,none" initialization failed
[0x1be1888] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
[0x22b8818] a52 decoder: A/52 channels:6 samplerate:48000 bitrate:448000
[0x2eeb218] pulse audio output: No. of Audio Channels: 6
QPainter::begin: Paint device returned engine == 0, type: 1
```

Any idea?  I'd prefer not to reinstall, but...

TIA  ;)

---

### Post by quini on 2010-01-07
Hi!

As it's a brand new computer, and the problem seems strange to me -I'm using linux since year 2000-, I've reinstalled Ubuntu...

... and after installing a brand new system onto /, keeping the same /home, I'm experiencing the same problems: totem, xine & vlc show a black screen, but audio plays fine.

This time I've noticed that **it's my user's problem, not system-wide!**  As I've copied all user's data from my laptop (keeping the user ID), I'm now looking into the config files looking for the problem.

I'll keep you informed!  Maybe this is helpfull to someone out there!  ;)

Thanks for your time!

---

### Post by quini on 2010-01-07
Hi!

I've finally located the problem; it's somewhere in ~/.gconf/apps/

Renaming the "apps" directory did the trick... video is now showing fine !!

Hopefully it helps someone!  Tnx!  ;)

---

### Post by howcanireachthesekids on 2010-01-13
hey, i have exactly the same problem !

how did you fix the problem more specifically ? you are not so understandable in the last post :popcorn:

---

### Post by quini on 2010-01-13
Hi!

First rename the ~/.gconf/apps directory; that's going to "reset" all configurations stored there with defaults'
```
mv ~/.gconf/apps ~/.gconf/apps.bak
```

Second log out & log in again.

The configuration of some programs has been reset to defaults; configure them again and you're done!

Hope the above helps  ;)

---

