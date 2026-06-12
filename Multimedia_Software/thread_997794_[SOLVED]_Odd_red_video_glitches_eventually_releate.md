---
title: "[SOLVED] Odd red video glitches eventually releated to xine"
date: 2008-11-30
forum: Multimedia Software
---

### Post by RytmenPinnen on 2008-11-30
I've come across some weird and most annoying video glitches. The output blinks either completely red for one frame or one frame of red squares in a chessboard kind of way. I'm suspecting its related to xine because all video players that I've tried have the same glitches, vlc, mplayer and kaffeine.

I'm running Kubuntu 8.10 64bit on:
amd 5400+ x2
4gb ram
9600gt with the 180.08 beta drivers, and now that I start to think, it might aswell be related to these. I'd rather not downgrade tho cause kde4 runs much smoother on these :)

Edit: with some further testing it seems as it was the kwin effects that did it, I didn't even know I had them enabled.

---

### Post by adde83 on 2009-10-07
Hello I had same problem. 
Changing Preferences->Video->output modules   from Default to X11 video output seemed to remove this problem in VLC for me.

---

### Post by persio on 2010-06-11
I'm sorry to revive this old thread, but I'm having exactly the same problem and I can't find any way around it.

> **adde83 said:**
> with some further testing it seems as it was the kwin effects that did  it, I didn't even know I had them enabled.

Some time ago I installed KDE but I didn't like it and uninstalled it. Now (i think that) i'm using gnome+compiz. Kwin does not seem to be installed, but it surely has been some time ago.

> **adde83 said:**
> Hello I had same problem. 
Changing Preferences->Video->output modules   from Default to X11 video output seemed to remove this problem in VLC for me.
I can't find those prefs., are they just for kubuntu?

These are my actual specs:

> **SYSTEM INFORMATION**
    Running Ubuntu Linux, the Ubuntu 10.04 (lucid) release.
    GNOME: 2.30.0 (Ubuntu 2010-03-31)
    Kernel version: 2.6.32-22-generic (#36-Ubuntu SMP Thu Jun 3 22:02:19  UTC 2010)
    GCC: 4.4.3 (i486-linux-gnu)
    Xorg: unknown (23 April 2010  05:11:50PM) (23 April 2010   05:11:50PM)
[B]
GRAPHIC CARD[/B]
    VGA controller
        nVidia Corporation G94 [GeForce 9800M GTS] (rev a1)
        Subsystem: Gateway 2000 Device 0696

**NVIDIA GRAPHIC CARD INFORMATION**
    Model name: GeForce 9800M GTS
    Card Type: PCI-E 16x
    Video RAM: 1024 MB
    GPU Frequency: 169 MHz
    Driver version: NVIDIA UNIX x86 Kernel Module  195.36.15  Thu Mar 11  21:41:46 PST 2010

---

### Post by no2498 on 2010-06-13
the x11 is in gstreamer-properties it is the plugin you use how to change it

open a terminal type, gstreamer-properties click enter
click video click plugins

set it as you like

hope this helps

---

### Post by persio on 2010-06-14
> **no2498 said:**
> the x11 is in gstreamer-properties it is the plugin you use how to change it

open a terminal type, gstreamer-properties click enter
click video click plugins

set it as you like

hope this helps
It seems to have done the job, thank you very much :)

---

### Post by persio on 2010-06-14
Umh, I'm sorry, but the glitch is still there... any other ideas?

---

### Post by vinan on 2010-12-25
> **no2498 said:**
> the x11 is in gstreamer-properties it is the plugin you use how to change it

open a terminal type, gstreamer-properties click enter
click video click plugins

set it as you like

hope this helps



Thanks m8

worked like a charm    :popcorn:

---

### Post by no2498 on 2010-12-27
vinan
thank you for saying thanks
you can also do it this way

click system, preferences
go down the list to multimedia systems selector, start it click video

---

