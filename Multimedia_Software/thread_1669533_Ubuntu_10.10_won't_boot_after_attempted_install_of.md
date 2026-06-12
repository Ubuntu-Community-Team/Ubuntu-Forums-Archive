---
title: "Ubuntu 10.10 won't boot after attempted install of ATI FGLRX driver"
date: 2011-01-17
forum: Multimedia Software
---

### Post by sirtiksalot on 2011-01-17
I'm running 10.10 from an 8GB USB flash drive with persistence to see if I can get it working the way I need it before I can completely transition from Windows.  I have an onboard ATI Radeon HD3300 running dual monitors which is on the list of supported devices for the FGLRX driver package, but I've encountered multiple issues.

First, when I chose to activate it from the Add'l Drivers dialog, it gave an error: "SystemError: installArchives() failed".  I found a forum where someone had suggested opening the Terminal and giving the following commands:
[INDENT]sudo aticonfig --initial[/INDENT]
followed by
[INDENT]sudo reboot[/INDENT]

When my system rebooted, the Ubuntu screen showed "Ubuntu 10.10" in a plain font instead of the Ubuntu graphical logo, and then it quickly displays an error in a dark-colored font and then the screen flickers several times before stopping at a full-screen terminal.  I have never used Linux before, so I don't know any commands at all or even what to do from here.  I just want the dual screens to work and have the correct resolution.

Am I going to have to format and reload my flash drive again???
I really want to abandon Microsoft, but it's a little frustrating at the moment.

---

### Post by soekarmana on 2011-01-17
[http://ubuntuforums.org/showthread.php?t=1425993](http://ubuntuforums.org/showthread.php?t=1425993), this post may help you solve your problem

try fresh install and don't install anything then go to system -> administrator -> additional drivers, activate your ATI driver, reboot.

---

