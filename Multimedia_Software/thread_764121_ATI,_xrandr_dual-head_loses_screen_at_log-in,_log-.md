---
title: "ATI, xrandr dual-head loses screen at log-in, log-out"
date: 2008-04-23
forum: Multimedia Software
---

### Post by robbobrob on 2008-04-23
I am having a problem with a dual-head setup using ATI hardware and xrandr.  When I log-in, I sometimes get one screen, sometimes two.  I can always issue an xrandr command at the console to get two screens working as one big desktop.  Frequently when I log out, I lose the "primary" screen.  Anybody have any suggestions on how to fix or diagnose this?

Here are some specifics:

Kubuntu 7.10, up-to-date, but fairly stock otherwise

lspci:  01:00.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200 PRO] 

driver:  xserver-xorg-video-ati version 1:6.7.195-1ubuntu2

After initial boot:  Two screens active as desired, so xorg.conf is somewhat correct.

Test User:  Always get two screens after login, sometimes lose a screen after log-off, and its the one I need to log back in ("primary").

Main User:  Always lose the "secondary screen" after login and before the KDE splash screen and the whole KDE initialization sequence.  xrandr command at the console always gets me back to two functioning screens.  When I log-out, I typically (but not always) lose the primary screen.  I can't log in since I can't see kdm so need to reboot.

May be related - Ctrl-Alt-F1 usually won't bring up a virtual terminal where I can log-in and try to restart X, etc.

---

