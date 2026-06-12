---
title: "Screen stays blank when monitor turned back on"
date: 2011-09-20
forum: Multimedia Software
---

### Post by jimmux on 2011-09-20
I can't find evidence of anyone else having this problem, but hopefully someone can suggest at least a workaround.

This is happening on a fresh install. At first I was getting it with Ubuntu using either Unity of classic desktop, but I am now using xubuntu and still getting the problem. The machine is an old desktop unit that I am attempting to use like a media centre, with the only display being a TV connected using a DVI to HDMI cable.

The problem goes like this:
[LIST]
[*]Everything is fine, until the screen is turned off, unplugged or input source changed.
[*]When switching back, I get one of 4 possibilities:
[/LIST]
[LIST=1]
[*]Everything is fine.
[*]The screen is black. The correct resolution and such is detected, but I can see only black. Switching to alt-ctrl-f6, etc. has no effect.
[*]As above, but purple instead of black.
[*]The machine locks up completely, stops responding to ping, etc.
[/LIST]
[LIST]
[*]After a reboot everything is fine again.
[/LIST]

I thought disabling compiz fixed it, but it came back again.

Any thought?

---

### Post by jimmux on 2011-09-22
Some more developments.

I've tried various options without much difference, but now when I turn the screen back on I can see output from startup. There is even a visible and moveable cursor. I suspect this is because I disabled quiet and splash in my grub configuration.

I also installed x11vnc and configured it to start on boot in .xsessionrc, so when the screen doesn't come back I can vnc in. The weird thing is that this actually works. VNC shows what I should be seeing on display :0 even though the attached screen is wrong. This lets me start xbmc remotely, which brings things back to normal.

At least I know the screen detection and xorg config is correct, because it always shows things as configured.

This is a usable workaround for now, but the question now is: why is my desktop not displaying?

---

