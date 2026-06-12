---
title: "Many problems with MythTV"
date: 2009-01-28
forum: Multimedia Software
---

### Post by AKADAP on 2009-01-28
I have attempted to set up myth TV on my computer, but have run into many problems.

If I haven't run "MythTV Backend Setup" since I booted the computer, attempting to "watch live TV" in the mythTV front end flashes the screen and dumps me back in the main menu.

When I exit from "MythTV Backend Setup", it hangs showing MythTV Setup Terminal with the following:
```
2009-01-28 16:04:54.546 Using runtime prefix = /usr
2009-01-28 16:04:54.552 XScreenSaver support enabled
2009-01-28 16:04:54.553 DPMS is active.
2009-01-28 16:04:54.553 Empty LocalHostName.
2009-01-28 16:04:54.553 Using localhost value of Compromise
QSettings: failed to open file '/etc/qt3/qt_plugins_3.3rc'
QSettings::sync: filename is null/empty
2009-01-28 16:04:54.558 New DB connection, total: 1
2009-01-28 16:04:54.561 Connected to database 'mythconverg' at host: localhost
2009-01-28 16:04:54.561 Closing DB connection named 'DBManager0'
2009-01-28 16:04:54.562 Primary screen 0.
2009-01-28 16:04:54.563 Connected to database 'mythconverg' at host: localhost
2009-01-28 16:04:54.563 Using screen 0, 2560x1600 at 0,0
QSettings: failed to open file '/etc/qt3/qt_plugins_3.3rc'
QSettings::sync: filename is null/empty
2009-01-28 16:04:54.569 New DB connection, total: 2
2009-01-28 16:04:54.569 Connected to database 'mythconverg' at host: localhost
2009-01-28 16:04:54.570 Current Schema Version: 1214
2009-01-28 16:04:54.583 Primary screen 0.
2009-01-28 16:04:54.583 Using screen 0, 2560x1600 at 0,0
2009-01-28 16:04:54.584 No theme dir: /home/username/.mythtv/themes/G.A.N.T
2009-01-28 16:04:54.584 Switching to square mode (G.A.N.T)
2009-01-28 16:04:54.686 Using the Qt painter
mythtv: could not connect to socket
mythtv: No such file or directory
2009-01-28 16:04:54.686 lirc_init failed for mythtv, see preceding messages
2009-01-28 16:04:54.686 JoystickMenuClient Error: Joystick disabled - Failed to
read /home/username/.mythtv/joystickmenurc
QSettings: failed to open file '/etc/qt3/qt_plugins_3.3rc'
QSettings::sync: filename is null/empty
QSettings: failed to open file '/etc/qt3/qt_plugins_3.3rc'
QSettings::sync: filename is null/empty
QSettings: failed to open file '/etc/qt3/qt_plugins_3.3rc'
QSettings::sync: filename is null/empty
2009-01-28 16:04:55.725 Loading from: /usr/share/mythtv/themes/G.A.N.T/base.xml
2009-01-28 16:04:55.858 Loading from: /usr/share/mythtv/themes/default/base.xml
2009-01-28 16:04:55.872 No theme dir: /home/username/.mythtv/themes/G.A.N.T

```

Once I have manually closed MythTV Setup Terminal, I can show live TV.
Quite often however, changing channels crashes the computer, sometimes rebooting, sometimes locking up with a blank screen.
When the channel does change, if the resolution is different, I get garbage, I have to hit escape twice to get back to the main menu, then restart the "watch live TV" before video can be viewed.

The system is running Ubuntu 64 with an ATI HD4850 video card, and two HDHomeRun boxes.
I am aware that the video corruption is an ATI driver issue, but I'd like to at least resolve the hang in the backend setup, the fact that I have to run the backend setup every time, and the crashing.

---

### Post by AKADAP on 2009-01-29
I changed attributes of /etc/qt3/qt_plugins_3.3rc from -rw-r----- to -rw-r--r--. This eliminated the "unable to open file" error messages. Now I get:
```
2009-01-29 14:28:05.640 Using runtime prefix = /usr
2009-01-29 14:28:05.647 XScreenSaver support enabled
2009-01-29 14:28:05.647 DPMS is active.
2009-01-29 14:28:05.647 Empty LocalHostName.
2009-01-29 14:28:05.648 Using localhost value of Compromise
QSettings::sync: filename is null/empty
2009-01-29 14:28:05.651 New DB connection, total: 1
2009-01-29 14:28:05.653 Connected to database 'mythconverg' at host: localhost
2009-01-29 14:28:05.653 Closing DB connection named 'DBManager0'
2009-01-29 14:28:05.653 Primary screen 0.
2009-01-29 14:28:05.654 Connected to database 'mythconverg' at host: localhost
2009-01-29 14:28:05.654 Using screen 0, 2560x1600 at 0,0
QSettings::sync: filename is null/empty
2009-01-29 14:28:05.657 New DB connection, total: 2
2009-01-29 14:28:05.658 Connected to database 'mythconverg' at host: localhost
2009-01-29 14:28:05.658 Current Schema Version: 1214
2009-01-29 14:28:05.673 Primary screen 0.
2009-01-29 14:28:05.673 Using screen 0, 2560x1600 at 0,0
2009-01-29 14:28:05.673 No theme dir: /home/username/.mythtv/themes/G.A.N.T
2009-01-29 14:28:05.674 Switching to square mode (G.A.N.T)
2009-01-29 14:28:05.764 Using the Qt painter
mythtv: could not connect to socket
mythtv: No such file or directory
2009-01-29 14:28:05.765 lirc_init failed for mythtv, see preceding messages
2009-01-29 14:28:05.765 JoystickMenuClient Error: Joystick disabled - Failed to 
read /home/username/.mythtv/joystickmenurc
QSettings::sync: filename is null/empty
2009-01-29 14:28:06.589 Loading from: /usr/share/mythtv/themes/G.A.N.T/base.xml
2009-01-29 14:28:06.689 Loading from: /usr/share/mythtv/themes/default/base.xml
2009-01-29 14:28:06.704 No theme dir: /home/username/.mythtv/themes/G.A.N.T

```
But it still hangs on exit.

---

### Post by chronographer on 2009-01-29
Myth tv can be a bitch to set up... I can't help you with any specific problem but... you could try (if you don't mind a new install) installing mythbuntu. It comes as a live Cd and installs with good settings and a different GUI for setting things up.

I thought is was pretty easy to use, but still had to hack at a few things!

If you think it is a video card issue try the open source ATI drivers rather than the ATI official ones (or vice versa)/

---

### Post by AKADAP on 2009-01-30
> **chronographer said:**
> Myth tv can be a bitch to set up... I can't help you with any specific problem but... you could try (if you don't mind a new install) installing mythbuntu. It comes as a live Cd and installs with good settings and a different GUI for setting things up.

I thought is was pretty easy to use, but still had to hack at a few things!

If you think it is a video card issue try the open source ATI drivers rather than the ATI official ones (or vice versa)/

I am not willing to re-install as I am using this computer as my main system. I hope eventually to be able to use it as a front end, and have a much lower powered system be the back end (I only intend to record digital, so there is no need for much CPU on the back end).

Unless there has been a new release of the open source driver in the last few months, this is a no go. I was unable to install with the open source driver, I had to install in safe mode, then install the ATI driver. Otherwise I was left with a sleeping monitor and no way to wake it up. I am not aware of an easy way to recover from a screwed up display driver other than re-installing Ubuntu, and as I have stated, I don't want to do that.

on the machine I intended to run the back end on, a Via Epia-M 6000 motherboard, I have not been able to successfully install any version of Linux on. I believe that linux is misidentifying the processor and attempting to run code that uses instructions (cmov) the processor does not have. I know the hardware works as I was able to install the beta of Windows 7 on that computer.

---

### Post by AKADAP on 2009-02-03
> **AKADAP said:**
> I changed attributes of /etc/qt3/qt_plugins_3.3rc from -rw-r----- to -rw-r--r--. This eliminated the "unable to open file" error messages.(stuff deleted)
But it still hangs on exit.
I found I had to change it to -rw-rw-rw- to completely eliminate the errors. Still hangs.
Had another problem. both front end and back end suddenly were unable to access the server. It turns out my computers IP address changed. I fixed that in the backend setup, so now I am back where I was.

---

### Post by AKADAP on 2009-02-03
Even that wasn't quite enough. Myth was attempting to open a temp file in the /etc/qt3/ directory, so I had to change that directories permissions as well.

---

### Post by AKADAP on 2009-02-08
I found that there was a mythbuntu metapackage (I had originally installed mythTV by typing "mythTV" into the search field of "Add/Remove...")
Unfortunately, aside from changing my login screen, this did not change anything useful, all of the above bugs remain.

---

### Post by buntunub on 2009-02-08
Go to Add/Remove and install the Mythbuntu Control Center. From there you should be quite easily able to do everything you want to do with Mythtv.

---

### Post by AKADAP on 2009-02-08
> **buntunub said:**
> Go to Add/Remove and install the Mythbuntu Control Center. From there you should be quite easily able to do everything you want to do with Mythtv.

The mythbuntu control center got installed when I installed the mythbuntu metapackage. I didn't see anything there that would fix any of the problems I'm having with MythTV.

---

### Post by buntunub on 2009-02-11
Switch to OpenGL and see if that helps. I had some issues like then when using QT themes as well and I recall that there is some known bug about it. Switching fixed all issues.

---

### Post by AKADAP on 2009-02-12
I have discovered (after I created this thread) that there is a whole subforum on this site for Mythbuntu. I have moved my questions there.

I have solved the issue of having to run backend setup before I could watch live TV. It turns out that the backend was starting before the network was up, so it could not find the HDHomeRun boxes.

Other issues are still in play though.

Switch what to OpenGL? and what issues did that fix?

---

