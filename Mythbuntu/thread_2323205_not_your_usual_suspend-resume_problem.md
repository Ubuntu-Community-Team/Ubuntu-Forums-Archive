---
title: "not your usual suspend-resume problem"
date: 2016-05-03
forum: Mythbuntu
---

### Post by marcw on 2016-05-03
Starting from scratch on a Zotac EN970 with a Nvidia GTX 960 graphics chip, I installed a Myth .28 FE on the latest Ubuntu 16.04 and Myth PPA.  I'm using this as a component in my home theater and the install and almost all functionality works well (except for some vdpau issues but that's another thread).  I'm controlling all Myth functions including both suspend and resume from a Harmony hub and a Flirc virtual keyboard.  The one remaining issue I'm having is with resume from suspend.  But even that's a little misleading as both suspend AND resume do work, just not correctly.  Resume always asks for a password and I don't want it to.

Now that 16.04 seems to have gone almost whole hog into systemd for service management I had some catching up to do so that I could script and configure Ubuntu to get Myth to work the way I want.  That's not too difficult, just some tweaks and syntax changes from my previous myth installations.  But this password on resume has got me stumped.  Steps I've already taken include:
- made sure the User Mgr doesn't require a password
- made 3-4 changes in dconf-editor related to inhibiting password prompting
- created a "allow_suspend.pkla" file in /etc/polkit-1/localauthority/50-local.d which contains the following
```
[Allow all users to suspend]
Identity=unix-user:*
Action=org.freedesktop.login1.suspend-multiple-sessions
ResultActive=yes

[Allow all users to suspend]
Identity=unix-user:*
Action=org.freedesktop.login1.suspend
ResultActive=yes

[Allow all users to ignore inhibit of suspend]
Identity=unix-user:*
Action=org.freedesktop.login1.suspend-ignore-inhibit
ResultActive=yes
```
- changed to a gnome desktop to eliminate composting
- added "username ALL=(ALL) NOPASSWD: ALL" to sudoers (since removed as it didn't help)

My suspend script works terrific with no prompting if run from a command prompt on my myth FE.  It's only when run from a button press on my Harmony remote that I get a password prompt when resuming.  Here's my suspend script:
```
#!/bin/bash

export DISPLAY=:0.0
MYTHRUNNING=`ps -ef |grep mythfrontend.real |grep -v grep`
xdotool key Escape Escape Escape Escape Escape

# see if mythfrontend is running
if [ -n "$MYTHRUNNING" ] ;then
    `pkill mythfrontend`
fi

sleep 5

dbus-send --system --print-reply --dest=org.freedesktop.login1 /org/freedesktop/login1 "org.freedesktop.login1.Manager.Suspend" boolean:true

export DISPLAY=:0.0
/usr/bin/mythfrontend --service

exit
```

I've researched a ton on Google and found that most Myth tips are pre-systemd and so not very helpful.  I'm about at my wits end trying to figure out how to get this resume working without a password prompt.  Looking for suggestions.  I'll try anything.

---

