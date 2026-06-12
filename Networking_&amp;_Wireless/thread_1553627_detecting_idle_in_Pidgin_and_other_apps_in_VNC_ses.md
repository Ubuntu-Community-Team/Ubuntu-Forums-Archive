---
title: "detecting idle in Pidgin and other apps in VNC sessions?"
date: 2010-08-15
forum: Networking &amp; Wireless
---

### Post by robertbub on 2010-08-15
I run **pidgin** instant messenger via **fbpanel** taskbar via **fluxbox** window manager via **xvnc** vnc server via **xrdp** remote desktop terminal via **sesman** session manager.

One problem I've found is that Pidgin does not detect when I stop mousing or typing.  I also run gnotime time tracker and it too is not able to detect when I don't type on the keyboard or move the mouse in my X-Windows.

Some questions:[LIST=1]
[*]Is there a common problem?
[*]Is there a workaround?
[*]Is there a way to diagnose the problem?
[LIST]
[*]perhaps a program which says which window got the input which resets the idle timeout
[/LIST]
[*]Is there a way to examine or record the idle periods?
[/LIST]Thanks.

---

### Post by robertbub on 2010-09-25
I'm pretty sure this is due to limitations in the X windows server I'm running.

In particular, I'm running Xvnc (Xtightvnc) and Gnotime and xautolock also do not detect mouse and keyboard idleness.

I'm gunna report a bug at launchpad.net .

---

