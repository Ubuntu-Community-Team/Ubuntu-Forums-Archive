---
title: "No sound on some MP3's"
date: 2011-12-23
forum: Multimedia Software
---

### Post by RealityMaster on 2011-12-23
I hate to even post this, as it seems like such a noob question, but I can't get it working and I've spent two weeks on it, so here it is...

Some of my MP3's will not play on my desktop, these same MP3's will play streamed from my desktop to my XBMC box (also Ubuntu same version and build).  It appears the ratio is about 60/40, 40% play 60% are silent.  I have tried using Rhythembox (my default music player), VLC, QMMS, and totem.  All of which will  play these mp3s but no sound is created by doing so.  It's not a volume issue (that I can tell) as hitting next track a few times plays an MP3 with sound.

](*,)

I do have the Ubuntu restricted extras installed, as I said I can play a lot of them, just not all.

perhaps helpful?

```
:~$ cat /proc/version
Linux version 3.0.0-15-generic (buildd@allspice) (gcc version 4.6.1 (Ubuntu/Linaro 4.6.1-9ubuntu3) ) #24-Ubuntu SMP Mon Dec 12 15:23:55 UTC 2011

```

Although I doubt it matters...
```
:~$ lspci | grep Audio
00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
```

VLC output (this song works)
```
VLC media player 1.1.12 The Luggage (revision exported)
Blocked: call to unsetenv("DBUS_ACTIVATION_ADDRESS")
Blocked: call to unsetenv("DBUS_ACTIVATION_BUS_TYPE")
[0xfe5120] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
Blocked: call to setlocale(6, "")
Blocked: call to setlocale(6, "")

(process:5332): Gtk-WARNING **: Locale not supported by C library.
	Using the fallback 'C' locale.
QPixmap::handle(): Pixmap is not an X11 class pixmap
QPixmap::handle(): Pixmap is not an X11 class pixmap
Blocked: call to setlocale(6, "")
QPixmap::handle(): Pixmap is not an X11 class pixmap

```

Same thing, but this song is silent...
```
VLC media player 1.1.12 The Luggage (revision exported)
Blocked: call to unsetenv("DBUS_ACTIVATION_ADDRESS")
Blocked: call to unsetenv("DBUS_ACTIVATION_BUS_TYPE")
[0x1679120] main libvlc: Running vlc with the default interface. Use 'cvlc' to use vlc without interface.
Blocked: call to setlocale(6, "")
Blocked: call to setlocale(6, "")

(process:5276): Gtk-WARNING **: Locale not supported by C library.
	Using the fallback 'C' locale.
QPixmap::handle(): Pixmap is not an X11 class pixmap
QPixmap::handle(): Pixmap is not an X11 class pixmap
Blocked: call to setlocale(6, "")
QPixmap::handle(): Pixmap is not an X11 class pixmap
QPixmap::handle(): Pixmap is not an X11 class pixmap
Warning: call to rand()
Warning: call to rand()
Warning: call to rand()

```

Any help or direction would be great.

---

