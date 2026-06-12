---
title: "Remote switching focus between X screens / Multi-monitor"
date: 2011-10-12
forum: Multimedia Software
---

### Post by professorYaffle on 2011-10-12
I have a machine (running natty (a basic ubuntu install with kubuntu added later) fully up to date) with three monitors on two nvidia graphics cards, using the nvidia drivers. Two monitors are rotated and merged using twinview to give a single X screen :0.0. I've recently added the thrid monitor. It forms a second X screen (:0.1) on the left of the first. I'm using fluxbox as the window manager etc..

This all works quite nicely at the desk, but I now have problems when I try to get to it remotely. I use x11vnc to share the existing desktop. I was expecting to be limited to remotely controlling only one of the X screens at a time, and I can successfully select which of :0.0 and :0.1 that x11vnc shares. The problem is that whilst I can see the correct screen, all the events (well, keypresses certainly, probably mouse movement and clicks as well) go to the X screen that last had focus.

I'm looking for a way that I can remotely switch the focus / move the mouse pointer between the two X screens. I've even gone as far as trying to implement a little commandline interface program to the XTestFakeMotionEvent() call. It moves the pointer okay, but seems to ignore the screen argument. So far, the only way I know of that works is to physically move the mouse on the mouse mat (and that's not something I can do remotely.) So I have to remember to leave the mouse on the correct screen before I leave the building.

There has to be something obvious that I've missed!!??

---

### Post by krunge on 2011-11-19
I think I have finally diagosed what is causing this and then I found your post. At some point (2009?) the Xorg implementation broke XTestFakeMotionEvent() just as you described: it ignores the screen argument.

Fortunately there is workaround for x11vnc that makes is use XWarpPointer() instead of XTestFakeMotionEvent().  Add this cmdline option:
```

x11vnc -xwarppointer ...

```
where ... means your other x11vnc cmdline options.

Please let me know if it works around the Xorg bug for you.

Here are some references:

[INDENT][https://bugzilla.redhat.com/show_bug.cgi?id=518803](https://bugzilla.redhat.com/show_bug.cgi?id=518803)[/INDENT]

[INDENT][https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/339783](https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/339783)[/INDENT]

---

### Post by professorYaffle on 2011-11-21
Thank you so much Krunge, that's solved it for me.

So it seems that the only real bug here is that the documentation (man page) for XTestFakeMotionEvent is out of date. Still claiming to support the screen number argument.

Thanks again.

---

### Post by krunge on 2011-11-26
Glad it is working for you. I modified x11vnc 0.9.14 so that the -xwarppointer workaround is applied automatically.
> So it seems that the only real bug here is that the documentation (man page) for XTestFakeMotionEvent is out of date. Still claiming to support the screen number argument.
I have filed a bug at Xorg:

[INDENT][https://bugs.freedesktop.org/show_bug.cgi?id=43101](https://bugs.freedesktop.org/show_bug.cgi?id=43101)[/INDENT]

---

