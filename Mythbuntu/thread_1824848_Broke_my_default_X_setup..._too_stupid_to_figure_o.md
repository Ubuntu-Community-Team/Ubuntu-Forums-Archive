---
title: "Broke my default X setup... too stupid to figure out how to revert back"
date: 2011-08-14
forum: Mythbuntu
---

### Post by sirnickum on 2011-08-14
Hi everyone,

I made a ridiculous rookie mistake, long story short I ran sudo startx from the console and messed up the default mythbuntu xorg setup. I don't know how to fix what I did though.

default was to auto logon a particular user, now I get a login screen...

I would try logging in as my default user and use the mythbuntu control panel to try and see if autologon can be re-enabled but I don't have mouse and keyboard input working for some reason. The reason I was at the console in the first place was because my usb system stopped working so I restarted dbus (on recommendation of another forum)... which killed X, so I figured I'd bring it back up with a startx... bad idea apparently.

So instead of potentially mucking things up even worse I submit myself to the mercy of the forum.

What changed when I ran sudo startx and how can I reverse the damage?

Any thoughts on why my usb keyboard and mouse stopped working randomly?
I have no /proc/bus/usb directory at all, lspci says I have AMD 8111 OHCI usb controller, before I messed up X xinput list gave me only Virtual core XTEST pointer and Virtual core XTEST keyboard

I used to be able to control my system through VNC... until I messed up the autologin, now I can only control the system through ssh

---

### Post by nickrout on 2011-08-14
Try renaming /etc/X11.xorg.conf and restart the computer.

The correct way to restart X is ```
sudo restart gdm
```

---

### Post by sirnickum on 2011-08-16
Thanks for the idea!

I renamed /etc/X11/xorg.conf but it had no effect, got the same gdm login screen on a reboot.

I read on another forum about /usr/share/mythbuntu/session.sh
so I stopped gdm and the ran sudo /usr/share/mythbuntu/session.sh (because it wouldn't let me start x any other way.

that gave me the default mythbuntu I've been trying to get back on boot. but on a reboot I was back at the gdm login screen.

when I was at the default mythbuntu desktop (as root) I tried to modify the autologin settings via mythbuntu-control-centre but all the options were greyed out and the unlock button on the menu did nothing, I thought that was odd since I was root... but maybe it was because they don't want you auto-logging in root, understandable.

So how can I get /usr/share/mythbuntu/session.sh to run on boot and not as root?

I modified /etc/X11/xinit/xinitrc and changed the X session script from /etc/X11/Xsession to /usr/share/mythbuntu/session.sh but it had no effect either. on a reboot I still get the gdm login screen.

I feel like I'm close, but oh so far away.

---

